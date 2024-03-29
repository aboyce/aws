# Amazon EventBridge

Provides real-time access to changes in data in AWS services, your own applications, and software as a service applications without writing code.

To get started, you can choose an event source on the EventBridge console, and select a target from a number of AWS services. EventBridge will automatically deliver event in near-real-time.

You can also publish your own event to EventBridge by generating custom application-level events and publish them via the EventBridge APIs. You can also set up scheduled events that are generated on a periodic basis.

The events are a specific JSON structure. Every event has the same top-level envelope fields, such as the source of the event, timestamp, and region. This is followed by a detail field, which is the body of the event.

You can add rules to filter which events are delivered to a target. A rule matches incoming events for a given event bus and routes them to targets for processing. A single rule can route to multiple targets, all of which are processed in parallel.

There are over 90 AWS services available as event sources, and over 15 AWS services available as event targets.

The latency is about half a second, but this can vary.

You can tag rules, but you cannot tag event buses or event sources.

You can have cross-account events.

### Schemas

You can generate code from your schema in Java, Python, and TypeScript.

### EventBridge Archive and Replay

Event Replay is a new feature for EventBridge that allows customers to re-process past events back to an event bus or specific EventBridge rule. This allows developers to debug applications easily. Gives developers peace of mind that they will always have access to any event that has been pushed.

### How does it relate to CloudWatch

EventBridge builds upon and extends CloudWatch events. It uses the same service API and endpoint, and the same underlying service infrastructure. For existing CloudWatch customers nothing changes.

This is a set of new features that would enable customer to connect data from their own apps and third-party SaaS apps. Rather than keeping this beneath the CloudWatch service, this functionality has been released under a new name.

### Global Endpoints

Makes it easier for you to build highly available event-driven applications. You can replicate your events across primary and secondary regions to enable failover with minimum data loss along with the ability to failover automatically to a backup Region in the case of service disruptions.

You can configure failover criteria using CloudWatch alarms.

You publish events to the global endpoint, the events are routed to the event bus in your primary region. If errors are detected in the primary region, your health check is marked as unhealthy and incoming events are routed to the secondary region.

They are suitable for applications that do not require idempotency or can handle idempotency across regions. They are also well suited for applications that are tolerant of having up to 420 seconds of events being not replicated.

You should turn on replication to minimise the data at risk during a service disruption.

Global endpoints are available for custom events only, there will be support for events from AWS services in the future.
