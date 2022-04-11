## Elasticache

A service that makes it easy to deploy, operate, and scale an in-memory cache. Can be a good way to store compute intensive calculations.

Supports two open source engines:

- Memcached
- Redis

A maintenance window will be assigned by default, you can change this.

You are charged per node type, per hour. Partial node hours are billed as full hours. Billing is any time the node is available.

### Memcached

Widely adopted, multi-threaded, memory object caching system. Elasticache is protocol compliant with Memcached, this enables existing tools to be able to work with Elasticache.

Is a pure caching solution with no persistence. It is managed as a pool that can grow and shrink. Individual nodes are seen as expendable.

### Redis

Popular open-source, in-memory key-value store that supports data structures such as sorted sets and lists. Supports master-slave replication and multi availability zone to achieve cross availability zone redundancy.

Is for more advanced data types (lists, hashes, sets). Includes persistence and sorting/ranking datasets.

A node is the smallest building block, a fixed-size chunk of secure, network attached RAM. It has its own DNS name and port. Nodes range from 555MB to 635GB.

A Redis shard is a subset of the clusters namespace that can include a primary node and zero or more (up to five) read replicas. If there are multiple read replicas, the read replica with the smallest async replication lag to the primary will be promoted. You can trigger a failover event.

If you need something for leader boards, the answer is Redis.

### Reserved Nodes

Reserved nodes or reserved instances offers significant discount when doing one or three year terms. You can make an upfront payment.

If you reserve the same type you are using, it will transfer.

Types are (the only difference is billing):

- All upfront
- No upfront
- Partial upfront

Can purchase up to 20 reserved nodes, for more, contact Amazon.

### Security

Can be controlled with security groups or inside a VPC, subnet groups are collections of subnets, use DNS over IPs where possible.

### Parameter Groups

A parameter group acts as 'container' for engine configuration values that can be applied to one or more clusters. If not provided, a default group is used. By default, the optimal config is used to suite the node/config.

### Engine Version Management

You control when to upgrade the engine version but Amazon handle the upgrade. Some security vulnerabilities may be done automatically. You can specify any major/minor version. To test you can create a new cluster in stage before upgrading.

### Caching Strategies

#### Lazy loading

Loads into the cache when necessary, the cache hits result in a quick response. If a cache miss happens, the data is fetched and then is written to the cache for the next time. This means the first request will probably be slower than without a cache.

Data can become stale, this can be reduced by adding a TTL.

#### Write Through

Adds/updates data whenever data is written to the database, means there is no stale data and generally slightly slower updates/saves are tolerated. This does add a write penalty as everything has to be written twice.

A node failure means that the node needs rebuilding with all the data to catch back up. It can result in wasted resources if the data is not read.

#### Restore and Backup

Allows snapshot creation which is a copy of your entire Redis cluster, taking snapshots from a read replica is the most effective. They are stored in S3. Snapshots allow for a warm start up.
