# CDC Pipeline

## What is CDC Pipeline?

CDC (Change Data Capture) Pipeline is a data architecture pattern that captures database changes and streams them to downstream systems in near real time.

Instead of periodically copying entire datasets, CDC captures only inserts, updates and deletes.

CDC pipelines are widely used in:

- Data platforms
- Event driven systems
- Analytics platforms
- Data warehouse synchronization
- Real time dashboards
- Microservices integration

---

## Why CDC Pipeline?

Problems without CDC:

- Full database copy is expensive
- Batch processing increases latency
- Duplicate processing overhead
- Data freshness becomes poor
- Large scale synchronization becomes difficult

CDC improves:

- Near real time processing
- Lower infrastructure cost
- Better scalability
- Reduced database load
- Faster analytics availability

---

## High Level Architecture

```text
+-------------+
| Database    |
| MySQL       |
| PostgreSQL  |
+------+------+
       |
       | Change Events
       v
+-------------------+
| CDC Connector     |
| Debezium          |
+---------+---------+
          |
          | Stream Events
          v
+-------------------+
| Kafka / Queue     |
+---------+---------+
          |
          |
  +-------+-------+
  |               |
  v               v
Warehouse      Analytics
System         Dashboard
```

---

## Core Components

### Source Database

Primary transactional database.

Examples:

- MySQL
- PostgreSQL
- MongoDB
- Oracle

CDC captures changes from source systems.

---

### CDC Connector

Reads database changes.

Methods:

- Transaction log reading
- Binlog processing
- WAL processing
- Trigger based CDC

Examples:

- Debezium
- GoldenGate
- AWS DMS

---

### Event Streaming Layer

Buffers and distributes change events.

Examples:

- Kafka
- Pulsar
- Kinesis

Responsibilities:

- Event durability
- Scalability
- Consumer decoupling

---

### Consumer Layer

Consumes changes for downstream processing.

Examples:

- Data Warehouse
- Search Index
- Analytics Platform
- Recommendation System

---

## CDC Approaches

### Log Based CDC

Captures database transaction logs.

Example:

```text
INSERT User ID=100
UPDATE User Status=Active
DELETE User ID=120
```

Advantages:

- Low database overhead
- High scalability
- Near real time processing

Disadvantages:

- Database specific implementation

---

### Trigger Based CDC

Database triggers capture changes.

Advantages:

- Easier implementation

Disadvantages:

- Higher database overhead
- Performance impact

---

### Query Based CDC

Periodic polling identifies changes.

Example:

```sql
SELECT *
FROM orders
WHERE updated_at > last_sync_time;
```

Advantages:

- Simple implementation

Disadvantages:

- Increased latency
- Database pressure

---

## Event Flow Example

Example:

```text
Order Created
     ↓
MySQL Binlog
     ↓
Debezium
     ↓
Kafka Topic
     ↓
Analytics Pipeline
     ↓
Dashboard Updated
```

---

## Production Challenges

Common issues:

- Duplicate events
- Schema evolution
- Event ordering problems
- Backpressure
- Consumer lag

Solutions:

- Idempotent consumers
- Schema registry
- Partition strategy
- Retry handling
- Dead letter queue

---

## Production Examples

Examples:

- Data warehouse sync
- Real time analytics
- Fraud detection systems
- Recommendation platform
- Search indexing platform
- Event driven architecture

---

## Interview Questions

1. What is CDC Pipeline?

2. Why use CDC instead of batch processing?

3. Log based CDC vs trigger based CDC?

4. Why Kafka is commonly used with CDC?

5. How to handle duplicate CDC events?

6. CDC challenges in production?

---

## Quick Revision

- CDC captures inserts updates and deletes
- Log based CDC is preferred for scale
- Kafka commonly distributes CDC events
- CDC reduces database synchronization cost
- CDC improves data freshness
- Idempotency prevents duplicate processing
- CDC powers real time analytics systems
