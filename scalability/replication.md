# Database Replication

## Definition

Replication means copying database data from one database server to one or more database servers.

Goal:

- Improve availability
- Improve read performance
- Backup support
- Disaster recovery

---

## Why Needed?

Without replication:

```text
Users

↓

Single Database

↓

Heavy Traffic

↓

Slow Queries
```

Problems:

- Database bottleneck
- Single point of failure
- Slow read performance

Example:

```text
1 Database

10000 Read Requests / Second
```

Database becomes overloaded.

---

## With Replication

```text
Users

↓

Application

↓

Primary Database

↓

Replica 1

↓

Replica 2
```

Benefits:

- Read scalability
- Better availability
- Better fault tolerance

---

## How Replication Works?

Steps:

1. Data written to Primary Database
2. Primary updates Replica Database
3. Replica databases synchronize data
4. Read requests served from replicas

Example:

```text
INSERT User

↓

Primary Database

↓

Replica Sync

↓

Replica Updated
```

---

## Primary Replica Model

Architecture:

```text
Write Requests

↓

Primary Database

↓

Replication

↓

Replica Database
```

Read Requests:

```text
Application

↓

Replica Database
```

Interview Tip:

Primary → Write

Replica → Read

---

## Types of Replication

## 1. Synchronous Replication

Primary waits for replica confirmation.

Flow:

```text
Primary Write

↓

Replica Update

↓

Success Response
```

Benefits:

- Strong consistency

Problems:

- Higher latency

Best for:

- Banking systems
- Financial systems

---

## 2. Asynchronous Replication

Primary does not wait.

Flow:

```text
Primary Write

↓

Success Response

↓

Replica Update Later
```

Benefits:

- Faster write performance

Problems:

- Replication lag

Most common production approach.

---

## Synchronous vs Asynchronous

| Feature | Synchronous | Asynchronous |
|----------|--------------|---------------|
| Speed | Slower | Faster |
| Consistency | Strong | Eventual |
| Latency | Higher | Lower |
| Replication Lag | No | Possible |

Interview Tip:

Banking → Synchronous

Social Media → Often Asynchronous

---

## Replication Lag

Definition:

Replica database updates slower than primary.

Example:

```text
Primary Updated

12:00:01
```

Replica Updated:

```text
12:00:05
```

Lag:

```text
4 Seconds
```

Problem:

User reads stale data.

Solutions:

- Faster network
- Better hardware
- Monitor replication health

---

## Failover

If Primary Database fails:

Before:

```text
Primary Database

↓

Replica Database
```

After failover:

```text
Replica Promoted

↓

New Primary
```

Benefits:

- High availability
- Disaster recovery

---

## Production Examples

Common databases:

- MySQL Replication
- PostgreSQL Replication
- MongoDB Replica Set

Cloud Examples:

- AWS RDS Read Replica
- Aurora Replica

---

## Real World Example

Instagram:

Problem:

```text
Millions Of Read Requests
```

Solution:

```text
Primary Database

+

Multiple Read Replicas
```

Benefits:

- Faster reads
- Better scaling

---

## Interview Questions

### Q1. Why replication needed?

Improve availability and read scalability.

---

### Q2. Primary vs Replica?

Primary:

Write operations.

Replica:

Read operations.

---

### Q3. Replication vs Sharding?

Replication:

Copy data.

Sharding:

Split data.

---

### Q4. What is replication lag?

Delay between primary update and replica update.

---

## Quick Revision

- Replication → Copy data
- Primary → Write
- Replica → Read
- Synchronous → Strong consistency