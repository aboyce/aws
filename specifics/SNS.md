## Simple Notification Service (SNS)

A fully managed messaging service for both application-to-application (A2A) and application-to-person (A2P) communication, that makes it easy to set up, operate, and send notifications

The pub/sub functionality provides topics for push-based, many-to-many messaging between distributed systems, microservices, and event-driven serverless applications. Pub/sub ensures that notifications will be pushed to clients to prevent them from having to poll for updates.

You can use topics to fanout message to multiple subscribers, including AWS SQS queue, AWS Lambda functions, HTTPS endpoints, and AWS Kinesis Data Firehose, for parallel processing. A topic is an access point for allowing recipients to dynamically subscript for identical copies of the same notification.

The A2P functionality enables you to send messages to users at scale via SMS, mobile push, and email.

A common pattern is to use SNS to publish messages to SQS message queues to reliably send messages to one or many systems asynchronously.

All notification messages will contain a single published message. It is unlikely, but not guaranteed that a message could be delivered multiple times, applications should be able to handle this. Due to networking, messages could arrive in an order different to that it was sent, but should not regularly happen.

You cannot recall a message once it has been published to a topic.

Some message are relevant or valuable for a limited period of time, you can set a TTL value for each message. When the TTL expires for a message that was not delivered and read by and end user, the message is deleted. There is a default TTL of 4 weeks for all mobile platforms. You can set TTL of 0 as a special case to attempt to deliver the message immediately, else let it expire.

### How does it work?

You must first create a 'topic' which is an 'access point' identifying a specific subject or event type for publishing messages and allowing clients to subscribe for notifications.

When created, the topic owner can set polices for who can publish messages or subscribe to notifications, specifying which notification protocols will be supported. Clients can subscribe or be subscribed by the topic owner.

### Benefits

- Instant, push based delivery
- Simple API making it easy to integrate into applications
- Flexible message delivery over multiple transport protocols
- Pay-as-you-go model with no upfront costs

### Topics

Limited to 256 characters, must be unique within an AWS account.

Topic owners can configure specific transports on their topics by setting the appropriate permissions through access control polices.

You can use message filtering to build simpler and more streamlined pub/sub architectures. Message filtering enables topic subscribers to selectively receive only a subset of the messages they are interested in, as opposed to all messages in a topic.

### Formats/Transports

Subscribers can receive notifications on any transport supported by the topic. A topic can support subscriptions and notification deliveries over multiple transports.

HTTP; subscribers specify a URL as part of subscription registration, notifications will be delivered through an HTTP POST.

Email; messages are sent to registered addresses as email. Email-JSON sends notifications as a JSON object, while email sends text-based email.

SQS; can specify a standard queue as the endpoint.

SMS; messages are sent to registered phone numbers are SNS text messages.

### Example Use Cases

Can be used for:

- Event notifications
- Monitoring applications
- Workflow systems
- Time-sensitive information updates
- Mobile applications

### Pricing

Pay-as-you-go model:

- $0.50 per 1,000,000 mobile push notifications
- $2.00 per 1,000 email/email-JSON notifications
- $0.60 per 1,000,000 HTTP/S notifications
- No charge (other that SQS charges) for SQS notifications
- No charge (other that Lambda charges) for Lambda notifications
- $0.19 per 1,000,000 (Kinesis charges apply) Kinesis notifications

### Simple Queue Service (SQS) Comparison

Both messaging systems.

SNS allows applications to send time-critical messages to multiple subscribers via a push mechanism.

SQS is a message queue system used by distributed applications to exchange message through a polling model, and can be used to decouple sending and receiving components. SQS allows flexibility for distributed components of applications to send and receive messages without requiring each component to be concurrently available.

### Amazon MQ Comparison

MQ supports industry-standard APIs and protocols so you can switch from and standards-based message broker to Amazon MQ without rewriting the messaging code in your applications.

If you are building a brand new application in the cloud, we recommend you consider SQS or SNS.

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
