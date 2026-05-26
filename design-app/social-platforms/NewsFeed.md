# News Feed System Design

## Problem Statement

Design a news feed system like Facebook, Instagram or LinkedIn feed that supports feed generation, ranking and large scale content distribution.

System should support:

- Feed Generation
- Post Creation
- Like and Comment
- Ranking System
- Content Recommendation
- Media Upload
- Notification
- Infinite Scrolling

---

## Functional Requirements

### Core Features

- Create post
- View feed
- Like content
- Comment content
- Share post
- Follow users
- Personalized ranking
- Notification delivery

---

## Non Functional Requirements

### Scalability

- Billions of feed requests/day
- Millions of posts/day

### Availability

- 99.99% uptime

### Reliability

- No feed data loss

### Latency

- Feed loading under 200 ms

---

## Capacity Estimation

Assume:

- 500 Million DAU
- 200 Million posts/day
- 5 Billion feed requests/day

Storage:

Posts + Media + Feed Cache + Analytics

Petabyte scale storage

Peak Traffic:

Read heavy workload

Read : Write

100 : 1

---

## API Design

### Create Post

```http
POST /posts
```

### Get Feed

```http
GET /feed
```

### Like Post

```http
POST /likes
```

---

## Database Design

### Post Table

| Field | Type |
|--------|-------|
| post_id | UUID |
| author_id | UUID |
| content | Blob |
| created_at | Timestamp |

### Feed Table

| Field | Type |
|--------|-------|
| user_id | UUID |
| post_id | UUID |
| score | Double |
| created_at | Timestamp |

---

## High Level Design

```text
Client
 |
Load Balancer
 |
API Gateway
 |
Post Service
 |
Feed Service
 |
Ranking Service
 |
Recommendation Service
 |
Redis Cache
 |
Kafka
 |
Database
 |
Analytics Pipeline
```

---

## Feed Generation Strategy

### Fan Out On Write

Flow:

```text
Create Post
 ↓
Push Feed Update
 ↓
Follower Feed Cache
```

Benefits:

- Faster feed read

Drawback:

- Expensive write

### Fan Out On Read

Flow:

```text
Read Feed
 ↓
Build Feed Dynamically
```

Benefits:

- Cheaper write

Drawback:

- Higher read latency

---

## Ranking System

Signals:

- Engagement
- User affinity
- Freshness
- Watch history
- Like history

Example Score:

Ranking Score =

Engagement + Affinity + Recency

---

## Feed Flow

```text
User Creates Post
 ↓
Kafka Event
 ↓
Feed Generation
 ↓
Ranking
 ↓
Redis Cache
 ↓
Feed Delivery
```

---

## Scaling Strategy

### Cache

Redis:

- Feed cache
- Ranking cache

### Queue

Kafka:

- Feed events
- Analytics events

### Database

- Sharding
- Read replica

---

## Reliability

Strategies:

- Retry mechanism
- Dead letter queue
- Replication
- Multi region deployment

---

## Bottlenecks

| Problem | Solution |
|----------|-----------|
| Feed spike | Redis cache |
| Ranking latency | Cache ranking |
| Feed generation load | Kafka pipeline |
| Database contention | Sharding |

---

## Tradeoffs

| Choice | Benefit | Drawback |
|---------|----------|-----------|
| Fan Out On Write | Faster feed read | Expensive write |
| Fan Out On Read | Lower write cost | Higher read latency |

---

## Interview Questions

1. Fan Out On Write vs Fan Out On Read?
2. How feed ranking works?
3. Why Kafka useful?
4. Why Redis useful?
5. How feed scales?
6. How ranking optimized?

---

## Quick Revision

- Feed generation is core challenge
- Redis improves feed latency
- Kafka handles feed events
- Ranking improves engagement
- Fan out strategy impacts scalability
- Sharding improves database scale