## Kinesis

AWS Kinesis makes it easy to collect, process, and analyse real-time, streaming data. Can ingest real-time data such as video, audio, application logs, website clickstreams, and IoT telemetry data. Allows you to process and analyse data as it arrives instantly rather than having to wait till all of the data is collected. Synchronously replicates data across three availability zones.

### Streams

Data is sent to steams and stored in shards. Default storage is 24 hours but can be up to 7 days. You can then pass this data onto consumers. Can attach up to 20 consumers per stream, each with its own dedicated read throughput.

You can choose between on-demand and provisioned capacity.

Shards handle 5 transactions per second for reads, maximum of 2MB per second. 1000 records per second for writes, maximum of 1MB per second.

### Shards

Base throughput of a data stream. Provides 1MB/sec data input, 2MB/sec data output. You can combine them for more throughput.

### Record

A unit of data stored in a data stream, composed of a sequence number, partition key, and data blob.

#### Partition Key

Used to segregate and route records to different shards of a data stream specified by you data producer.

### Firehose

An extract, transform, and load (ETL) service that reliably captures, transforms, and delivers streaming data to data lakes, data stores, and analytic services.

Can load data into:

- S3
- Redshift
- OpenSearch Service
- HTTP endpoints
- Datadog
- New Relic
- MongoDB
- Splunk

### ReSharding

Shard split is a single shard divided into two for increased throughput. Shard merging combines two into one, decreasing throughput.

### Analytics

Easiest way to transform and analyse streaming data in real time using Apache Flink.

Can run SQL queries on the data within Firehose or Streams. Can store the results in S3, Redshift, ElasticSearch cluster.
