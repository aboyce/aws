## Certified Developer Associate

_Taken from [AWS Exam Guide](https://d1.awsstatic.com/training-and-certification/docs-dev-associate/AWS-Certified-Developer-Associate_Exam-Guide.pdf)_

### Domain 1: [Deployment](/concepts//Deployment.md)

- 1.1 Deploy written code in AWS using existing CI/CD pipelines, processes, and patterns.
  - Commit code to a repository and invoke build, test and/or deployment actions
  - Use labels and branches for version and release management
  - Use AWS CodePipeline to orchestrate workflows against different environments
  - Apply AWS CodeCommit, AWS CodeBuild, AWS CodePipeline, AWS CodeStar, and AWS CodeDeploy for CI/CD purposes
  - Perform a roll back plan based on application deployment policy
- 1.2 Deploy applications using AWS Elastic Beanstalk.
  - Utilize existing supported environments to define a new application stack
  - Package the application
  - Introduce a new application version into the Elastic Beanstalk environment
  - Utilize a deployment policy to deploy an application version (i.e., all at once, rolling, rolling with
    batch, immutable)
  - Validate application health using Elastic Beanstalk dashboard
  - Use Amazon CloudWatch Logs to instrument application logging
- 1.3 Prepare the application deployment package to be deployed to AWS.
  - Manage the dependencies of the code module (like environment variables, config files and
    static image files) within the package
  - Outline the package/container directory structure and organize files appropriately
  - Translate application resource requirements to AWS infrastructure parameters (e.g., memory,
    cores)
- 1.4 Deploy serverless applications.
  - Given a use case, implement and launch an AWS Serverless Application Model (AWS SAM)
    template
  - Manage environments in individual AWS services (e.g., Differentiate between Development,
    Test, and Production in Amazon API Gateway)

### Domain 2: [Security](/concepts/Security.md)

- 2.1 Make authenticated calls to AWS services.
  - Communicate required policy based on least privileges required by application.
  - Assume an IAM role to access a service
  - Use the software development kit (SDK) credential provider on-premises or in the cloud to
    access AWS services (local credentials vs. instance roles)
- 2.2 Implement encryption using AWS services.
  - Encrypt data at rest (client side; server side; envelope encryption) using AWS services
  - Encrypt data in transit
- 2.3 Implement application authentication and authorization.
  - Add user sign-up and sign-in functionality for applications with Amazon Cognito identity or
    user pools
  - Use Amazon Cognito-provided credentials to write code that access AWS services.
  - Use Amazon Cognito sync to synchronize user profiles and data
  - Use developer-authenticated identities to interact between end user devices, backend
    authentication, and Amazon Cognito

### Domain 3: [Development with AWS Services](/concepts/Development%20with%20AWS%20Services.md)

- 3.1 Write code for serverless applications.
  - Compare and contrast server-based vs. serverless model (e.g., micro services, stateless nature
    of serverless applications, scaling serverless applications, and decoupling layers of serverless
    applications)
  - Configure AWS Lambda functions by defining environment variables and parameters (e.g.,
    memory, time out, runtime, handler)
  - Create an API endpoint using Amazon API Gateway
  - Create and test appropriate API actions like GET, POST using the API endpoint
  - Apply Amazon DynamoDB concepts (e.g., tables, items, and attributes)
  - Compute read/write capacity units for Amazon DynamoDB based on application requirements
  - Associate an AWS Lambda function with an AWS event source (e.g., Amazon API Gateway,
    Amazon CloudWatch event, Amazon S3 events, Amazon Kinesis)
  - Invoke an AWS Lambda function synchronously and asynchronously
- 3.2 Translate functional requirements into application design.
  - Determine real-time vs. batch processing for a given use case
  - Determine use of synchronous vs. asynchronous for a given use case
  - Determine use of event vs. schedule/poll for a given use case
  - Account for tradeoffs for consistency models in an application design
- 3.3 Implement application design into application code.
  - Write code to utilize messaging services (e.g., SQS, SNS)
  - Use Amazon ElastiCache to create a database cache
  - Use Amazon DynamoDB to index objects in Amazon S3
  - Write a stateless AWS Lambda function
  - Write a web application with stateless web servers (Externalize state)
- 3.4 Write code that interacts with AWS services by using APIs, SDKs, and AWS CLI.
  - Choose the appropriate APIs, software development kits (SDKs), and CLI commands for the
    code components
  - Write resilient code that deals with failures or exceptions (i.e., retries with exponential back off
    and jitter)

### Domain 4: Refactoring

- 4.1 Optimize applications to best use AWS services and features.
  - Implement AWS caching services to optimize performance (e.g., Amazon ElastiCache, Amazon
    API Gateway cache)
  - Apply an Amazon S3 naming scheme for optimal read performance
- 4.2 Migrate existing application code to run on AWS.
  - Isolate dependencies
  - Run the application as one or more stateless processes
  - Develop in order to enable horizontal scalability
  - Externalize state

### Domain 5: Monitoring and Troubleshooting

- 5.1 Write code that can be monitored.
  - Create custom Amazon CloudWatch metrics
  - Perform logging in a manner available to systems operators
  - Instrument application source code to enable tracing in AWS X-Ray
- 5.2 Perform root cause analysis on faults found in testing or production.
  - Interpret the outputs from the logging mechanism in AWS to identify errors in logs
  - Check build and testing history in AWS services (e.g., AWS CodeBuild, AWS CodeDeploy, AWS
    CodePipeline) to identify issues
  - Utilize AWS services (e.g., Amazon CloudWatch, VPC Flow Logs, and AWS X-Ray) to locate a
    specific faulty component

### Key Tools, Technologies, and Concepts

- Analytics
- Application Integration
- Containers
- Cost and Capacity Management
- Data Movement
- Developer Tools
- Instances (virtual machines)
- Management and Governance
- Networking and Content Delivery
- Security
- Serverless

### Services and Features

#### Analytics:

- Amazon Elasticsearch Service (Amazon ES)
- Amazon Kinesis

#### Application Integration:

- Amazon EventBridge (Amazon CloudWatch Events)
- Amazon Simple Notification Service (Amazon SNS)
- Amazon Simple Queue Service (Amazon SQS)
- AWS Step Functions

#### Compute:

- Amazon EC2
- AWS Elastic Beanstalk
- AWS Lambda

#### Containers:

- Amazon Elastic Container Registry (Amazon ECR)
- Amazon Elastic Container Service (Amazon ECS)
- Amazon Elastic Kubernetes Services (Amazon EKS)

#### Database:

- Amazon DynamoDB
- Amazon ElastiCache
- Amazon RDS

#### Developer Tools:

- AWS CodeArtifact
- AWS CodeBuild
- AWS CodeCommit
- AWS CodeDeploy
- Amazon CodeGuru
- AWS CodePipeline
- AWS CodeStar
- AWS Fault Injection Simulator
- AWS X-Ray

#### Management and Governance:

- AWS CloudFormation
- Amazon CloudWatch

#### Networking and Content Delivery:

- Amazon API Gateway
- Amazon CloudFront
- Elastic Load Balancing

#### Security, Identity, and Compliance:

- Amazon Cognito
- AWS Identity and Access Management (IAM)
- AWS Key Management Service (AWS KMS)

#### Storage:

- Amazon S3

### Out of Scope

- AWS Application Discovery Service
- Amazon AppStream 2.0
- Amazon Chime
- Amazon Connect
- AWS Database Migration Service (AWS DMS)
- AWS Device Farm
- Amazon Elastic Transcoder
- Amazon GameLift
- Amazon Lex
- Amazon Machine Learning (Amazon ML)
- AWS Managed Services
- Amazon Mobile Analytics
- Amazon Polly
- Amazon QuickSight
- Amazon Rekognition
- AWS Server Migration Service (AWS SMS)
- AWS Service Catalog
- AWS Shield Advanced
- AWS Shield Standard
- AWS Snow Family
- AWS Storage Gateway
- AWS WAF
- Amazon WorkMail
- Amazon WorkSpaces
