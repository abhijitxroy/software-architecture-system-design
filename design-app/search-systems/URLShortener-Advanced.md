

# URL Shortener Advanced System Design

## Problem Statement

Design a URL shortening service like Bitly or TinyURL that supports short URL generation, redirection, analytics and large scale traffic handling.

System should support:

- Short URL Generation
- URL Redirection
- Custom Alias
- URL Expiration
- Analytics Tracking
- Click Counting
- QR Code Support
- Abuse Detection

---

## Functional Requirements

### Core Features

- Create short URL
- Redirect short URL
- Custom alias support
- Expiration time support
- Click analytics
- QR code generation
- URL deletion
- User dashboard

---

## Non Functional Requirements

### Scalability

- Billions of URLs
- Millions of redirects/sec

### Availability

- 99.99% uptime

### Reliability

- No URL mapping loss

### Latency

- Redirect under 100 ms

---

## Capacity Estimation

Assume:

- 100 Million DAU
- 500 Million URLs/day
- Average short URL length: 7 chars

Storage:

500M × 365

≈ 182 Billion URLs/year

Storage needed:

Multi TB yearly storage

Peak Traffic:

Read heavy workload

100:1

Read : Write ratio

---

## API Design

### Create Short URL

```http
POST /shorten
```

Request:

```json
{
 "longUrl":"https://example.com/article"
}
```

Response:

```json
{
 "shortUrl":"abc123X"
}
```

### Redirect URL

```http
GET /abc123X
```

### Analytics API

```http
GET /analytics/{shortCode}
```

---

## Database Design

### URL Table

| Field | Type |
|--------|-------|
| short_code | String |
| original_url | String |
| created_at | Timestamp |
| expires_at | Timestamp |
| user_id | UUID |

### Analytics Table

| Field | Type |
|--------|-------|
| short_code | String |
| click_count | Integer |
| country | String |
| timestamp | Timestamp |

---

## URL Generation Strategy

### Base62 Encoding

Characters:

```text
[a-z][A-Z][0-9]
```

Example:

```text
125 -> cb
99999 -> q0T
```

Benefits:

- Small URL size
- Human readable

### Unique ID Generator

Options:

- Counter + Base62
- UUID Hash
- Snowflake ID

Preferred:

Snowflake + Base62

---

## High Level Design

```text
Client
 |
Load Balancer
 |
API Gateway
 |
Short URL Service
 |
Redis Cache
 |
Primary Database
 |
Kafka
 |
Analytics Pipeline
```

---

## Redirect Flow

```text
User Click
 ↓
Redis Lookup
 ↓
DB Fallback
 ↓
Get Original URL
 ↓
302 Redirect
 ↓
Analytics Event
```

---

## Core Components

### Cache Layer

Redis:

Responsibilities:

- Hot URL cache
- Faster redirect

### Analytics Pipeline

Kafka:

Responsibilities:

- Click tracking
- Async analytics

### Abuse Detection

Responsibilities:

- Spam URL detection
- Malware blocking
- Rate limiting

---

## Scaling Strategy

### Database

- Sharding
- Read replica

### Cache

Redis:

- Hot URL cache

### Queue

Kafka:

- Analytics event processing

---

## Reliability

Strategies:

- Retry mechanism
- Replication
- Dead letter queue
- Multi region deployment

---

## Bottlenecks

| Problem | Solution |
|----------|-----------|
| Redirect traffic spike | Redis cache |
| Analytics overload | Kafka buffering |
| Hot URL traffic | Cache scaling |
| Database contention | Sharding |

---

## Tradeoffs

| Choice | Benefit | Drawback |
|---------|----------|-----------|
| Counter + Base62 | Simple | Predictable IDs |
| UUID Hash | Better uniqueness | Longer URL |
| Cache heavy design | Faster redirect | Cache invalidation |

---

## Interview Questions

1. Why Base62 used?
2. Counter vs UUID vs Snowflake?
3. Why Redis useful?
4. Why analytics async?
5. How hot URL traffic handled?
6. Why redirect uses cache first?

---

## Quick Revision

- Base62 reduces URL length
- Redis improves redirect latency
- Kafka handles analytics pipeline
- Snowflake improves ID generation
- Cache first improves performance
- Sharding improves scalability