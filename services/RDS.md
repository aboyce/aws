## Relational Database Service (RDS)

Supported instances:

- MS SQL Server
- Oracle
- MySQL
- PostgreSQL
- AWS Aurora (MySQL and/or PostgreSQL compatible)
- Maria DB

### Automated Backups

There are two different types:

#### Automated backups

Allow you to recover to any point within a retention period (between 1-35 days). Take a full daily snapshot and store transaction logs. They are enabled by default and the data is stored in S3 (free storage that equals the DB size). During the backup you may see latency.

#### Snapshots

Done manually and stored after you delete the RDS instance (unlike automated backups).

### Restoring Backups

When you restore either, you get a new instance with a new DNS endpoint.

### Encryption

Encryption at rest is supported on all DBS and done via KMS. If encrypted, your backups are also encrypted. To encrypt a non-encrypted DB, restore a snapshot and then enable it.

### Multi-AZ

Allows an exact copy of your database in another availability zone. AWS handles the replication and failover for you, this is for disaster recovery though, not performance.

### Read Replica

You can have up to 5 per database. If you are read heavy, these help take the load from the primary DB. Can have read replicas of read replicas but there will be a latency of the data. Each replica has its own DNS endpoint. You can promote a read replica to be a full instance but it will break the replication. They can exist in another region.
