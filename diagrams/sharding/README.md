

# Sharding Diagram

## Purpose

Sharding partitions data across multiple databases.

Goals:

- Horizontal scaling
- Higher throughput
- Better scalability
- Reduce database bottleneck
- Support large datasets

---

## High Level Flow

```text
Application
      ↓
Shard Router

 ↓       ↓       ↓

Shard 1  Shard 2  Shard 3

Users A-F
Users G-M
Users N-Z
```

Each shard stores part of the data.

---

## Production Flow

```text
Client
 ↓
Load Balancer
 ↓
Application Service
 ↓
Shard Router
 ↓
Shard Database
```

---

## Why Sharding?

Without Sharding:

```text
Single Database
↓
Traffic Growth
↓
Database Bottleneck
↓
Scaling Problem
```

Problems:

- Storage limitation
- Higher latency
- Write bottleneck
- Scaling difficulty

With Sharding:

```text
Partition Data
↓
Distribute Load
↓
Scale Horizontally
```

---

## Sharding Strategies

### Range Based Sharding

```text
1-100000
→ Shard 1

100001-200000
→ Shard 2
```

Best For:

- Ordered data

Problem:

- Hot shard risk

---

### Hash Based Sharding

```text
Hash(UserID)
↓
Shard Mapping
```

Best For:

- Better distribution

Problem:

- Rebalancing complexity

---

### Directory Based Sharding

```text
Lookup Table
↓
Shard Selection
```

Best For:

- Flexible routing

Problem:

- Metadata dependency

---

## Common Challenges

### Hot Shard

```text
Uneven Traffic
↓
One Shard Overloaded
```

### Rebalancing

```text
New Shard Added
↓
Move Existing Data
```

---

## Production Examples

Sharding commonly used in:

- Social platforms
- E Commerce systems
- Analytics systems
- Large scale SaaS platforms

---

## Interview Notes

Common discussion:

```text
Replication vs Sharding

Consistent Hashing

Shard Rebalancing
```

---

## Quick Revision

```text
Sharding
→ Data Partitioning

Horizontal Scaling
→ Primary Goal

Hot Shard
→ Uneven Traffic

Rebalancing
→ Operational Challenge
```