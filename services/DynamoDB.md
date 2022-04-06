## DynamoDB

A fully managed, NoSQL database service that provides fast and predictable performance with seamless scalability. Runs exclusively on SSDs.

The service stores three geographically replicas of each table to ensure high availability and durability.

When reading the data, the user can decide if they want the read to be;

- **Eventually consistent** (default), usually consistent within a second, repeating a read should update
- **Strongly consistent**, returns a result that reflects all successful prior writes

### Structure

Supports both document and key-value data models.

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

You can reduce the page size for fewer reads and more but smaller requests can help to reduce throttling.

Avoid scans if you can, think about the table design.

Can use parallel scans if the database is not under much load.

### Provisioned Throughput

Provisioned throughput is measured in capacity units.

When you create a table (and not using auto-scaling) you specify your requirements in terms of:

- Read capacity units
- Write capacity units

The math (Strongly Consistent Write = SCW, Eventually Consistent Write = ECR):

- `1 x WCU = 1 x 1KB Write per Second`
- `1 x RCU = (1 x SCR of 4KB per Second) OR (2 x ECR of 4KB per Second (default))`

If your application reads/writes larger items it will consume more capacity units and will cost more.

When calculating requirements, ensure you round to the nearest whole capacity unit when working it out.

### On Demand Capacity

Charges apply for reading, writing, and storing data. You do not have to specify the requirements, it scales up and down automatically. This is good for unpredictable work loads and you only pay for what you use (per request).

### DynamoDB Accelerator (DAX)

DAX is a fully managed, clustered in-memory cache for DynamoDB. Delivers up to a 10x read improvement and microsecond performance for millions of requests per second. It is a write-through caching system, this means that data is written to the cache as well as the backend store. If the item (read) is not available (a cache miss) then DAX performs an eventually consistent `GET` item operation against DynamoDB.

Ideal for ready heavy or burst workloads. Reduces the load for reads on tables and may allow for a reduced read capacity.

Allows you to point your DynamoDB API calls to the DAX cluster itself.

It is not suitable for:

- Anything that requires strongly consistent reads
- Write intensive applications
- Read light workloads
- Apps that do not require microsecond response times
