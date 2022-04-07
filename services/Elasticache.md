## Elasticache

A service that makes it easy to deploy, operate, and scale an in-memory cache. Can be a good way to store compute intensive calculations.

Supports two open source engines:

- Memcached
- Redis

### Memcached

Widely adopted, multi-threaded, memory object caching system. Elasticache is protocol compliant with Memcached, this enables existing tools to be able to work with Elasticache.

Is a pure caching solution with no persistence. It is managed as a pool that can grow and shrink. Individual nodes are seen as expendable.

### Redis

Popular open-source, in-memory key-value store that supports data structures such as sorted sets and lists. Supports master-slave replication and multi availability zone to achieve cross availability zone redundancy.

Is for more advanced data types (lists, hashes, sets). Includes persistence and sorting/ranking datasets.

If you need something for leader boards, the answer is Redis.

### Caching Strategies

#### Lazy loading

Loads into the cache when necessary, the cache hits result in a quick response. If a cache miss happens, the data is fetched and then is written to the cache for the next time. This means the first request will probably be slower than without a cache.

Data can become stale, this can be reduced by adding a TTL.

#### Write Through

Adds/updates data whenever data is written to the database, means there is no stale data and generally slightly slower updates/saves are tolerated. This does add a write penalty as everything has to be written twice.

A node failure means that the node needs rebuilding with all the data to catch back up. It can result in wasted resources if the data is not read.
