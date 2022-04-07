## Simple Notification Service (SNS)

A fully managed messaging service for both application-to-application (A2A) and application-to-person (A2P) communication, that makes it easy to set up, operate, and send notifications

The pub/sub functionality provides topics for push-based, many-to-many messaging between distributed systems, microservices, and event-driven serverless applications.

You can use topics to fanout message to multiple subscribers, including AWS SQS queue, AWS Lambda functions, HTTPS endpoints, and AWS Kinesis Data Firehose, for parallel processing. A topic is an access point for allowing recipients to dynamically subscript for identical copies of the same notification.

The A2P functionality enables you to send messages to users at scale via SMS, mobile push, and email.

Push based delivery.

### Pricing

Pay-as-you-go model:

- $0.50 per 1,000,000 mobile push notifications
- $2.00 per 1,000 email/email-JSON notifications
- $0.60 per 1,000,000 HTTP/S notifications
- No charge (other that SQS charges) for SQS notifications
- No charge (other that Lambda charges) for Lambda notifications
- $0.19 per 1,000,000 (Kinesis charges apply) Kinesis notifications

### Simple Email Service (SES) Comparison

SES is a scalable and highly available email service to help send marketing, notification, and transactional emails using a pay-as-you-go model.

Can be used to receive emails, can automatically be delivered to an S3 bucket. Incoming emails can also trigger Lambda and SNS notifications.

#### SES

- Email only
- Can trigger Lambda or SNS
- Both incoming or outgoing email
- Only need an email address to send

#### SNS

- Pub/sub messaging (SMS, HTTP, SQS, Email)
- Can trigger Lambda
- Can fan out messages
- Customers must subscribe to a topic to get notifications
