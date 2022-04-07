## CloudWatch

Monitoring and observability service built for DevOps engineers, developers, site reliability engineers, IT managers, and product owners. It provides data and actionable insights to monitor your applications, respond to system-wide performance changes, and optimise resource utilisation.

By default, logs are stored indefinitely.

### Categories

#### Vended Logs

These are natively published by AWS services on your behalf. Currently, VPC Flow Logs and Route 53 logs are the two supported types.

#### Logs Published by AWS Services

Currently, more that 30 AWS services publish logs to CloudWatch. They include API Gateway, Lambda, CloudTrail (monitors API calls within AWS) and many more.

#### Custom Logs

These are logs from your application and on-premise resources.

### EC2

EC2, by default, monitors host metrics (CPU, network, disk, status check), RAM is custom. Monitoring is in 5 minute intervals by default, detailed is 1 minute.

The same logic used to send logs from on-premise resources can also be used for EC2 as they are just virtual servers. Can use CRONs etc. to push logs with more frequency.

Logs are kept for terminated instances.

### Config

AWS Config is a service that enabled you to assess, audit, and evaluate the configurations of your AWS resources. It can notify you when the configuration has been changed.
