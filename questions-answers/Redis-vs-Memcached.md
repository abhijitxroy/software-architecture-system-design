

# Redis vs Memcached

## Why This Comparison Matters?

Redis and Memcached are popular caching technologies.

System design interviews commonly ask when to choose Redis and when Memcached is a better option.

Choosing the wrong cache technology can create:

- Higher latency
- Infrastructure inefficiency
- Scalability problems
- Memory limitations
- Operational complexity

Understanding caching systems is important for:

- System Design Interviews
- Distributed Systems
- Performance Optimization
- Production Architecture

---

## Redis

Redis is an in memory data store.

Primary Goal:

```text
Low Latency
Rich Data Structures
```

Supports:

- String
- List
- Set
- Hash
- Sorted Set
- Pub Sub

Flow:

```text
Application
    ↓
Redis
    ↓
Response
```

Best For:

- Cache Layer
- Session Store
- Rate Limiter
- Leaderboard
- Pub Sub Messaging

Pros:

- Extremely fast
- Multiple data structures
- Persistence support
- Replication support

Cons:

- Higher memory cost
- Operational complexity higher

---

## Memcached

Memcached is a distributed memory cache.

Primary Goal:

```text
Simple Cache
High Performance
```

Flow:

```text
Application
     ↓
Memcached
     ↓
Response
```

Best For:

- Database Query Cache
- Simple Object Cache
- Read Heavy Workload

Pros:

- Very lightweight
- Easier setup
- Lower memory overhead
- Fast performance

Cons:

- Limited data types
- No persistence
- Feature set smaller

---

## Key Differences

| Feature | Redis | Memcached |
|----------|-------|------------|
| Data Structure | Rich | Key Value Only |
| Persistence | Yes | No |
| Replication | Yes | Limited |
| Pub Sub | Yes | No |
| Memory Efficiency | Moderate | Better |
| Complexity | Higher | Lower |
| Best For | Advanced Cache | Simple Cache |

---

## Production Example

Gaming Leaderboard:

```text
Need Ranking Support
```

Choose:

```text
Redis
```

Database Cache:

```text
Need Simple Cache
```

Choose:

```text
Memcached
```

---

## Interview Shortcut

Remember:

```text
Redis
→ Rich Features

Memcached
→ Simple Cache
```

---

## Interview Questions

1. Redis vs Memcached?

2. Why Redis supports leaderboard systems?

3. Why Redis is more feature rich?

4. Why Memcached uses less memory?

5. Session storage technology choice?

6. Cache layer technology decision?

---

## Quick Revision

- Redis supports persistence
- Redis provides rich data structures
- Memcached focuses on simple caching
- Redis commonly powers session systems
- Memcached works well for read heavy cache
- Technology choice depends on workload
- Cache systems are common interview topics