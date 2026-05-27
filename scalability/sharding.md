# Database Sharding

## Definition

Sharding means splitting a large database into multiple smaller databases called shards.

Each shard stores part of the data.

Goal:

- Improve scalability
- Reduce database load
- Improve query performance

---

## Why Needed?

Without sharding:

```text
Users

↓

Single Database

↓

100 Crore Records

↓

Slow Queries
```

Problems:

- Database bottleneck
- Slow response time
- Storage limitation
- Write performance issues

Example:

```text
User Table

500 Million Records
```

Single database becomes difficult to scale.

---

## With Sharding

```text
Application

↓

Shard Router

↓

Shard-1   Shard-2   Shard-3
```

Benefits:

- Better write scalability
- Better performance
- Reduced database pressure

---

## How Sharding Works?

Steps:

1. Data divided using sharding key
2. Router determines shard
3. Data stored in target shard
4. Query routed to proper shard

Example:

User IDs:

```text
User 1001

↓

Shard-1
```

```text
User 2001

↓

Shard-2
```

---

## Horizontal Partitioning

Sharding is horizontal partitioning.

Example:

Before:

```text
Users Table

ID Name City

1  A    Delhi

2  B    Kolkata

3  C    Bangalore

4  D    Mumbai
```

After:

Shard 1:

```text
1 A Delhi

2 B Kolkata
```

Shard 2:

```text
3 C Bangalore

4 D Mumbai
```

---

## Sharding Strategies

## 1. Range Based Sharding

Data divided by ranges.

Example:

```text
Shard 1

User ID 1–100000
```

```text
Shard 2

User ID 100001–200000
```

Benefits:

- Simple implementation

Problem:

Uneven traffic distribution.

---

## 2. Hash Based Sharding

Shard selected using hash function.

Example:

```text
UserID % 3
```

```text
1001 % 3 = 2

↓

Shard 2
```

Benefits:

- Better distribution

Problem:

Resharding becomes difficult.

---

## 3. Geographic Sharding

Data divided by location.

Example:

```text
India Users

↓

India Database
```

```text
US Users

↓

US Database
```

Benefits:

- Lower latency
- Better locality

Common in global applications.

---

## Sharding vs Replication

| Feature | Sharding | Replication |
| ------- | ----------- | ------------ |
| Purpose | Scalability | Availability |
| Data Split | Yes | No |
| Data Copy | No | Yes |
| Write Scaling | Better | Limited |
| Read Scaling | Good | Better |

Interview Tip:

Sharding → Split Data

Replication → Copy Data

---

## Challenges

### Cross Shard Join

Example:

```text
Order Data

Shard 1
```

```text
User Data

Shard 2
```

Joining becomes difficult.

---

### Resharding

Traffic increases.

Need:

```text
3 Shards

↓

5 Shards
```

Data movement becomes complex.

---

### Hotspot Problem

One shard receives heavy traffic.

Example:

```text
Shard 2

90% Traffic
```

System becomes unbalanced.

---

## Production Examples

Large companies use sharding:

- Instagram
- Uber
- Amazon
- Netflix

Common databases:

- MongoDB
- Cassandra
- Vitess

---

## Real World Example

E-Commerce Platform:

Problem:

```text
500 Million Users
```

Solution:

```text
Shard 1

Asia Users
```

```text
Shard 2

Europe Users
```

Benefits:

- Faster query execution
- Better scaling

---

## Interview Questions

### Q1. Why sharding needed?

Improve scalability.

---

### Q2. Replication vs Sharding?

Replication copies data.

Sharding splits data.

---

### Q3. Which sharding strategy most common?

Hash based sharding.

---

### Q4. Biggest challenge in sharding?

Cross shard query complexity.

---

## Quick Revision

- Sharding → Split database
- Goal → Scalability
- Horizontal partitioning → Sharding
- Hash based → Better distribution
- Geographic → Regional routing
- Replication → Copy data
- Sharding → Split data
- Cross shard join → Complex operation
