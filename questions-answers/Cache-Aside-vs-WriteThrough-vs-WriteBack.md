

# Cache Aside vs Write Through vs Write Back

## Why This Comparison Matters?

Caching improves system performance by reducing database load and improving latency.

Choosing the wrong cache pattern can create:

- Data inconsistency
- Higher latency
- Database bottlenecks
- Cache failures
- Operational complexity

Understanding cache patterns is important for:

- System Design Interviews
- Distributed Systems
- Scalability Design
- Production Systems

---

## Cache Aside Pattern

Application manages cache directly.

Read Flow:

```text
Read Request
     ↓
Check Cache
     ↓
Cache Hit?
 ↓       ↓
Yes      No
 ↓       ↓
Return   Read Database
Data         ↓
         Update Cache
             ↓
         Return Data
```

Write Flow:

```text
Write Database
      ↓
Invalidate Cache
```

Advantages:

- Simple implementation
- Lower cache storage usage
- Common production approach

Challenges:

- Cache miss latency
- Cache consistency issues

Production Examples:

- Redis + Database
- Social Feed Systems
- Product Catalog Systems

---

## Write Through Cache

Application writes cache and database together.

Flow:

```text
Write Request
      ↓
Update Cache
      ↓
Update Database
      ↓
Return Success
```

Read Flow:

```text
Read Request
      ↓
Read Cache
```

Advantages:

- Better consistency
- Faster reads

Challenges:

- Higher write latency
- Extra cache storage

Production Examples:

- Banking Systems
- User Profile Systems

---

## Write Back Cache

Application writes cache first.

Database update happens later asynchronously.

Flow:

```text
Write Request
      ↓
Update Cache
      ↓
Return Success
      ↓
Async Database Update
```

Advantages:

- Lower write latency
- Better write performance

Challenges:

- Data loss risk
- Recovery complexity

Production Examples:

- Analytics Systems
- High Throughput Platforms

---

## Comparison Table

| Feature | Cache Aside | Write Through | Write Back |
|----------|--------------|----------------|------------|
| Read Speed | Fast | Fast | Fast |
| Write Speed | Moderate | Slower | Fastest |
| Consistency | Moderate | Strong | Weak |
| Database Load | Lower | Higher | Lowest |
| Complexity | Low | Medium | Higher |
| Data Loss Risk | Low | Low | Higher |

---

## Interview Shortcut

Remember:

```text
Cache Aside
→ Database First

Write Through
→ Cache + Database Together

Write Back
→ Cache First Database Later
```

---

## When To Use?

Cache Aside:

- Read heavy systems
- Social platforms
- E commerce systems

Write Through:

- Banking systems
- User profile systems

Write Back:

- Analytics systems
- High throughput workloads

---

## Interview Questions

1. Cache Aside vs Write Through?

2. Why Cache Aside is common?

3. Why Write Back improves performance?

4. Write Back risk?

5. Which pattern works best for banking?

6. Which cache pattern is most common in production?

---

## Quick Revision

- Cache reduces database load
- Cache Aside is most common
- Write Through improves consistency
- Write Back improves write performance
- Async writes improve throughput
- Cache consistency is interview favorite
- Cache choice depends on workload