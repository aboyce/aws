# Kinesis

AWS Kinesis makes it easy to collect, process, and analyse real-time, streaming data. Can ingest real-time data such as video, audio, application logs, website clickstreams, and IoT telemetry data. Allows you to process and analyse data as it arrives instantly rather than having to wait till all of the data is collected. Synchronously replicates data across three availability zones.

## Data Streams

You can build custom applications that process or analyse streaming data for specialised needs. You can add various types of data such as clickstreams, application logs, and social media to a Kinesis data stream from hundreds of thousands of sources.

Data is sent to steams and stored in shards. Default storage is 24 hours but can be up to 7 days. Long term data retention greater than 7 days and up to 365 days lets you reprocess old data for use cases such as algorithm back testing, data store backfills, and auditing. You can then pass this data onto consumers. Can attach up to 20 consumers per stream, each with its own dedicated read throughput. It will scale automatically by default.

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

#### Sequence Number

A unique identifier for each record. It is assigned by Kinesis when a data producer calls `PutRecord` or `PutRecords` operation to add data to the stream. Sequence numbers for the same partition key generally increase over time, the longer the time period between the put operations, the larger the sequence numbers become.

#### Capacity Mode

Determines how capacity is managed and usage is charged for a stream. You can choose between provisioned and on-demand modes. In on-demand mode, AWS manages the shards to provide the necessary throughput, you only pay for the actual throughput used. You can switch between the two modes twice a day.

#### Kinesis Agent

A prebuilt Java application that offers an easy way to collect and send data to the stream. You can install it on a Linux-based environment, it can monitor files and send data to your stream.

#### Reading and Processing Data

A consumer is an application that processes all data from a stream. You can choose between fan-out and enhanced fan-out.

Shared fan-out all share a shards 2MB/second of read throughput and five transactions per second limits and require the use of `GetRecords` API.

Enhanced fan-out consumer gets its own 2MB/second allotment of read throughput, allowing multiple consumers to read data from the same stream in parallel, without contending for read throughput with other consumers.

#### On-Demand Mode

A new on-demand mode stream has a quota of 4MB/second and 4,000 records per second for writes. By default, these streams automatically scale up to 200MB/second and 200,000 records per second for writes.

#### Schema Registration

Clients of Data Streams can use the AWS Glue Schema Registry, a serverless feature of Glue. This is available at no additional charge.

#### Encryption

You can add encryption either by:

- Using the fully managed server-side encryption, it automatically encrypts and decrypts data as you put and get it from the data stream.
- You can write encrypted data to the stream by encrypting and decrypting client side.

Server-side encryption makes reading or writing impossible if the user does not have permission to use the key selected for encryption.

There is a cost for server-side encryption, however, if you are using the AWS managed KMS key for Kinesis and are not exceeding free tier KMS usage your server-side encryption is free.

#### Working out the Required Throughput

```
incoming_write_bandwidth_in_KB = average_data_size_in_KB * number_of_records_per_second

outgoing_read_bandwidth_in_KB = incoming_write_bandwidth_in_KB * number_of_consumers

number_of_shards = max (incoming_write_bandwidth_in_KB/1000, outgoing_read_bandwidth_in_KB/2000)
```

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
