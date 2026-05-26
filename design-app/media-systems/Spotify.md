

# Spotify System Design

## Problem Statement

Design a music streaming platform like Spotify that supports music streaming, playlist management, recommendation systems and large scale audio delivery.

System should support:

- Music Streaming
- Playlist Management
- Search Music
- Recommendation System
- Download Offline Music
- Artist Management
- User Library
- Podcast Streaming

---

## Functional Requirements

### Core Features

- Play music
- Pause music
- Create playlist
- Search songs
- Follow artists
- Download offline music
- Personalized recommendation
- Podcast streaming

---

## Non Functional Requirements

### Scalability

- Millions of concurrent users
- Global traffic distribution

### Availability

- 99.99% uptime

### Reliability

- No playback interruption

### Latency

- Audio playback starts quickly

---

## Capacity Estimation

Assume:

- 600 Million users
- 200 Million DAU
- 100 Million songs
- 2 Billion streams/day

Storage:

Music metadata + audio files + analytics

Petabyte scale storage

Bandwidth:

Massive CDN bandwidth requirement

---

## API Design

### Play Song

```http
GET /songs/{songId}/play
```

### Create Playlist

```http
POST /playlist
```

Request:

```json
{
 "userId":"u123",
 "playlist":"Workout Mix"
}
```

### Search Song

```http
GET /search?q=coldplay
```

---

## Database Design

### Song Table

| Field | Type |
|--------|-------|
| song_id | UUID |
| artist_id | UUID |
| title | String |
| duration | Integer |
| metadata | JSON |

### Playlist Table

| Field | Type |
|--------|-------|
| playlist_id | UUID |
| owner_id | UUID |
| song_ids | Array |
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
Music Service
 |
Playlist Service
 |
Recommendation Service
 |
Redis Cache
 |
Metadata Database
 |
CDN
 |
Audio Storage

Kafka
 |
Analytics Pipeline
```

---

## Core Components

### Music Service

Responsibilities:

- Audio playback
- Song metadata retrieval
- Playback management

### Recommendation System

Responsibilities:

- Personalized recommendation
- Similar song ranking
- Trending music

Signals:

- Listening history
- User preference
- Playlist behavior

### CDN

Responsibilities:

- Global audio delivery
- Reduce playback latency
- Reduce origin traffic

### Analytics Pipeline

Responsibilities:

- Playback analytics
- User engagement
- Recommendation feedback

---

## Playback Flow

```text
Open App
 ↓
Search Song
 ↓
Metadata Lookup
 ↓
CDN Audio Fetch
 ↓
Play Audio
 ↓
Analytics Event
```

---

## Scaling Strategy

### Cache

Redis:

- Metadata cache
- Playlist cache

### Database

- Read replica
- Sharding

### Queue

Kafka:

- Playback event processing
- Recommendation analytics

---

## Reliability

Strategies:

- CDN replication
- Retry mechanism
- Multi region deployment
- Cache fallback

---

## Bottlenecks

| Problem | Solution |
|----------|-----------|
| Playback spike | CDN scaling |
| Metadata load | Redis cache |
| Analytics traffic | Kafka buffering |
| Recommendation latency | Cache ranking |

---

## Tradeoffs

| Choice | Benefit | Drawback |
|---------|----------|-----------|
| Aggressive cache | Faster playback | Stale metadata |
| Offline download | Better UX | Higher storage |

---

## Interview Questions

1. Why CDN needed?
2. How recommendation system works?
3. Why Kafka useful?
4. How playback scales globally?
5. Why Redis useful?
6. How offline download works?

---

## Quick Revision

- CDN reduces playback latency
- Redis improves metadata lookup
- Kafka handles analytics events
- Recommendation improves engagement
- Sharding improves scalability
- Cache improves performance