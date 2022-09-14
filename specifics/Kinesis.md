# Kinesis

AWS Kinesis makes it easy to collect, process, and analyse real-time, streaming data. Can ingest real-time data such as video, audio, application logs, website clickstreams, and IoT telemetry data. Allows you to process and analyse data as it arrives instantly rather than having to wait till all of the data is collected. Synchronously replicates data across three availability zones.

## Data Streams

You can build custom applications that process or analyse streaming data for specialised needs. You can add various types of data such as clickstreams, application logs, and social media to a Kinesis data stream from hundreds of thousands of sources.

Data is sent to steams and stored in shards. Default storage is 24 hours but can be up to 7 days. You can then pass this data onto consumers. Can attach up to 20 consumers per stream, each with its own dedicated read throughput. It will scale automatically by default.

They synchronously replicates data across three AZs.

You can choose between on-demand and provisioned capacity if you want to manage throughput on your own.

Shards handle 5 transactions per second for reads, maximum of 2MB per second. 1000 records per second for writes, maximum of 1MB per second.

Some example scenarios are:

- Accelerated log and data feed intake
- Real-time metrics and reporting
- Real-time data analytics
- Log and event data collection
- Power event-driven applications

You can also send data from existing resources in AWS services such as:

- DynamoDB
- Aurora
- CloudWatch
- IoT Core

### Shards

A shard has a sequence of data records in a stream. It serves as a base throughput unit of a data steam.

Base throughput of a data stream. Provides 1MB/sec and 1,000 records per second for writes, 2MB/sec data reads. You can combine them for more throughput.

The shard limits ensure predicable performance, making it easy to design and operate. If writes and reads exceed the shard limits, the producer and consumer applications will receive throttles, which can be handled via retries.

### Record

A unit of data stored in a data stream, composed of a sequence number, partition key, and data blob. Data blob is the data of interest your data producer adds to a data stream. Maximum size of a data blob (the data payload before Base64-encoding) is 1MB.

#### Partition Key

Used to segregate and route records to different shards of a data stream specified by you data producer whilst adding data to the data stream. For example, you could have shards 1 and 2, you configure your producer to use two partition keys (A and B) so that all records with key A are added to shard 1 and all records with key B are added to shard 2.

## Firehose

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
