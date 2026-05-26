# Cache Flow Diagram

## Definition

Cache flow explains how application requests move between Client, Cache and Database.

Goal:

- Reduce database load
- Improve response time
- Improve scalability

---

## Why Cache Needed?

Without Cache:

```text
Client

↓

Application

↓

Database
```

Problems:

- Slow response
- Database overload
- Increased latency

---

## Cache Flow

```text
Client

↓

Application

↓

Cache

↓

Database
```

---

## Cache Hit

Definition:

Requested data found in cache.

Flow:

```text
Client

↓

Application

↓

Cache

↓

Data Found

↓

Return Response
```

Benefits:

- Faster response
- Reduced database load

Example:

```text
User Profile

Already Cached

↓

Return Directly
```

---

## Cache Miss

Definition:

Requested data not available in cache.

Flow:

```text
Client

↓

Application

↓

Cache

↓

Data Missing

↓

Database

↓

Cache Updated

↓

Response Returned
```

Problems:

- Higher latency
- Database access needed

---

## Cache Aside Pattern

Most common pattern.

Flow:

```text
Read Request

↓

Check Cache

↓

Cache Miss

↓

Read Database

↓

Update Cache

↓

Return Response
```

Examples:

- Redis
- Memcached

---

## Write Through Cache

Flow:

```text
Write Request

↓

Cache Update

↓

Database Update
```

Benefits:

- Data consistency

Problem:

- Slower writes

---

## Write Back Cache

Flow:

```text
Write Request

↓

Cache Update

↓

Database Update Later
```

Benefits:

- Faster writes

Problem:

- Data loss risk

---

## Cache Eviction Policies

### LRU

Least Recently Used.

Old unused data removed.

---

### LFU

Least Frequently Used.

Less accessed data removed.

---

### TTL

Time based expiration.

Example:

```text
User Session

30 Minutes
```

---

## Production Example

E-Commerce Product Page:

Without Cache:

```text
Client

↓

Database

Every Request
```

With Cache:

```text
Client

↓

Redis

↓

Database Only Cache Miss
```

---

## Interview Questions

### Q1. Cache Hit vs Cache Miss?

Cache Hit:

Data found in cache.

Cache Miss:

Database lookup needed.

---

### Q2. Most common cache pattern?

Cache Aside.

---

### Q3. Why Redis used?

- Fast
- In-memory
- Scalable

---

## Quick Revision

- Cache → Faster response
- Cache Hit → Fast path
- Cache Miss → Database access
- Cache Aside → Most common
- LRU → Remove old data
- Redis → Production cache
# Cache Flow Diagram

## Purpose

Cache flow explains how requests move between application, cache and database.

Goals:

- Lower latency
- Reduce database load
- Improve scalability
- Improve throughput
- Improve user experience

---

## Why Cache?

Without Cache:

```text
Client
 ↓
Application
 ↓
Database
```

Problems:

- Slow response
- Database overload
- Higher latency
- Lower scalability

With Cache:

```text
Client
 ↓
Application
 ↓
Cache
 ↓
Database
```

Benefits:

- Faster response
- Lower database traffic
- Better scalability

---

## Cache Hit Flow

Requested data already exists in cache.

Flow:

```text
Client
 ↓
Application
 ↓
Cache
 ↓ HIT
Return Response
```

Benefits:

- Fast response
- Lower infrastructure load

Example:

```text
User Profile
↓
Already Cached
↓
Return Response
```

---

## Cache Miss Flow

Requested data not found in cache.

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
Return Response
```

Problems:

- Higher latency
- Database dependency

---

## Cache Aside Pattern

Most common production pattern.

Flow:

```text
Read Request
 ↓
Check Cache
 ↓ MISS
Read Database
 ↓
Update Cache
 ↓
Return Response
```

Best For:

- Read heavy systems
- Product catalog
- User profile

---

## Write Through Cache

Application updates cache and database together.

Flow:

```text
Write Request
 ↓
Cache Update
 ↓
Database Update
```

Benefits:

- Better consistency

Problem:

- Higher write latency

---

## Write Back Cache

Application updates cache immediately.

Database update happens later.

Flow:

```text
Write Request
 ↓
Cache Update
 ↓ Async
Database Update
```

Benefits:

- Faster writes

Problem:

- Data loss risk

---

## Cache Eviction Policies

### LRU

```text
Least Recently Used
↓
Old Data Removed
```

Best For:

- General caching

---

### LFU

```text
Least Frequently Used
↓
Less Accessed Data Removed
```

Best For:

- Stable access pattern

---

### TTL

```text
Time To Live
↓
Automatic Expiration
```

Example:

```text
User Session
↓
30 Minutes
```

---

## Production Example

E Commerce Product Page:

Without Cache:

```text
Client
 ↓
Database
 ↓
Every Request
```

With Cache:

```text
Client
 ↓
Redis
 ↓ MISS
Database
```

---

## Interview Notes

Common discussion:

```text
Cache Hit vs Cache Miss

Cache Aside vs Write Through

Redis vs Memcached
```

---

## Quick Revision

```text
Cache
→ Faster Response

Cache Hit
→ Fast Path

Cache Miss
→ Database Access

Cache Aside
→ Most Common Pattern

LRU
→ Remove Old Data
```