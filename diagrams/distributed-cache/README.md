# Distributed Cache Diagram

## Definition

Distributed cache stores cached data across multiple cache servers.

Goal:

- Handle large traffic
- Improve scalability
- Improve availability
- Reduce database pressure

Examples:

- Redis Cluster
- Memcached Cluster

---

## Why Distributed Cache Needed?

Single cache server:

```text
Application

↓

Redis Server
```

Problems:

- Memory limitation
- Single point of failure
- Traffic bottleneck

Example:

```text
100 Million Users

↓

Single Redis

↓

Slow Response
```

---

## Distributed Cache Architecture

```text
Application

↓

Cache Router

↓

Cache-1  Cache-2  Cache-3
```

Benefits:

- Better scalability
- Better fault tolerance
- Traffic distribution

---

## Data Distribution

Data divided across cache nodes.

Example:

```text
User:1001

↓

Cache Node 1
```

```text
User:2001

↓

Cache Node 2
```

```text
User:3001

↓

Cache Node 3
```

---

## Cache Partitioning (Sharding)

Definition:

Split cache data into multiple cache servers.

Example:

```text
Shard 1

User 1–100000
```

```text
Shard 2

User 100001–200000
```

Benefits:

- Better scalability
- Lower memory pressure

Problem:

- Rebalancing complexity

---

## Cache Replication

Definition:

Copy cache data into multiple nodes.

Architecture:

```text
Primary Cache

↓

Replica Cache
```

Benefits:

- High availability
- Better fault tolerance

Problem:

```text
Replication delay
```

---

## Consistent Hashing

Definition:

Technique to distribute cache keys efficiently.

Example:

```text
User:1001

↓

Hash Function

↓

Cache Node
```

Benefits:

- Better distribution
- Less data movement

Interview Tip:

Distributed cache interviews often ask:

```text
Consistent Hashing
```

---

## Cache Failure Scenario

Before failure:

```text
Cache-1

Cache-2

Cache-3
```

Cache-2 fails:

```text
Traffic Redirect

↓

Remaining Nodes
```

Benefits:

- Better resilience

---

## Production Example

Instagram Feed:

Without distributed cache:

```text
Database

↓

Heavy Traffic

↓

Slow System
```

With distributed cache:

```text
Redis Cluster

↓

Fast Feed Loading
```

---

## Production Tools

- Redis Cluster
- Memcached
- Hazelcast
- Apache Ignite

---

## Interview Questions

### Q1. Why distributed cache needed?

Improve scalability and availability.

---

### Q2. Sharding vs Replication?

Sharding:

Split cache data.

Replication:

Copy cache data.

---

### Q3. Why Consistent Hashing used?

Reduce cache redistribution.

---

## Quick Revision

- Distributed cache → Multiple cache servers
- Sharding → Split cache
- Replication → Copy cache
- Consistent Hashing → Better distribution
- Redis Cluster → Production example
- Distributed cache → Scalability + availability
# Distributed Cache Diagram

## Purpose

Distributed cache stores cached data across multiple cache servers.

Goals:

- Improve scalability
- Improve availability
- Reduce database load
- Improve throughput
- Handle large traffic

Examples:

- Redis Cluster
- Memcached Cluster
- Hazelcast
- Apache Ignite

---

## Why Distributed Cache?

Without Distributed Cache:

```text
Application
 ↓
Single Cache Server
 ↓
Database
```

Problems:

- Memory limitation
- Single point of failure
- Traffic bottleneck
- Lower scalability

Example:

```text
100 Million Users
↓
Single Redis Server
↓
Slow Response
```

With Distributed Cache:

```text
Application
 ↓
Cache Router
 ↓
Multiple Cache Nodes
```

Benefits:

- Better scalability
- Better resilience
- Better traffic distribution

---

## Distributed Cache Architecture

```text
Application
 ↓
Cache Router
 ↓
Cache-1   Cache-2   Cache-3
```

Responsibilities:

- Traffic distribution
- Key routing
- Better load balancing

---

## Data Distribution

Cache keys distributed across nodes.

Example:

```text
User:1001
↓
Cache Node 1

User:2001
↓
Cache Node 2

User:3001
↓
Cache Node 3
```

Benefits:

- Better throughput
- Better memory utilization

---

## Cache Partitioning (Sharding)

Definition:

Split cache data across multiple cache servers.

Example:

```text
Shard 1
↓
User 1-100000

Shard 2
↓
User 100001-200000
```

Benefits:

- Better scalability
- Lower memory pressure

Problem:

```text
Shard Rebalancing
```

---

## Cache Replication

Definition:

Copy cache data across multiple nodes.

Flow:

```text
Primary Cache
 ↓
Replica Cache
```

Benefits:

- Better fault tolerance
- High availability

Problem:

```text
Replication Delay
```

---

## Consistent Hashing

Definition:

Distribute cache keys efficiently.

Flow:

```text
Cache Key
↓
Hash Function
↓
Cache Node
```

Benefits:

- Better distribution
- Less redistribution during scaling

Best For:

- Distributed cache scaling

---

## Cache Failure Scenario

Before Failure:

```text
Cache-1
Cache-2
Cache-3
```

Node Failure:

```text
Cache-2 Down
↓
Traffic Redirect
↓
Remaining Nodes
```

Benefits:

- Better resilience
- Better availability

---

## Production Example

Social Feed System:

Without Distributed Cache:

```text
Database
↓
Heavy Traffic
↓
Slow Response
```

With Distributed Cache:

```text
Redis Cluster
↓
Fast Feed Loading
```

---

## Interview Notes

Common discussion:

```text
Distributed Cache vs Single Cache

Consistent Hashing

Cache Sharding

Replication Delay
```

---

## Quick Revision

```text
Distributed Cache
→ Multiple Cache Nodes

Sharding
→ Split Cache Data

Replication
→ Copy Cache Data

Consistent Hashing
→ Better Distribution

Distributed Cache
→ Scalability + Availability
```