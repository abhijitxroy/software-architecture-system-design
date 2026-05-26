

# YouTube System Design

## Problem Statement

Design a video streaming platform like YouTube that supports video upload, video processing, streaming, recommendation and large scale content delivery.

System should support:

- Video Upload
- Video Streaming
- Recommendation System
- Search Video
- Like and Comment
- Subscription
- Notification
- Analytics

---

## Functional Requirements

### Core Features

- Upload video
- Stream video
- Search content
- Subscribe channel
- Like and comment
- Video recommendation
- Playback history
- Notification delivery

---

## Non Functional Requirements

### Scalability

- Billions of users
- Millions of video uploads/day

### Availability

- 99.99% uptime

### Reliability

- No playback interruption

### Latency

- Fast video startup

---

## Capacity Estimation

Assume:

- 2 Billion monthly users
- 100 Million uploads/day
- Average video size: 200 MB

Storage:

Video files + metadata + analytics

Petabyte scale storage

Bandwidth:

Extremely high CDN bandwidth

---

## API Design

### Upload Video

```http
POST /videos
```

### Stream Video

```http
GET /videos/{videoId}
```

### Subscribe Channel

```http
POST /subscribe
```

---

## Database Design

### Video Table

| Field | Type |
|--------|-------|
| video_id | UUID |
| channel_id | UUID |
| title | String |
| duration | Integer |
| metadata | JSON |

### User Activity Table

| Field | Type |
|--------|-------|
| user_id | UUID |
| video_id | UUID |
| watch_time | Integer |
| timestamp | Timestamp |

---

## High Level Design

```text
Client
 |
Load Balancer
 |
API Gateway
 |
Upload Service
 |
Metadata Service
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

Kafka
 |
Analytics Pipeline
```

---

## Core Components

### Upload Service

Responsibilities:

- Upload video
- Validate content
- Store metadata

### Video Processing Service

Responsibilities:

- Video transcoding
- Resolution generation
- Thumbnail generation

Formats:

- 480P
- 720P
- 1080P
- 4K

### CDN

Responsibilities:

- Reduce playback latency
- Global content delivery
- Reduce origin load

### Recommendation System

Responsibilities:

- Personalized recommendation
- Similar video ranking
- Trending content

Signals:

- Watch history
- Search history
- User engagement

### Analytics Pipeline

Responsibilities:

- Playback analytics
- Engagement metrics
- Recommendation feedback

---

## Video Upload Flow

```text
Upload Video
 ↓
Metadata Validation
 ↓
Video Processing
 ↓
Storage
 ↓
CDN Distribution
 ↓
Available To Stream
```

---

## Playback Flow

```text
Open App
 ↓
Fetch Metadata
 ↓
Recommendation
 ↓
CDN Fetch
 ↓
Play Video
 ↓
Analytics Event
```

---

## Scaling Strategy

### Cache

Redis:

- Metadata cache
- Recommendation cache

### Queue

Kafka:

- Playback analytics
- Processing pipeline

### Database

- Read replica
- Sharding

---

## Reliability

Strategies:

- Multi CDN deployment
- Retry mechanism
- Replication
- Multi region deployment

---

## Bottlenecks

| Problem | Solution |
|----------|-----------|
| Upload spike | Queue buffering |
| Playback traffic | CDN scaling |
| Metadata load | Redis cache |
| Analytics traffic | Kafka buffering |

---

## Tradeoffs

| Choice | Benefit | Drawback |
|---------|----------|-----------|
| Aggressive cache | Faster playback | Stale metadata |
| Multiple CDN | Better availability | Higher cost |

---

## Interview Questions

1. Why CDN needed?
2. Why transcoding required?
3. How recommendation system works?
4. Why Kafka useful?
5. How upload pipeline scales?
6. How playback latency reduced?

---

## Quick Revision

- CDN reduces latency
- Kafka handles analytics pipeline
- Recommendation improves engagement
- Transcoding improves playback quality
- Redis improves metadata lookup
- Sharding improves scalability