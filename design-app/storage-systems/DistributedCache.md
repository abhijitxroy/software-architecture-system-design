# Distributed Cache System

## What is Distributed Cache?

Distributed Cache is a storage architecture used to store frequently accessed data across multiple cache servers to improve performance, scalability and latency.

Distributed cache reduces database load by serving repeated requests directly from memory.

Unlike local cache, distributed cache works across multiple machines.

Distributed cache systems are commonly used in:

- Social media platforms
- E commerce systems
- API platforms
- Recommendation systems
- Gaming infrastructure
- Large scale web applications

---

## Why Distributed Cache?

Problems without distributed cache:

- High database load
- Increased latency
- Poor scalability
- Expensive database queries
- Traffic bottlenecks

Distributed cache improves:

- Lower latency
- Better scalability
- Reduced database pressure
- Faster response time
- Higher throughput

---

## High Level Architecture

```text
Client Request
      |
      v
Application Layer
      |
      v
+----------------+
| Distributed    |
| Cache Cluster  |
| Redis Cluster  |
| Memcached      |
+--------+-------+
         |
Cache Hit?
  |     |
 Yes    No
  |     |
  v     v
Return Database Query
Data        |
            v
      Update Cache
```

---

## Core Components

### Cache Cluster

Stores cached data across multiple nodes.

Examples:

- Redis Cluster
- Memcached
- Hazelcast

Responsibilities:

- Data storage
- Request handling
- Replication

---

### Cache Key

Unique identifier for cached data.

Example:

```text
user:123:profile
product:1001
```

Requirements:

- Unique naming
- Predictable format

---

### Cache Eviction Policy

Controls cache cleanup.

Common strategies:

### LRU

Least recently used data removed first.

### LFU

Least frequently used data removed first.

### TTL

Data removed after expiration.

Example:

```text
Cache TTL = 10 Minutes
```

---

## Cache Access Patterns

### Cache Aside Pattern

Application checks cache first.

Flow:

```text
Read Request
     ↓
Check Cache
     ↓
Cache Miss
     ↓
Read Database
     ↓
Update Cache
```

Advantages:

- Simple implementation

---

### Write Through Cache

Data written to cache and database together.

Flow:

```text
Write Request
     ↓
Update Cache
     ↓
Update Database
```

Advantages:

- Better consistency

---

### Write Back Cache

Database updated asynchronously.

Advantages:

- Lower write latency

Challenges:

- Data durability risk

---

## Distributed Cache Scaling

Production systems commonly use:

```text
Consistent Hashing
       ↓
Cache Node Distribution
       ↓
Balanced Load
```

Benefits:

- Horizontal scaling
- Better availability

---

## Replication Strategy

Example:

```text
Primary Cache Node
       ↓
Replica Node
```

Benefits:

- Fault tolerance
- Reliability

---

## Production Challenges

Common issues:

- Cache stampede
- Cache invalidation
- Hot keys
- Memory pressure
- Data inconsistency

Solutions:

- Request coalescing
- TTL optimization
- Replication
- Consistent hashing
- Cache warming

---

## Production Examples

Examples:

- Redis Cluster
- CDN cache infrastructure
- Recommendation platform
- Social feed infrastructure
- API acceleration platform

---

## Interview Questions

1. What is Distributed Cache?

2. Cache aside vs write through?

3. Why cache invalidation is difficult?

4. Why consistent hashing matters?

5. Cache stampede problem?

6. Distributed cache production challenges?

---

## Quick Revision

- Distributed cache improves latency
- Cache reduces database load
- Consistent hashing improves scaling
- Replication improves reliability
- Cache eviction controls memory usage
- Cache aside pattern is commonly used
- Distributed cache improves throughput