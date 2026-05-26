

# CAP Theorem Interview

## What is CAP Theorem?

CAP Theorem states that a distributed system can guarantee only two out of three properties during a network partition.

CAP stands for:

```text
C → Consistency
A → Availability
P → Partition Tolerance
```

Distributed systems must make tradeoffs.

CAP Theorem is a very common system design interview topic.

---

## Consistency (C)

Every user sees the latest data.

Example:

```text
User A Updates Balance
       ↓
User B Reads Balance
       ↓
Always Gets Latest Value
```

Goal:

- Same data everywhere
- No stale reads

Examples:

- Banking systems
- Payment systems

---

## Availability (A)

System always responds.

Even during failures.

Example:

```text
Server A Failed
      ↓
Another Node Responds
```

Goal:

- High uptime
- Fast response

Examples:

- Social media feed
- Streaming systems

---

## Partition Tolerance (P)

System continues working even if network communication breaks.

Example:

```text
Region A  X  Region B
(Network Failure)

System Still Runs
```

Goal:

- Fault tolerance
- Distributed reliability

Partition tolerance is mandatory for distributed systems.

---

## Why Tradeoff Happens?

Example:

```text
Node A
  X
Node B

(Network Partition)
```

Choose:

```text
Consistency
OR
Availability
```

Cannot guarantee both.

---

## CP System

Prioritizes:

```text
Consistency
+
Partition Tolerance
```

Behavior:

- Latest data guaranteed
- System may reject requests

Examples:

- HBase
- MongoDB (majority configuration)
- ZooKeeper

Best for:

- Banking
- Inventory systems

---

## AP System

Prioritizes:

```text
Availability
+
Partition Tolerance
```

Behavior:

- System stays online
- Stale reads possible

Examples:

- Cassandra
- DynamoDB
- DNS systems

Best for:

- Social feeds
- Recommendation systems

---

## CA System

Prioritizes:

```text
Consistency
+
Availability
```

Reality:

Distributed systems cannot avoid partitions.

CA mainly applies to:

- Single node databases
- Non distributed systems

---

## Interview Shortcut

Remember:

```text
CP
→ Correct Data

AP
→ Always Available
```

---

## Production Example

Social Platform:

```text
Feed Slightly Delayed
      ↓
System Still Available
```

Choose:

```text
AP
```

Banking Platform:

```text
Never Show Wrong Balance
```

Choose:

```text
CP
```

---

## Interview Questions

1. What is CAP Theorem?

2. Why partition tolerance matters?

3. CP vs AP?

4. Why CA is uncommon?

5. Banking system CAP choice?

6. Social media CAP choice?

---

## Quick Revision

- CAP means Consistency Availability Partition Tolerance
- Distributed systems require partition tolerance
- CP prioritizes correctness
- AP prioritizes uptime
- Banking commonly prefers CP
- Social systems commonly prefer AP
- CAP tradeoff is interview favorite