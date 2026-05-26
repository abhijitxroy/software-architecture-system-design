

# Kafka System Design

## Problem Statement

Design a distributed event streaming platform like Kafka that supports high throughput messaging, event streaming and reliable asynchronous communication.

System should support:

- Producer Message Publish
- Consumer Message Processing
- Topic Management
- Partition Distribution
- Replication
- Consumer Group
- Fault Tolerance
- Event Retention

---

## Functional Requirements

### Core Features

- Publish event
- Consume event
- Topic creation
- Partition event
- Replicate data
- Replay event
- Consumer offset tracking
- Message retention

---

## Non Functional Requirements

### Scalability

- Millions of messages/sec
- Horizontal broker scaling

### Availability

- 99.99% uptime

### Reliability

- No message loss

### Durability

- Persistent event storage

### Latency

- Millisecond message delivery

---

## Capacity Estimation

Assume:

- 10 Million messages/sec
- Average event size: 1 KB

Traffic:

10M × 1 KB

≈ 10 GB/sec

Daily Storage:

≈ Petabyte scale yearly storage

Replication Factor:

3

---

## API Design

### Produce Event

```http
POST /produce
```

Request:

```json
{
 "topic":"payments",
 "message":"payment_success"
}
```

### Consume Event

```http
GET /consume?topic=payments
```

---

## High Level Design

```text
Producer
 |
Kafka Broker
 |
+----------------+
| Topic          |
| ├─Partition 0  |
| ├─Partition 1  |
| └─Partition 2  |
+----------------+
 |
Consumer Group
 |
Consumer 1
Consumer 2
Consumer 3

ZooKeeper / KRaft
 |
Cluster Metadata
```

---

## Core Components

### Producer

Responsibilities:

- Publish event
- Partition selection
- Retry failed publish

Partition Strategy:

- Round Robin
- Key Based Partition

### Broker

Responsibilities:

- Event persistence
- Replication
- Consumer delivery

### Topic

Topic contains:

- Partitions
- Event stream

Example:

```text
payments-topic
 ├─Partition 0
 ├─Partition 1
 └─Partition 2
```

### Partition

Benefits:

- Horizontal scale
- Parallel processing
- Ordering guarantee inside partition

### Consumer Group

Responsibilities:

- Parallel consumption
- Load balancing

Example:

```text
3 Partitions
3 Consumers

1 Consumer → 1 Partition
```

### Replication

Concepts:

- Leader Replica
- Follower Replica
- ISR (In Sync Replica)

Failure Flow:

```text
Leader Failure
 ↓
ISR Election
 ↓
New Leader
```

---

## Message Flow

```text
Producer
 ↓
Partition Selection
 ↓
Broker Persist
 ↓
Replication
 ↓
Consumer Poll
 ↓
Offset Commit
```

---

## Offset Management

Consumer Offset stores:

- Consumed message position

Example:

```text
Partition 0
Offset 100

Consumer restart
 ↓
Resume from 101
```

---

## Delivery Semantics

### At Most Once

- No duplicate
- Possible message loss

### At Least Once

- No message loss
- Possible duplicate

### Exactly Once

- No duplicate
- No message loss

---

## Scaling Strategy

### Broker Scaling

- Add broker
- Rebalance partition

### Partition Scaling

- Increase partition count

---

## Reliability

Strategies:

- Replication
- ISR
- Retry mechanism
- Dead letter topic

---

## Bottlenecks

| Problem | Solution |
|----------|-----------|
| Hot partition | Better partition key |
| Broker overload | Horizontal scale |
| Consumer lag | Add consumer |
| Broker failure | Replication |

---

## Tradeoffs

| Choice | Benefit | Drawback |
|---------|----------|-----------|
| More partitions | Better throughput | More management |
| Higher replication | Better durability | Higher storage |

---

## Interview Questions

1. Why partition needed?
2. Why ISR important?
3. How ordering maintained?
4. Consumer group purpose?
5. Why offset needed?
6. How Kafka scales?

---

## Quick Revision

- Partition improves scalability
- Replication improves durability
- Consumer group improves throughput
- ISR improves fault tolerance
- Offset tracks consumption state
- Ordering guaranteed inside partition