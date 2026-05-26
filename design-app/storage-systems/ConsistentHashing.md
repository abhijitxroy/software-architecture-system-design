# Consistent Hashing

## What is Consistent Hashing?

Consistent Hashing is a distributed systems technique used to distribute data across multiple servers while minimizing data movement when nodes are added or removed.

Traditional hashing causes large scale data redistribution during scaling operations.

Consistent hashing reduces redistribution and improves scalability.

Consistent hashing is widely used in:

- Distributed cache systems
- CDN infrastructure
- Database sharding
- Object storage systems
- Load balancing systems
- Distributed storage platforms

---

## Why Consistent Hashing?

Problems with traditional hashing:

- Large scale data movement
- Rebalancing overhead
- Scaling inefficiency
- Increased downtime risk
- Cache invalidation problems

Consistent hashing improves:

- Scalability
- Data distribution
- Rebalancing efficiency
- Fault tolerance
- Operational stability

---

## Traditional Hashing Problem

Example:

```text
Server Index = Hash(Key) % N
```

Example:

```text
4 Servers

User123 → Server 1

Add New Server

5 Servers

User123 → Server 3
```

Problem:

```text
Most keys move
```

Scaling becomes expensive.

---

## High Level Architecture

```text
Hash Ring

0 ---------------- 360
|                  |
|                  |
Node A         Node B
|                  |
|                  |
Node D         Node C

Key → Hash(Key)
     ↓
Clockwise Node Selection
```

Keys are assigned to nearest clockwise node.

---

## Core Components

### Hash Ring

Logical circular space.

Example:

```text
0 → 2^32
```

Benefits:

- Stable distribution
- Reduced movement

---

### Nodes

Servers placed on hash ring.

Example:

```text
Node A
Node B
Node C
```

Responsibilities:

- Store data
- Handle requests

---

### Key Mapping

Data keys hashed into ring.

Example:

```text
User123
   ↓
Hash(User123)
   ↓
Nearest Clockwise Node
```

Benefits:

- Deterministic routing

---

## Node Addition Example

Before:

```text
Node A
Node B
Node C
```

Add:

```text
Node D
```

Result:

```text
Only nearby keys move
```

Benefits:

- Lower redistribution cost

---

## Virtual Nodes

Virtual nodes improve load balancing.

Example:

```text
Physical Node A
 ├── Virtual Node A1
 ├── Virtual Node A2
 └── Virtual Node A3
```

Benefits:

- Better distribution
- Lower hotspot risk

---

## Replication Strategy

Production systems commonly replicate data.

Example:

```text
Primary Node
    ↓
Replica Node 1
    ↓
Replica Node 2
```

Benefits:

- Reliability
- Fault tolerance

---

## Production Challenges

Common issues:

- Hot partitions
- Uneven distribution
- Node failures
- Data replication complexity
- Rebalancing cost

Solutions:

- Virtual nodes
- Replication
- Monitoring
- Auto scaling
- Load balancing

---

## Production Examples

Examples:

- Redis Cluster
- Cassandra
- DynamoDB
- CDN infrastructure
- Distributed cache platform

---

## Interview Questions

1. What is Consistent Hashing?

2. Traditional hashing vs consistent hashing?

3. Why virtual nodes matter?

4. Why consistent hashing improves scalability?

5. How node addition impacts distribution?

6. Consistent hashing production challenges?

---

## Quick Revision

- Consistent hashing minimizes redistribution
- Hash ring improves scalability
- Virtual nodes improve balance
- Node addition impacts nearby keys only
- Replication improves reliability
- Consistent hashing improves distributed storage systems
- Distributed systems use consistent hashing for scalability