# LinkedIn System Design

## Problem Statement

Design a professional networking platform like LinkedIn that supports user profiles, connections, feeds, messaging, job discovery and content engagement at massive scale.

System should support:

- User Profile
- Connection System
- News Feed
- Job Platform
- Messaging
- Post Creation
- Notification
- Search People

---

## Functional Requirements

### Core Features

- Create profile
- Connect with users
- Create post
- Like and comment
- Search people
- Job recommendation
- Send message
- Notification delivery

---

## Non Functional Requirements

### Scalability

- Hundreds of millions of users
- Millions of posts/day

### Availability

- 99.99% uptime

### Reliability

- No profile or post loss

### Latency

- Fast feed loading
- Fast search response

---

## Capacity Estimation

Assume:

- 1 Billion users
- 50 Million DAU
- 100 Million posts/day
- 500 Million feed requests/day

Storage:

Profiles + Posts + Feed + Messages + Analytics

Petabyte scale storage

Peak Traffic:

Read heavy workload

---

## API Design

### Create Post

```http
POST /posts
```

Request:

```json
{
 "userId":"u123",
 "content":"Excited to share my new project"
}
```

### Get Feed

```http
GET /feed
```

### Send Connection Request

```http
POST /connections
```

---

## Database Design

### User Table

| Field | Type |
|--------|-------|
| user_id | UUID |
| name | String |
| headline | String |
| location | String |

### Post Table

| Field | Type |
|--------|-------|
| post_id | UUID |
| author_id | UUID |
| content | Blob |
| created_at | Timestamp |

### Connection Table

| Field | Type |
|--------|-------|
| user_id | UUID |
| connection_id | UUID |
| status | String |

---

## High Level Design

```text
Client
 |
Load Balancer
 |
API Gateway
 |
Profile Service
 |
Connection Service
 |
Feed Service
 |
Messaging Service
 |
Search Service
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

## Core Components

### Feed Service

Responsibilities:

- Feed generation
- Ranking posts
- Content retrieval

Feed Approaches:

- Fan Out On Write
- Fan Out On Read

### Search Service

Responsibilities:

- Search people
- Search company
- Search jobs

Optimization:

- Inverted Index
- Elasticsearch style search

### Recommendation Service

Responsibilities:

- Suggested connection
- Job recommendation
- Content recommendation

Signals:

- User activity
- Profile similarity
- Engagement history

### Messaging Service

Responsibilities:

- Chat delivery
- Notification generation
- Message persistence

---

## Feed Flow

```text
User Creates Post
 ↓
Kafka Event
 ↓
Feed Processing
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
- Profile cache

### Queue

Kafka:

- Feed event processing
- Notification event processing

### Database

- Sharding
- Read replica

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
| Feed traffic spike | Redis cache |
| Feed generation load | Kafka pipeline |
| Search latency | Index optimization |
| Connection graph growth | Graph optimization |

---

## Tradeoffs

| Choice | Benefit | Drawback |
|---------|----------|-----------|
| Fan Out On Write | Faster feed read | Expensive write |
| Fan Out On Read | Cheaper write | Slower feed load |

---

## Interview Questions

1. Fan Out On Write vs Fan Out On Read?
2. How feed ranking works?
3. How connection recommendation works?
4. Why Kafka useful?
5. How search scales?
6. How LinkedIn feed handles massive traffic?

---

## Quick Revision

- Feed generation is core challenge
- Kafka handles feed events
- Redis improves feed latency
- Recommendation improves engagement
- Search needs indexing
- Sharding improves scalability