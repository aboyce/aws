## Deployment

### CI/CD

Continuous integration; integrating changes into environments.

Continuous delivery/deployment; taking CI one step further and automatically releasing as soon as it passes all checks/stages.

### AWS Code Services

Source (AWS CodeCommit) -> Build (AWS CodeBuild) -> Test -> Production (AWS CodeDeploy) -> Monitor (AWS X-Ray, AWS Cloudwatch)

#### AWS CodeCommit

Source code repository. Equivalent to Github or Bitbucket.

#### AWS CodeBuild

Compiles source code, runs test and created packages. Equivalent to Jenkins.

### AWS CodeStar

Enables you to quickly develop, build and deploy applications on AWS. Provides a unified interface, enabling you to easily manage your software development activities in one place. Allows your whole team to work together securely. Each project comes with a dashboard powered by JIRA. There is no charge, you are only charged for the resources that are required, EC2 instances etc. Uses IAM for acces.

#### Test

Up to the user to decide what commercial tool they prefer or are using.

#### AWS CodeDeploy

Automates deployments to any instance, can deploy to EC2, external servers, or Lambda. Works with any language on any operating system. Integrates with 3rd party tools and other AWS services.

Can integrate with:

- Jenkins
- Github
- Atlassian
- Ansible
- Chef
- Puppet

##### In Place Deployment

It works through the instances and deploys them out. This causes reduced capacity. EC2 and on-premise only.

##### Blue/Green Deployment

Brings up new instances and swaps over when ready. No downtime and quick roll back.

##### Key Terms

- **Deployment Group** is a set of EC2 instances or Lambda where the new version is deployed
- **Deployment** is the process of applying update
- **Deployment Configuration** is the deployment rules and success/failure conditions
- **AppSpec File** defines deployment actions
- **Revision** is everything you need for a new version
- **Application** is the unique Id for the app you want to deploy, ensures correct combination of everything

##### AppSpec File

It is used to define parameters that are used for a CodeDeploy deployment.

For Lambda deployments:

- `version`, which is reserved for future use
- `resources` is the name/property of lambda
- `hooks` are Lambda functions to run at set points in the deployment lifecycle, can be used to test/validate deployments, e.g. `BeforeInstall`.

For EC2/On-Premise:

- `version`, which is reserved for future use
- `os` is the operating system
- `files` is the `source` and `destination` of the required files
- `hooks` specifies scripts to run within the deployment lifecycle

The `AppSpec` file must be in the root directory.

##### Hooks

1. `BeforeBlockTraffic` runs on instance before the are deregistered from the load balancer
2. `BlockTraffic` run when it is deregistered from the load balancer
3. `AllowBlockTraffic` runs tasks on instances after they are deregistered
4. `ApplicationStop`
5. `DownloadBundle`
6. `BeforeInstall`
7. `Install`
8. `AfterInstall`
9. `ApplicationStart`
10. `ValidateService`
11. `BeforeAllowTraffic`
12. `AllowTraffic`
13. `AfterAllowTraffic`

#### AWS CodePipeline

Orchestrates the CI/CD pipeline, provides fast and reliable application updates. Allows you to model and visualise the release process, linking up the other services. Can trigger a CodeDeploy from a commit.

#### AWS Elastic Beanstalk

Deploying applications to Elastic Beanstalk, more information on the service [here](/specifics/Elastic%20Beanstalk.md)

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

Infrastructure as Code, with resources defined as CloudFormation templates. CloudFormation interprets the template and makes the appropriate API calls.

It can be YAML or JSON, and these can/should be version controlled.

Can manage updates and dependencies.

Can rollback or delete the stack.

Main sections are:

- `Parameters`; input customer values
- `Conditions`; pre requirements etc.
- `Resources` (mandatory); the resources to create
- `Mappings`; e.g. region, AMI
- `Transforms`; reference code snippets

##### Nested Stacks

Allows reuse of code (CloudFormation templates) for common cases, prevents copy/pasting. Allows you to keep generic templates and reference them in your template. Declared as a resource that is of type `AWS::CouldFormation:Stack`. This is the same as Terraform modules.

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

Simple notification and queueing services, more information on SNS [here](/specifics/SNS.md) and more information on SQS [here](/specifics/SQS.md).

#### AWS Step Functions (Orchestration)

A low-code, visual workflow service that can be used to build distributed applications, automate IT and business processes, and build data and machine learning pipelines with AWS services. The workflows manage failures, retries, parallelisation, service integrations, and observability, allowing developers to focus on the the business logic.

They provide a graphical console to arrange and visualise the components of your application as a series of steps. This makes it easy to build multi-step applications. They provide blueprints for commonly encountered workflows.

They log the state of each step to help with debugging and automatically trigger and track steps, handling retries and fallback if there are errors.

Can have step branches or parallel and can handle millions of steps simultaneously. Can handle if the step takes seconds or months to complete.

##### State Language

Amazon State Language is a JSON based structured language used to define your state machine. A collection of state that can do work, task states, determine which states to transition to the next, which are called choice states. If execution is stopped with an error, you get a failed state.

#### AWS Kinesis, AWS Athena (Analytics)

AWS Kinesis data processing, more information on the service [here](/specifics/Kinesis.md)

AWS Athena is an interactive query service that makes it easy to analyse data in AWS S3 using standard SQL. It is serverless, so there is no infrastructure to manage, you just pay for the queries you make.

#### Tooling (Developer Tools)

### Serverless Application Model (SAM)

CloudFormation extension optimised for serverless. It offers new serverless resource types; functions, API, and tables. Also supports anything CloudFormation supports.

Provides simplified syntax for defining serverless resources (APIs, Lambda, DynamoDB tables etc.).

User the SAM CLI to package the deployment code, upload to S3 and then deploy.

#### Commands

`sam package` packages and uploads to S3

`same deploy` deploys using Cloud Formation
