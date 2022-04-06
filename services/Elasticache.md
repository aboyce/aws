## Elasticache

A service that makes it easy to deploy, operate, and scale an in-memory cache.

Supports two open source engines:

- Memcached
- Redis

### Memcached

Widely adopted, memory object caching system. Elasticache is protocol compliant with Memcached, this enables existing tools to be able to work with Elasticache.

Is a pure caching solution with no persistence. It is managed as a pool that can grow and shrink. Individual nodes are seen as expendable.

### Redis

Popular open-source, in-memory key-value store that supports data structures such as sorted sets and lists. Supports master-slave replication and multi availability zone to achieve cross availability zone redundancy.

Is for more advanced data types (lists, hashes, sets). Includes persistence and sorting/ranking datasets.

If you need something for leader boards, the answer is Redis.
