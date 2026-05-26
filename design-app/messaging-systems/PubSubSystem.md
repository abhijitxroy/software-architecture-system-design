

# Publish Subscribe System

## What is Publish Subscribe System?

Publish Subscribe (Pub Sub) System is a messaging architecture pattern where producers publish messages without directly knowing consumers.

Consumers subscribe to topics and receive relevant events asynchronously.

Pub Sub enables loose coupling between services and improves scalability in distributed systems.

Pub Sub systems are widely used in:

- Event driven architecture
- Notification systems
- Microservices communication
- Analytics platforms
- Streaming systems
- Real time systems

---

## Why Pub Sub System?

Problems without Pub Sub:

- Tight service coupling
- Difficult scalability
- Synchronous communication bottlenecks
- Failure propagation
- Complex integration dependencies

Pub Sub improves:

- Scalability
- Reliability
- Loose coupling
- Event driven processing
- Independent service evolution

---

## High Level Architecture

```text
Publisher Service
       |
Publish Event
       |
       v
+----------------+
| Topic Broker   |
| Kafka / Pulsar |
| SNS / RabbitMQ |
+--------+-------+
         |
 +-------+-------+
 |       |       |
 v       v       v
Email  Analytics Cache
Svc    System    Layer
```

---

## Core Components

### Publisher

Publisher produces events.

Example:

```text
Order Created
→ Publish Event
```

Responsibilities:

- Event generation
- Topic selection
- Retry handling

---

### Topic

Topic acts as logical event channel.

Example:

```text
order-events
payment-events
notification-events
```

Benefits:

- Consumer isolation
- Event categorization

---

### Broker

Broker distributes messages.

Examples:

- Kafka
- RabbitMQ
- Pulsar
- Amazon SNS
- Google Pub Sub

Responsibilities:

- Message durability
- Delivery guarantee
- Consumer management

---

### Subscriber

Subscriber consumes messages.

Example:

```text
OrderCreated
↓
Send Email
```

Responsibilities:

- Event processing
- Retry handling
- Offset tracking

---

## Event Flow Example

E-commerce example:

```text
Order Created
      ↓
Publish Topic
      ↓
+-----+-----+
|     |     |
v     v     v
Email Analytics Inventory
```

Benefits:

- Independent processing
- Better scalability

---

## Delivery Models

### Push Model

Broker pushes messages.

Advantages:

- Lower latency

Disadvantages:

- Consumer overload risk

---

### Pull Model

Consumer pulls messages.

Advantages:

- Better consumer control

Examples:

- Kafka consumers

---

## Pub Sub vs Queue

| Feature | Pub Sub | Queue |
|----------|----------|-------|
| Consumer Model | Multiple Consumers | Single Consumer |
| Processing Style | Broadcast | Work Distribution |
| Coupling | Loose | Loose |
| Use Case | Notifications | Background Processing |
| Scaling | Consumer Scaling | Worker Scaling |

---

## Ordering and Reliability

Production considerations:

- Ordering guarantee
- Duplicate handling
- Retry mechanism
- Dead letter queue
- Idempotency

Example:

```text
Event Duplicate
↓
Idempotency Check
↓
Ignore Duplicate
```

---

## Production Challenges

Common issues:

- Duplicate delivery
- Consumer lag
- Event ordering problems
- Topic explosion
- Retry complexity

Solutions:

- Partition strategy
- Idempotent consumers
- Dead letter queue
- Auto scaling
- Monitoring

---

## Production Examples

Examples:

- Notification platform
- Order processing platform
- Streaming analytics
- Payment event system
- Distributed microservices platform

---

## Interview Questions

1. What is Pub Sub?

2. Queue vs Pub Sub?

3. Why Pub Sub improves scalability?

4. Why idempotency matters?

5. Push vs Pull model?

6. Pub Sub production challenges?

---

## Quick Revision

- Pub Sub decouples producers and consumers
- Topics organize event communication
- Brokers distribute messages reliably
- Multiple consumers improve scalability
- Idempotency prevents duplicate processing
- Pub Sub enables event driven architecture
- Loose coupling improves system evolution