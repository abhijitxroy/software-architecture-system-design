

# Replication Diagram

## Purpose

Replication copies data across multiple servers.

Goals:

- Improve availability
- Improve fault tolerance
- Improve read scalability
- Reduce downtime
- Improve reliability

---

## High Level Flow

```text
Primary Database
      ↓
Replication

 ↓           ↓

Replica A    Replica B
```

Primary handles writes.

Replicas commonly handle reads.

---

## Production Flow

```text
Client
 ↓
Load Balancer
 ↓
Application Service
 ↓
Primary Database
 ↓
Replication
 ↓
Read Replicas
```

---

## Why Replication?

Without Replication:

```text
Single Database
↓
Traffic Increase
↓
Database Bottleneck
↓
Failure Risk
```

Problems:

- Single point of failure
- Read bottleneck
- Lower availability

With Replication:

```text
Primary Database
↓
Multiple Replicas
↓
Better Reliability
```

---

## Replication Models

### Primary Replica

```text
Primary
↓
Replica
Replica
```

Best For:

- Read heavy systems

---

### Multi Primary

```text
Primary A
↔
Primary B
```

Best For:

- Geo distributed systems

Problems:

- Conflict resolution

---

## Replication Lag

Replication takes time.

Example:

```text
Write Primary
↓
Replica Update Delayed
↓
Stale Read Risk
```

Common Solution:

```text
Read Critical Data
↓
Primary Database
```

---

## Production Examples

Replication commonly used in:

- E Commerce systems
- Social platforms
- Banking systems
- Analytics platforms

---

## Interview Notes

Common discussion:

```text
Replication vs Sharding

Replication Lag

Read Replica Strategy
```

---

## Quick Revision

```text
Replication
→ Data Copy

Primary
→ Write Traffic

Replica
→ Read Traffic

Replication Lag
→ Stale Read Risk
```