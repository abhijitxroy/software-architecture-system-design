# Tiny URL System Design

## Problem Statement

Design a URL shortening service like:

- TinyURL
- Bitly

Features:

- Generate Short URL
- Redirect Short URL
- URL Expiration (Optional)
- Analytics (Optional)

Example:

Original URL:

```text
https://example.com/products/mobile/iphone15
```

Short URL:

```text
https://tiny.url/Ab12Cd
```

---

## Functional Requirements

System should support:

1. URL Shortening

2. URL Redirection

3. Custom Alias (Optional)

4. URL Expiration (Optional)

5. Click Analytics

---

## Non Functional Requirements

- High Availability
- Low Latency
- Scalability
- Fault Tolerance
- High Read Throughput

Interview Tip:

Tiny URL is:

```text
Read Heavy System
```

---

## Capacity Estimation

Assume:

```text
100 Million URLs / Month
```

Read Write Ratio:

```text
100 : 1
```

Reason:

One URL generated once.

Read many times.

---

## API Design

Create URL:

```text
POST /shorten
```

Request:

```json
{
  "url":"https://example.com"
}
```

Response:

```json
{
  "shortUrl":"tiny.url/Ab12Cd"
}
```

Redirect:

```text
GET /Ab12Cd
```

---

## Database Design

Table:

| ShortURL | LongURL | CreatedAt |
|-----------|----------|------------|
| Ab12Cd | example.com | Timestamp |

Database Choice:

SQL:

- MySQL
- PostgreSQL

NoSQL:

- Cassandra

Interview Tip:

Large scale TinyURL often uses:

```text
NoSQL
```

Reason:

Massive scale.

---

## URL Encoding

Common interview question.

Base62 Encoding:

Characters:

```text
[a-z]
[A-Z]
[0-9]
```

Total:

```text
62 Characters
```

Example:

```text
Database ID

10001

↓

Base62

Ab12Cd
```

Benefits:

- Small URL
- Unique generation

---

## High Level Design

```text
Client

↓

Load Balancer

↓

Application Server

↓

Redis Cache

↓

Database
```

---

## Cache Strategy

Frequently accessed URL:

```text
Redis
```

Flow:

```text
Short URL

↓

Cache Hit

↓

Return Long URL
```

Cache Miss:

```text
Database Lookup
```

Benefits:

- Lower latency
- Reduced database load

---

## Scaling Strategy

Database Scaling:

- Replication
- Sharding

Application Scaling:

- Horizontal Scaling
- Load Balancer

Cache Scaling:

- Redis Cluster

---

## Bottleneck

Possible issues:

- Hot URLs
- Database overload
- Cache miss spike

Solutions:

- Cache
- CDN
- Read Replica

---

## Production Example

Flow:

```text
User Opens

tiny.url/Ab12Cd

↓

Redis

↓

Database

↓

Redirect User
```

---

## Interview Questions

### Q1. Why Tiny URL is read heavy?

Generated once.

Accessed many times.

---

### Q2. Why Redis used?

Reduce database lookup.

---

### Q3. Why Base62 used?

Generate short unique URL.

---

### Q4. SQL or NoSQL?

Depends scale.

Massive scale:

NoSQL common.

---

## Quick Revision

- TinyURL → Read heavy
- Base62 → URL encoding
- Redis → Faster redirect
- Cache → Reduce DB load
- Sharding → Scale database
- Replication → Availability