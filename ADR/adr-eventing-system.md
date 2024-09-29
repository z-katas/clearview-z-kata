# Choosing Message queue vs Event stream

## Status
Accepted 

## Context
Clearview system, a distributed system, follows event driven architecture in most of its applications. Therefore, we ned to chose an appropriate eventing system that help the platform in meeting the scaling needs

### Alternatives
* Message queue
* Pub/Sub system


### PrOACT 

| Criteria                         | Message Queue                                        | Pub/Sub                                                  | Clearview Requirement                                                                                           |
|-----------------------------------|-----------------------------------------------------|----------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|
| Communication Model               | Point-to-point (one producer, one consumer).         | Broadcast (one producer, multiple subscribers).           | Multiple services must respond to the same event (e.g., user profile update notification, recommendation engine). Pub/Sub is more suitable here. |
| Decoupling                        | Moderate decoupling; consumers need to know the queue. | High decoupling; producers and consumers don't need to know about each other. | Clearview requires microservices to communicate asynchronously without tight coupling, favoring Pub/Sub.        |
| Message Delivery                  | A message is consumed by only one consumer.          | Messages are delivered to all subscribers.               | Multiple components should respond to the same event (e.g., notifications, recommendations). Pub/Sub is better. |
| Ordering                          | Typically FIFO (depending on queue implementation).  | No strict guarantee of order across subscribers.          | Ordering is crucial in some operations (e.g., transaction processing), favoring queues for certain tasks.       |
| Load Balancing                    | Consumers can pull messages at their own pace, facilitating load balancing. | No load balancing; all subscribers get all messages.     | Queues are useful for tasks where controlled, balanced consumption is needed (e.g., heavy background jobs).      |
| Event Broadcasting                | Not inherently designed for broadcasting.            | Built for broadcasting events to multiple consumers.      | The Clearview system needs event broadcasting for microservices (e.g., a job post triggers multiple actions).    |
| Scalability                       | Scales with the number of consumers.                 | Scales well with high throughput and large numbers of subscribers. | Clearview should scale with high event throughput and support multiple subscribers. Pub/Sub is more scalable for these needs. |
| Durability and Reliability        | High reliability; guarantees that messages are processed once. | Reliable, but requires handling of duplicate messages due to at-least-once delivery guarantees. | Clearview needs guaranteed message delivery for transactional workflows, favoring message queues in specific cases. |
| Use Cases                         | Task processing, background jobs (e.g., job match calculation). | Event-driven, microservices communication, notifications. | Both patterns have applicable use cases in Clearview, but for event-driven workflows, Pub/Sub is the better choice. |
| Latency                           | Usually higher due to sequential processing.         | Lower latency in delivering real-time events.             | Clearview requires low-latency updates (e.g., real-time notifications), favoring Pub/Sub.                        |
| Event History and Replay          | Typically no replay of messages once processed.      | Supports replaying events or event sourcing.              | Pub/Sub’s event replay and historical event management can be valuable for debugging or state reconstruction.    |
| Complex Event Processing          | Limited capabilities for complex event processing.   | Supports filtering, aggregation, and pattern matching.    | For advanced workflows (e.g., recommendations), Pub/Sub offers more flexibility.                                 |
| Integration with Clearview's Architecture | Can integrate into certain workflows (e.g., background job processing). | Better fit for event-driven microservices and asynchronous communication. | Clearview's architecture and need for real-time, event-driven communication align better with Pub/Sub.            |



## Decision
**Pub/Sub**
Based on the requirements of clearview system, pub/sub is preferrable over message queues. Since there are events such as RESUME_UNLOCED which needs to be subscribed and processed more than one service(Invoice service and Integration service). There are few use cases for which message queues is applicable, however, for the sake of simplicity in the system, it is preferrable to use a single eventing system for all use cases.

## Trade-offs
* Pub/Sub systems don’t guarantee strict message ordering across subscribers, which can cause issues when processing dependent events. We can use partitioned topics based on a key (e.g user id) to ensure that events related to the same entity are processed in order.


## References
https://systemdesignschool.io/blog/message-queue-vs-pub-sub
