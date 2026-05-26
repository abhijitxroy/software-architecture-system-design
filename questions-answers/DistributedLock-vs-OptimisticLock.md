

# Distributed Lock vs Optimistic Lock

## Why This Comparison Matters?

Distributed Lock and Optimistic Lock solve concurrency problems.

System design interviews commonly ask when to use locking strategies.

Choosing the wrong locking approach can create:

- Race conditions
- Data corruption
- Lower throughput
- Deadlocks
- Scalability problems

Understanding locking strategies is important for:

- System Design Interviews
- Distributed Systems
- Database Design
- Production Systems

---

## Distributed Lock

Distributed Lock ensures only one system instance accesses a shared resource at a time.

Goal:

```text
Prevent Multiple Systems
From Updating Same Resource
```

Example:

```text
Server A
 ↓
Acquire Lock
 ↓
Update Inventory
 ↓
Release Lock
```

Examples:

- Redis Lock
- ZooKeeper Lock
- etcd Lock

Best For:

- Inventory Systems
- Distributed Scheduler
- Payment Processing

Pros:

- Prevents concurrent modification
- Works across distributed systems

Cons:

- Lock contention
- Higher latency
- Deadlock risk

---

## Optimistic Lock

Optimistic Lock assumes conflicts are rare.

Instead of locking resource first, validate before update.

Goal:

```text
Detect Conflict
Before Commit
```

Example:

```text
Read Version = 5
       ↓
Update Data
       ↓
Check Version
       ↓
Version Changed?
 ↓           ↓
No           Yes
 ↓            ↓
Commit      Retry
```

Common implementation:

```text
Version Column
Timestamp Column
```

Best For:

- User Profile Update
- E Commerce Systems
- Read Heavy Systems

Pros:

- Better throughput
- No lock waiting
- Higher scalability

Cons:

- Retry overhead
- Conflict handling complexity

---

## Key Differences

| Feature | Distributed Lock | Optimistic Lock |
|----------|------------------|-----------------|
| Approach | Lock First | Validate Later |
| Throughput | Lower | Higher |
| Scalability | Moderate | Better |
| Conflict Handling | Prevent Conflict | Detect Conflict |
| Retry Required | No | Yes |
| Distributed System Support | Strong | Moderate |

---

## Production Example

Inventory Platform:

```text
5 Items Left

Need Strict Protection
```

Choose:

```text
Distributed Lock
```

User Profile Update:

```text
Conflict Rare
```

Choose:

```text
Optimistic Lock
```

---

## Interview Shortcut

Remember:

```text
Distributed Lock
→ Prevent Conflict

Optimistic Lock
→ Detect Conflict
```

---

## Interview Questions

1. Distributed Lock vs Optimistic Lock?

2. Why optimistic lock scales better?

3. Inventory system locking choice?

4. Why optimistic lock needs retry?

5. Redis distributed lock use case?

6. Race condition prevention approaches?

---

## Quick Revision

- Distributed lock prevents conflicts
- Optimistic lock detects conflicts
- Distributed lock works well for critical resources
- Optimistic lock improves throughput
- Retry mechanism is core optimistic lock concept
- Locking strategy depends on workload
- Locking is common interview topic