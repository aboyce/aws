## OpenSearch Service

A managed services that makes it easy to perform log analytics, real-time application monitoring, website search and more. It is the open source version of ElasticSearch.

Amazon OpenSearch Service domains are ElasticSearch or OpenSearch cluster created using the Amazon OpenSearch Service console, CLI, or API. Each domain is an OpenSearch or ElasticSearch cluster in the cloud with the compute and storage resources that you specify.

You can deploy the instances across one, two or three AZs. It supports VPC. You can choose between local on-instance storage or EBS volumes. If you use EBS storage, you can increase and decrease the size of the storage volume as necessary. The maximum storage per node is 15TB. The default maximum of 40 data nodes are allowed per OpenSearch Service domain. You can allocate about 600TB of storage to a single domain. This can be increased and you could get to 3PB of storage.

For production, you should have a minimum of three dedicated master nodes. If one of more instances in an AZ are unreachable or not functional, new instances in the same AZ are brought up to replace the affected instances.

To migrate an existing cluster into AWS, you should create a snapshot of it, put that into S3, then create the new cluster from that snapshot.

Hourly snapshots of the domain are automatically taken and retained for 14 days, they are stored in S3 and there is no charge for these. You can also create manual snapshots and store them in S3 but you are charged as you would be to store anything in S3.

Slow logs help track the performance of various stages in an operation. There are two types:

- Index Slow Logs: Provide insight into the indexing process and can be used to fine-tune the index setup.
- Search Slow Logs: Provide insight into how fast or slow queries and fetches are performing. From these you can fine tune the performance of search operations.

Enabling slow logs does not cost anything, but as they will end up in CloudWatch, standard CloudWatch charges will apply. As it is not free, ideally you would only turn it on to debug any problems in performance. It requires deploying a new cluster to change the slow logging, AWS will handle all of this for you but it is not instant.

### Security

You can lock down Kibana dashboards with Cognito (so via Active Directory etc.).

It supports encryption at rest via KMS, node-to-node encryption over TLS, and the ability to require clients to communicate via HTTPS. Encryption at rest encrypts shards, log files, swap files and automated S3 snapshots.

### Pricing

You can reserve instances for one or three years to reduce the cost compared to On-Demand instances.

### SLA

The SLA guarantees a Monthly Uptime Percentage of at least 99.9%.

### UltraWarm

UltraWarm is a fully-managed, low-cost, warm storage tier. It allows you to cost effectively expand the data you want to analyse, gaining valuable insights on data that previously may have been deleted or archived.

There are two integrated storage tiers, hot and UltraWarm. The hot tier is powered by data nodes which are used for indexing, updating and providing the fastest access to data. UltraWarm nodes complement hot tier by providing low cost, read-only tier for older and less frequently accessed data.

It uses S3 under the hood, so has all the reliability benefits of that, whist preventing the need for an ElasticSearch replica adding to the cluster.

It supports up to 3PB of primary data.

For both UltraWarm and Cold Storage, it adds compute nodes on top of the data backed in S3. You can swap this data out to free up compute space and only attach it to the domain when you want to interrogate it.

### Cold Storage

Fully-managed lowest cost storage tier that makes it easy to securely store and analyse historical logs on-demand. Enables you to fully detach storage from compute when they are not actively performing analysis on their data and allows you to keep your data readily available at low cost. It is also backed by S3. It is made available via UltraWarm.

You can store any amount of data in cold storage.
