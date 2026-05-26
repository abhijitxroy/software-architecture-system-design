

# Strong Consistency vs Eventual Consistency

## Why This Comparison Matters?

Strong Consistency and Eventual Consistency are common distributed system concepts.

System design interviews frequently ask consistency tradeoffs because large scale systems must balance:

- Correctness
- Availability
- Latency
- Scalability
- User Experience

Understanding consistency models is important for:

- System Design Interviews
- Distributed Systems
- Database Design
- Production Architecture

---

## Strong Consistency

Strong Consistency guarantees users always see latest data.

Example:

```text
User A Updates Balance
       ↓
Database Updated
       ↓
User B Reads Balance
       ↓
Always Gets Latest Value
```

Goal:

```text
Correct Data
Every Read
```

Best For:

- Banking Systems
- Payment Platforms
- Inventory Systems

Pros:

- Data correctness
- Predictable behavior
- No stale reads

Cons:

- Higher latency possible
- Lower availability during failures
- Scaling harder

---

## Eventual Consistency

Eventual Consistency allows temporary stale data.

System guarantees data becomes consistent eventually.

Example:

```text
User Creates Post
       ↓
Region A Updated
       ↓
Region B Delayed
       ↓
Eventually Same Data
```

Goal:

```text
Availability
Scalability
```

Best For:

- Social Platforms
- Analytics Systems
- Recommendation Systems

Pros:

- Better availability
- Better scalability
- Lower latency

Cons:

- Stale reads possible
- Data propagation delay
- More application complexity

---

## Key Differences

| Feature | Strong Consistency | Eventual Consistency |
|----------|--------------------|----------------------|
| Data Correctness | Immediate | Delayed |
| Stale Read | No | Possible |
| Availability | Lower | Better |
| Latency | Higher | Lower |
| Scalability | Harder | Better |
| Best For | Banking | Social Systems |

---

## Production Example

Banking Platform:

```text
Wrong Balance
→ Not Acceptable
```

Choose:

```text
Strong Consistency
```

Social Feed:

```text
Few Seconds Delay
→ Acceptable
```

Choose:

```text
Eventual Consistency
```

---

## Production Reality

Large systems commonly combine both.

Example:

```text
Orders
↓
Strong Consistency

Analytics
↓
Eventual Consistency
```

---

## Interview Shortcut

Remember:

```text
Strong Consistency
→ Correct Data Now

Eventual Consistency
→ Correct Data Later
```

---

## Interview Questions

1. Strong Consistency vs Eventual Consistency?

2. Why social platforms use eventual consistency?

3. Banking consistency choice?

4. Why eventual consistency scales better?

5. Stale read meaning?

6. Production systems consistency strategy?

---

## Quick Revision

- Strong consistency guarantees latest data
- Eventual consistency allows temporary delay
- Banking systems prefer strong consistency
- Social systems commonly use eventual consistency
- Eventual consistency improves scalability
- Consistency tradeoff is common interview topic
- Production systems often combine both