# Database Scaling

## Definition

Database scaling improves database capacity to handle increasing traffic, larger data volume and higher application demand.

Goal:

- Improve performance
- Handle more users
- Reduce latency
- Improve availability

---

## Why Needed?

Small traffic:

```text
Users

↓

Single Database

✓ Works Fine
```

Large traffic:

```text
1 Million Users

↓

Single Database

↓

Slow Queries

↓

Application Slowdown
```

Problems:

- High latency
- Database bottleneck
- CPU overload
- Memory pressure
- Connection saturation

---

## Scaling Types

Two major approaches:

1. Vertical Scaling

2. Horizontal Scaling

---

## Vertical Scaling (Scale Up)

Increase database server resources.

Example:

Before:

```text
4 CPU

16 GB RAM
```

After:

```text
16 CPU

64 GB RAM
```

Architecture:

```text
Users

↓

Database Server

(Bigger Machine)
```

Benefits:

- Simple implementation
- No application change
- Easy maintenance

Problems:

- Hardware limit exists
- Expensive
- Single point of failure

Examples:

- Upgrade EC2 Instance
- Increase RAM
- Faster SSD

---

## Horizontal Scaling (Scale Out)

Add multiple database servers.

Architecture:

```text
Users

↓

Application

↓

Database Cluster

↓

DB1 DB2 DB3
```

Benefits:

- Better scalability
- High availability
- Better fault tolerance

Problems:

- Complex implementation
- Data consistency challenges

Examples:

- Sharding
- Replication

---

## Database Replication

Copy database data into multiple servers.

Architecture:

```text
Primary Database

↓

Replica 1

↓

Replica 2
```

Read queries:

```text
Replica Database
```

Write queries:

```text
Primary Database
```

Benefits:

- Better read performance
- High availability
- Backup support

Problem:

```text
Replication Lag
```

Data update delay between primary and replicas.

Production Examples:

- MySQL Replica
- PostgreSQL Replica

---

## Database Sharding

Large database split into smaller databases.

Example:

Without sharding:

```text
Users Table

1 Crore Records
```

With sharding:

```text
Shard1

User ID 1–1000000

Shard2

User ID 1000001–2000000
```

Benefits:

- Better scalability
- Reduced query load
- Faster performance

Problems:

- Complex joins
- Resharding difficulty

Production Examples:

- Instagram
- Uber
- Large E-Commerce Platforms

---

## Replication vs Sharding

| Feature | Replication | Sharding |
|----------|--------------|-----------|
| Goal | Read Scaling | Data Distribution |
| Data Copy | Yes | No |
| Write Scaling | Limited | Better |
| Complexity | Lower | Higher |

Interview Tip:

Replication → Availability

Sharding → Scalability

---

## Database Bottleneck Solutions

Common techniques:

- Connection Pooling
- Read Replica
- Caching
- Sharding
- Index Optimization

---

## Real World Example

E-Commerce Platform:

Problem:

```text
Festival Sale

100X Traffic
```

Solution:

```text
Read Replica

+

Redis Cache

+

Database Sharding
```

---

## Interview Questions

### Q1. Vertical vs Horizontal Scaling?

Vertical:

Increase machine capacity.

Horizontal:

Add machines.

---

### Q2. Replication vs Sharding?

Replication improves reads.

Sharding distributes data.

---

### Q3. Why replication lag happens?

Replica database synchronization delay.

---

## Quick Revision

- Scale Up → Bigger server
- Scale Out → More servers
- Replication → Copy data
- Sharding → Split data
- Read Replica → Better reads
- Sharding → Better write scaling
- Replication Lag → Data sync delay