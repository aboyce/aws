## Simple Queue Service (SQS)

First ever AWS service.

Distributed queue system that allows generators and consumers to be different components. You can decouple the components of an application so that they run independently. Any component of a distributed application can store messages in the queue.

Message can be up to 256KB of text in any format. Each 64KB section of payload is billed as 1 request, so a 256KB request will be billed as four requests.

Can use SQS API to retrieve messages.

Can link auto-scaling with queue size.

Message can be kept in a queue for between 1 minute and 14 days. Default retention is 4 days.

SQS is a poll based system. Long polling is a blocking call that waits for a response or a timeout. Can be used to prevent constant polling.

### Standard Queues

Default queue type.

Standard queues support a nearly unlimited number of transactions per second (TPS) per API action.

A message is delivered at least once, but occasionally more than one copy of a message is delivered.

Occasionally, message might be delivered in an order different from which they are sent.

### FIFO (First-In-First-Out) Queues

Complements the Standard queues.

By default, FIFO queues support up to 300 messages per second (300 send, receive, or delete operations per second). When you batch 10 message per operation (maximum), FIFO queues can support up to 3,000 messages per second. If you require higher throughput, you can enable high throughput mode for FIFO on the Console, which will support up to 30,000 messages per second with batching, or up to 3,000 messages per second without batching.

A message is delivered once and remains available until a consumer processes and deletes it. Duplicates aren't introduced into the queue.

The order in which the message are sent and received is strictly preserved.

### Visibility Timeout

The amount of time the message is invisible after a reader picks it up. If processed before the timeout, it will be deleted. If not processed, it will be visible again. This can cause multiple reads. The default time is 30 seconds, maximum time is 12 hours. You should increase the timeout if it requires a long running task.
