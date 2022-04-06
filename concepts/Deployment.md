## Deployment

#### AWS Code Services

Source (AWS CodeCommit) -> Build (AWS CodeBuild) -> Test -> Production (AWS CodeDeploy) -> Monitor (AWS X-Ray, AWS Cloudwatch)

#### AWS CodeCommit

Source code repository. Equivalent to Github or Bitbucket.

#### AWS CodeBuild

Compiles source code, runs test and created packages. Equivalent to Jenkins.

#### Test

Up to the user to decide what commercial tool they prefer or are using.

#### AWS CodeDeploy

Automates deployments to any instance, can deploy to EC2 or external servers. Works with any language on any operating system. Integrates with 3rd party tools and other AWS services.

#### AWS CodePipeline

Orchestrates the CI/CD pipeline, provides fast and reliable application updates. Allows you to model and visualise the release process, linking up the other services.

#### AWS Elastic Beanstalk

Allows you to deploy your application without worrying about the infrastructure or underlying technologies. Targeted at full stack environments for web and worker tiers. Simple to use but less fine grained control. Can provide dev, test environments, or full production environments with load balancing and scaling.

Components:

- Environment
- Application versions
- Configuration

Permission Model:

- Service role
- Instance role

#### AWS OpsWorks

Configuration management service that provides managed instances of Chef and Puppet.

#### AWS CloudFormation

Infrastructure as Code.

##### Template

- Define resources to create
- Code your infrastructure in either JSON or YAML

##### Stack

- Create from templates
- Create multiple stacks (multiple regions) from the same template
- Monitor progress of stack updates; in progress, complete, failed

##### Template Sections

- `AWSTemplateFormatVersion`
- `Description`
- `Metadata`
- `Parameters`
- `Mappings`
- `Conditions`
- `Resources`
- `Outputs`

##### Built-in Functions (intrinsic functions)

These usually start with `Fn:*` or is `Ref`.

### Serverless

Allows you to build and run applications without thinking about servers, doesn't require any provisioning, managing or scaling of servers. It allows developers to work on the core application rather than the operation.

It is made up of the following services:

#### AWS Lambda (Compute)

Event Sources that can trigger Lambda:

- Data Stores
  - AWS S3
  - AWS DynamoDB
  - AWS Kinesis
  - AWS Cognito
- Endpoints
  - AWS API Gateway
  - AWS IoT
  - AWS Step Functions
  - Amazon Alexa
- Development and Management Tools
  - AWS CloudFormation
  - AWS CloudTrail
  - AWS CodeCommit
  - AWS CloudWatch
- Event/Message Service
  - AWS SES
  - AWS SNS
  - AWS SQS
  - Event Crons

#### AWS API Gateway (API Proxy)

Fully managed way to create, publish, maintain, monitor and scale APIs at any scale. Can be used for RESTful APIs and WebSocket APIs.

#### AWS S3 (Storage)

Simple Storage Service, an object storage service.

#### AWS DynamoDB (Database)

Fully managed, serverless, key-value NoSQL database designed to run at any scale.

#### AWS SNS & SQS (Interprocess Messaging)

Simple Notification Service, a fully managed messaging service for both application-to-application (A2A) and application-to-person (A2P) communication.

The pub/sub functionality provides topics for push-based, many-to-many messaging between distributed systems, microservices, and event-driven serverless applications.

You can use topics to fanout message to multiple subscribers, including AWS SQS queue, AWS Lambda functions, HTTPS endpoints, and AWS Kinesis Data Firehose, for parallel processing.

The A2P functionality enables you to send messages to users at scale via SMS, mobile push, and email.

#### AWS Step Functions (Orchestration)

A low-code, visual workflow service that can be used to build distributed applications, automate IT and business processes, and build data and machine learning pipelines with AWS services. The workflows manage failures, retries, parallelisation, service integrations, and observability, allowing developers to focus on the the business logic.

#### AWS Kinesis, AWS Athena (Analytics)

AWS Kinesis makes it easy to collect, process, and analyse real-time, streaming data. Can ingest real-time data such as video, audio, application logs, website clickstreams, and IoT telemetry data. Allows you to process and analyse data as it arrives instantly rather than having to wait till all of the data is collected.

AWS Athena is an interactive query service that makes it easy to analyse data in AWS S3 using standard SQL. It is serverless, so there is no infrastructure to manage, you just pay for the queries you make.

#### Tooling (Developer Tools)

### Serverless Application Model (SAM)

CloudFormation extension optimised for serverless. It offers new serverless resource types; functions, API, and tables. Also supports anything CloudFormation supports.