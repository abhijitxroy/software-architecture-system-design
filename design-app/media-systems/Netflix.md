

# Netflix System Design

## Problem Statement

Design a video streaming platform like Netflix that supports video upload, content delivery, recommendation system and large scale streaming.

System should support:

- Video Streaming
- Content Upload
- Recommendation System
- Search Content
- Continue Watching
- Multi Device Playback
- Adaptive Streaming
- CDN Delivery

---

## Functional Requirements

### Core Features

- Stream video content
- Upload media content
- Search movies and shows
- Personalized recommendation
- Continue watching
- Playback history
- Multi device support
- Subtitle support

---

## Non Functional Requirements

### Scalability

- Millions of concurrent users
- Petabyte scale storage

### Availability

- 99.99% uptime

### Reliability

- No playback interruption

### Latency

- Video startup within seconds

---

## Capacity Estimation

Assume:

- 300 Million users
- 100 Million DAU
- Average video size: 5 GB
- 1 Billion playback/day

Storage:

Petabyte scale video storage

Bandwidth:

Extremely high CDN bandwidth requirement

---

## API Design

### Fetch Content

```http
GET /content/{contentId}
```

---

### Recommendation API

```http
GET /recommendations/{userId}
```

---

### Continue Watching

```http
GET /continueWatching/{userId}
```

---

## Database Design

### Content Table

| Field | Type |
|--------|-------|
| content_id | UUID |
| title | String |
| genre | String |
| duration | Integer |
| metadata | JSON |

### Watch History

| Field | Type |
|--------|-------|
| user_id | UUID |
| content_id | UUID |
| timestamp | Timestamp |
| progress | Integer |

---

## High Level Design

```text
Client
 |
Load Balancer
 |
API Gateway
 |
Content Service
 |
Recommendation Service
 |
Redis Cache
 |
Metadata Database
 |
CDN
 |
Video Storage

Playback Analytics
 |
Kafka
 |
Analytics Pipeline
```

---

## Core Components

### CDN

Responsibilities:

- Deliver content near user
- Reduce latency
- Reduce origin load

### Recommendation System

Responsibilities:

- Personalized feed
- Similar content suggestion
- Ranking content

Signals:

- Watch history
- Search history
- User preference

### Adaptive Bitrate Streaming

Responsibilities:

- Adjust video quality
- Prevent buffering

Examples:

- 480P
- 720P
- 1080P
- 4K

### Analytics Pipeline

Responsibilities:

- Playback analytics
- User engagement
- Recommendation feedback

---

## Scaling Strategy

### CDN

Improve:

- Latency
- Global delivery

### Cache

Redis:

- Metadata cache
- Recommendation cache

### Database

- Read replica
- Partitioning
- Sharding

---

## Reliability

Strategies:

- Multi CDN setup
- Retry mechanism
- Replication
- Multi region deployment

---

## Bottlenecks

| Problem | Solution |
|----------|-----------|
| Video traffic spike | CDN scaling |
| Recommendation latency | Redis cache |
| Metadata overload | Replica DB |
| Playback buffering | Adaptive streaming |

---

## Tradeoffs

| Choice | Benefit | Drawback |
|---------|----------|-----------|
| Aggressive cache | Faster playback | Stale metadata |
| Multiple CDN | Higher availability | Higher cost |

---

## Interview Questions

1. Why CDN needed?
2. Why adaptive streaming important?
3. How recommendation system works?
4. How playback scale handled?
5. Why cache metadata?
6. Why analytics useful?

---

## Quick Revision

- CDN reduces latency
- Redis improves response time
- Kafka enables analytics pipeline
- Adaptive streaming improves playback
- Recommendation system improves engagement
- Sharding improves scalability