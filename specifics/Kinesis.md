## Kinesis

AWS Kinesis makes it easy to collect, process, and analyse real-time, streaming data. Can ingest real-time data such as video, audio, application logs, website clickstreams, and IoT telemetry data. Allows you to process and analyse data as it arrives instantly rather than having to wait till all of the data is collected.

### Streams

Data is sent to steams and stored in shards. Default storage is 24 hours but can be up to 7 days. You can then pass this data onto consumers. Can attach up to 20 consumers per stream, each with its own dedicated read throughput.

You can choose between on-demand and provisioned capacity.

Shards handle 5 transactions per second for reads, maximum of 2MB per second. 1000 records per second for writes, maximum of 1MB per second.

### Firehose

An extract, transform, and load (ETL) service that reliable captures, transforms, and delivers streaming data to data lakes, data stores, and analytic services.

Can load data into:

- S3
- Redshift
- OpenSearch Service
- HTTP endpoints
- Datadog
- New Relic
- MongoDB
- Splunk

### Analytics

Easiest way to transform and analyse streaming data in real time using Apache Flink.

Can run SQL queries on the data within Firehose or Streams. Can store the results in S3, Redshift, ElasticSearch cluster.
