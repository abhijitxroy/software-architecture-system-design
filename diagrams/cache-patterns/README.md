

# Cache Patterns Diagram

## Purpose

Cache patterns improve application performance.

Goals:

- Lower latency
- Reduce database load
- Improve scalability
- Improve throughput

---

## Cache Aside Pattern

Application controls cache.

Flow:

```text
Client
 ↓
Application
 ↓
Cache
 ↓ MISS
Database
 ↓
Cache Update
 ↓
Response
```

Best For:

- Read heavy systems
- Product catalog
- User profile

Pros:

- Simple
- Common production pattern

Cons:

- Cache miss latency

---

## Write Through Pattern

Application writes cache and database together.

Flow:

```text
Client
 ↓
Application
 ↓
Cache
 ↓
Database
```

Best For:

- Strong consistency requirement

Pros:

- Cache remains updated

Cons:

- Higher write latency

---

## Write Behind Pattern

Application updates cache first.

Database update happens asynchronously.

Flow:

```text
Client
 ↓
Application
 ↓
Cache
 ↓ Async
Database
```

Best For:

- High write throughput

Pros:

- Faster writes

Cons:

- Data loss risk

---

## Refresh Ahead Pattern

Cache refreshes before expiration.

Flow:

```text
Cache Near Expiry
 ↓
Background Refresh
 ↓
Fresh Data Ready
```

Best For:

- Frequently accessed data

Pros:

- Lower cache miss probability

Cons:

- More infrastructure work

---

## Production Pattern Selection

```text
Read Heavy
↓
Cache Aside

Strong Consistency
↓
Write Through

Write Heavy
↓
Write Behind

Hot Data
↓
Refresh Ahead
```

---

## Interview Notes

Common discussion:

```text
Cache Aside vs Write Through

Write Through vs Write Behind
```

---

## Quick Revision

```text
Cache Aside
→ Read Optimization

Write Through
→ Consistency

Write Behind
→ Write Performance

Refresh Ahead
→ Lower Cache Miss
```