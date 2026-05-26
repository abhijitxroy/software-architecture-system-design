

# Cache vs Database

## Why This Comparison Matters?

Cache and Database solve different problems in distributed systems.

Many engineers confuse them because both store data.

Understanding differences is important for:

- System Design Interviews
- Scalability Design
- Distributed Systems
- Performance Optimization
- Production Architecture

---

## Cache

Cache is a high speed storage layer used to store frequently accessed data.

Primary goal:

```text
Reduce Latency
Reduce Database Load
```

Characteristics:

- Memory based storage
- Fast read access
- Temporary data
- Lower latency

Examples:

- Redis
- Memcached

Example:

```text
User Profile
    ↓
Cache
    ↓
Return Response
```

---

## Database

Database is the primary persistent storage system.

Primary goal:

```text
Durability
Consistency
Long Term Storage
```

Characteristics:

- Persistent storage
- Source of truth
- Supports queries
- Data durability

Examples:

SQL:

- PostgreSQL
- MySQL

NoSQL:

- Cassandra
- MongoDB

Example:

```text
Order Data
User Data
Payment Data
```

---

## Key Differences

| Feature | Cache | Database |
|----------|--------|-----------|
| Purpose | Speed | Persistence |
| Storage | Memory | Disk + Memory |
| Latency | Very Low | Higher |
| Data Lifetime | Temporary | Long Term |
| Query Capability | Limited | Strong |
| Durability | Lower | High |
| Source Of Truth | No | Yes |

---

## Architecture Example

Without Cache:

```text
Client
   ↓
Application
   ↓
Database
```

With Cache:

```text
Client
   ↓
Application
   ↓
Cache
 ↓    ↓
Hit   Miss
 ↓      ↓
Data Database
```

Benefits:

- Lower latency
- Better scalability
- Reduced database pressure

---

## Interview Shortcut

Remember:

```text
Cache
→ Performance

Database
→ Persistence
```

---

## When To Use Cache?

Use cache for:

- User profile cache
- Product catalog cache
- Session storage
- Timeline cache
- Frequently accessed data

---

## When Database Is Required?

Database required for:

- Payments
- Orders
- Transactions
- User records
- Long term storage

---

## Production Examples

Social Platform:

```text
Redis
 ↓
Timeline Cache

PostgreSQL
 ↓
Persistent Storage
```

E Commerce:

```text
Redis
 ↓
Product Cache

Database
 ↓
Inventory + Orders
```

---

## Interview Questions

1. Cache vs Database?

2. Why cache improves performance?

3. Why cache is not source of truth?

4. Cache miss problem?

5. Why production systems use both?

---

## Quick Revision

- Cache improves speed
- Database stores persistent data
- Cache reduces database load
- Database is source of truth
- Cache improves scalability
- Production systems commonly use both
- Cache solves latency problems