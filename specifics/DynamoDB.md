## DynamoDB

A fully managed, NoSQL database service that provides fast and predictable performance with seamless scalability. Runs exclusively on SSDs.

Autoscaling, partitions/repartitions as your data and table size grows.

The service stores three geographically replicas of each table to ensure high availability and durability. In most cases, DynamoDBs response times are in single digit milliseconds.

When reading the data, the user can decide if they want the read to be;

- **Eventually consistent** (default), usually consistent within a second, repeating a read should update
- **Strongly consistent**, returns a result that reflects all successful prior writes

Can use `PutItem` or `BatchWriteItem` to insert items. `GetItem` or `BatchGetItem` to retrieve, if you have the composite primary keys enabled you can use the query API.

### Structure

Supports both document and key-value data models.

- **Table**
- **Items** think rows in a table
- **Attributes** think columns in a table

Documents can be:

- JSON
- XML
- HTML

### Primary Keys

It stores and retrieves data based on a primary key, there are two types.

#### Partition Key

A unique attribute (e.g. a user Id). This value is an input to a hash function which determines the partition or location it is stored. No two items can have the same partition key.

#### Composite Key

A partition key and a sort key. Partition key is the same as above, the sort key could be a timestamp etc. all items with the same partition key are stored together but then are sorted on sort key value.

### Security

All access management is done via IAM with relevant permissions. You can use an IAM Condition to restrict user access to only their own records. This could be something such as only seeing items where the partition key value matches their user Id.

### Indexes

In an SQL database, in index is a data structure which allows you to perform fast queries on specific columns in a table, this avoids querying the full dataset. In DynamoDB, there are two types of index.

#### Local Secondary Index

Can only be created at table creation, cannot add/remove/modify it later. Has the same partition key as the table but has a different sort key. It gives a different view of your data, organised according to a different sort.

Any queries using this are much faster using the index rather than the main table.

#### Global Secondary Index

Can be create at table create time or any time after. It has a different partition key and sort key. It gives a completely different view of your data.

It speeds up queries relating to a different partition and sort key. An example could be:

- Partition key as an email address
- Sort key as a login date

### Scan and Query

#### Query

A query operation finds items in a table based on the primary key attribute and a distinct value to search for and returns all the attributes for the item. For example, `userId` is `212`.

Can use an optional sort key name and value to refine, this could be a timestamp in the last two days etc.

By default, the query returns all attributes but you can use a Project Expression if you only want to return specific attributes.

Results are always sorted by the sort key. Numeric order, default ascending. You can reverse the order by setting the `ScanIndexForward` to `false`.

By default, queries are eventually consistent. You need to explicitly set it with `ConsistentRead` to be strongly consistent.

### Scan

It examines every item in the table.

By default, the query returns all attributes but you can use a Project Expression if you only want to return specific attributes.

You can apply filters to the query, but these are applied post Scan execution so would be like running a `.filter()` after everything has been returned. As the table grows, scans take longer, a scan on a large table can saturate the throughput.

#### Performance Improvements

You can reduce the page size for fewer reads and more but smaller requests can help to reduce throttling, it uses fewer read operations and adds a pause between requests. Default page size is 1MB.

Avoid scans if you can, think about the table design.

Can use parallel scans if the database is not under much load.

### Provisioned Throughput

Provisioned throughput is measured in capacity units. You are charged for your provisioned read and write throughput by the hour if you use it or not.

If you want to exceed reads or writes of 10,000 capacity units for a table, contact Amazon.

When you create a table (and not using auto-scaling) you specify your requirements in terms of:

- Read capacity units
- Write capacity units

The math (Strongly Consistent Write = SCW, Eventually Consistent Write = ECR):

- `1 x WCU = 1 x 1KB Write per Second`
- `1 x RCU = (1 x SCR of 4KB per Second) OR (2 x ECR of 4KB per Second (default))`

If your application reads/writes larger items it will consume more capacity units and will cost more.

When calculating requirements, ensure you round to the nearest whole capacity unit when working it out. 25 read and 25 write capacity units is the account level free tier.

### On Demand Capacity

Charges apply for reading, writing, and storing data. You do not have to specify the requirements, it scales up and down automatically. This is good for unpredictable work loads and you only pay for what you use (per request).

### DynamoDB Accelerator (DAX)

DAX is a fully managed, clustered in-memory cache for DynamoDB. Delivers up to a 10x read improvement and microsecond performance for millions of requests per second. It is a read-through, write-through caching system, this means that data is written to the cache as well as the backend store for writes, and will keep hold of reads if they have previously been read before. If the item (read) is not available (a cache miss) then DAX performs an eventually consistent `GET` item operation against DynamoDB.

Ideal for ready heavy or burst workloads. Reduces the load for reads on tables and may allow for a reduced read capacity (and in tern potential cost savings).

Allows you to point your DynamoDB API calls to the DAX cluster itself as they both have the same API. So only requires minimal functional changes to swap over to using DAX.

It is not suitable for:

- Anything that requires strongly consistent reads
- Write intensive applications
- Read light workloads
- Apps that do not require microsecond response times

### Transactions

ACID (Atomic, Consistent, Isolated, Durable)

Read or write multiple tables as an all or nothing operation. Allows complex business logic to all take part in one transaction, can help to reduce errors or data from getting into an invalid state.

Provides the ability to check for a pre-requisite condition before writing to a table.

### TTL

Defines an expiry time for your data, expressed as epoch time, expired items are marked for deletion. You define the attribute that is the TTL.

Good solution for removing:

- Session data
- Event logs
- Temp data

Reduces costs by having less data.

### Global Tables

Allows data replication of DynamoDB tables. The changes made to an item in a replica table will be replicated to all other replicas within the same global table. In a global table, a newly written item, is usually propagated to all replica tables within seconds. It does not support partial replication of only some of the items.

### Steams

Time-ordered sequence of item level modifications (insert, update, delete) to DynamoDB tables. Accessed by a dedicated endpoint. By default the primary key is recorded. Events are recorded at near real-time, can trigger a Lambda on event, executes Lambda code based on event. Lambda polls the DynamoDB stream. Before and after images can be captured. Apps can take actions based on the content.

If a new item is added to a table, the streams captures an image of the entire item, including the attributes. If an item is updated, the steam captures old and new images of any attributes modified in the item. If an item is deleted from the table, the steam captures an image of the entire item before it was deleted.

Logs are encrypted at rest and stored for 24 hours.

### Provisioned Throughput Exceeded and Exponential Back-off

Seen if the request rate is too high for the read/write capacity.

SDK automatically retries the request until successful. If you are not using the SDK, you can:

- Reduce the request frequency
- Use exponential back-off (using progressively longer waits)
