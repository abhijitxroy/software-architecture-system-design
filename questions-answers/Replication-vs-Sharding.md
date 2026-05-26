

# Replication vs Sharding

## Why This Comparison Matters?

Replication and Sharding are common database scaling approaches.

System design interviews frequently ask when to use replication and when sharding becomes necessary.

Choosing the wrong scaling strategy can create:

- Database bottlenecks
- Higher latency
- Scalability limitations
- Reliability problems
- Infrastructure complexity

Understanding database scaling is important for:

- System Design Interviews
- Distributed Systems
- Database Design
- Production Architecture

---

## Replication

Replication creates multiple copies of data.

Goal:

```text
Improve Availability
Improve Read Scalability
```

Flow:

```text
Primary Database
      ↓
-----------------
↓               ↓
Replica 1    Replica 2
```

Example:

```text
Write
 ↓
Primary Database

Read
 ↓
Replica Database
```

Best For:

- Read Heavy Systems
- High Availability
- Disaster Recovery

Pros:

- Better read performance
- Backup capability
- Higher availability

Cons:

- Storage cost increases
- Replication lag possible
- Write scaling limited

---

## Sharding

Sharding splits data across multiple databases.

Goal:

```text
Improve Write Scalability
Handle Massive Data Growth
```

Flow:

```text
Users 1-1M
   ↓
Shard 1

Users 1M-2M
   ↓
Shard 2

Users 2M-3M
   ↓
Shard 3
```

Example:

```text
Shard Key
↓
User ID
```

Best For:

- Large Scale Systems
- Massive Write Workload
- Large User Base

Pros:

- Better write scalability
- Better storage scalability
- Horizontal scaling

Cons:

- Operational complexity
- Rebalancing difficulty
- Cross shard query complexity

---

## Key Differences

| Feature | Replication | Sharding |
|----------|-------------|-----------|
| Goal | Availability | Scalability |
| Data | Copied | Split |
| Read Performance | Better | Better |
| Write Performance | Limited | Better |
| Storage Cost | Higher | Distributed |
| Complexity | Lower | Higher |
| Best For | Read Heavy | Massive Scale |

---

## Production Example

News Platform:

```text
Millions Of Reads
```

Choose:

```text
Replication
```

Social Platform:

```text
Massive User Growth
```

Choose:

```text
Sharding
```

---

## Production Reality

Large systems commonly use both.

Example:

```text
Sharding
↓
Each Shard Uses Replication
```

Examples:

- Social Platforms
- E Commerce Systems
- Large SaaS Platforms

---

## Interview Shortcut

Remember:

```text
Replication
→ Copy Data

Sharding
→ Split Data
```

---

## Interview Questions

1. Replication vs Sharding?

2. Why replication improves read performance?

3. Why sharding improves write scalability?

4. Sharding challenges?

5. Cross shard query problem?

6. Why production systems use both?

---

## Quick Revision

- Replication copies data
- Sharding splits data
- Replication improves read scaling
- Sharding improves write scaling
- Sharding adds operational complexity
- Large systems commonly combine both
- Database scaling is a common interview topic