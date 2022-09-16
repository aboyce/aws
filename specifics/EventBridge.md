# Amazon EventBridge

Provides real-time access to changes in data in AWS services, your own applications, and software as a service applications without writing code.

To get started, you can choose an event source on the EventBridge console, and select a target from a number of AWS services. EventBridge will automatically deliver event in near-real-time.

You can also publish your own event to EventBridge by generating custom application-level events and publish them via the EventBridge APIs. You can also set up scheduled events that are generated on a periodic basis.

The events are a specific JSON structure. Every event has the same top-level envelope fields, such as the source of the event, timestamp, and region. This is followed by a detail field, which is the body of the event.

You can add rules to filter which events are delivered to a target. A rule matches incoming events for a given event bus and routes them to targets for processing. A single rule can route to multiple targets, all of which are processed in parallel.

https://aws.amazon.com/eventbridge/faqs/
