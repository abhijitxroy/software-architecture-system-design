
# Reddit System Design

## Problem Statement

Design a social discussion platform like Reddit.

Features:

- Create Post
- Upvote
- Downvote
- Comment
- Community Creation
- Feed Generation
- Search Post

Examples:

- Reddit
- Quora

---

## Functional Requirements

System should support:

1. Create Post

2. Create Community

3. Upvote Post

4. Downvote Post

5. Comment Post

6. Search Post

7. Personalized Feed

---

## Non Functional Requirements

- High Availability
- Low Latency
- Scalability
- Reliability
- Fault Tolerance

Interview Tip:

Reddit interviews focus heavily on:

```text
Feed Generation
+
Ranking System
```

---

## Capacity Estimation

Assume:

```text
100 Million Daily Active Users
```

Traffic Type:

```text
Read Heavy System
```

Reason:

Users consume more posts than creating.

---

## API Design

Create Post:

```text
POST /post/create
```

Get Feed:

```text
GET /feed
```

Vote:

```text
POST /vote
```

Comment:

```text
POST /comment
```

---

## Database Design

User Table:

| UserId | Name |
|--------|------|
| U101 | Roy |

Post Table:

| PostId | UserId | Title |
|--------|--------|-------|
| P101 | U101 | System Design |

Vote Table:

| VoteId | UserId | PostId | Type |
|---------|--------|--------|------|
| V101 | U201 | P101 | Upvote |

Community Table:

| CommunityId | Name |
|-------------|------|
| C101 | Backend |

---

## High Level Design

```text
Client

↓

Load Balancer

↓

API Service

↓

Feed Service

↓

Ranking Service

↓

Database
```

Supporting Services:

```text
Redis

Kafka

Search Service
```

---

## Ranking System

Interview Focus Topic.

Goal:

```text
Best Content First
```

Factors:

- Upvotes
- Comments
- Recency
- Engagement

Example:

```text
Score

=

Votes + Activity + Time
```

---

## Feed Generation

Feed Types:

- Community Feed
- Home Feed
- Trending Feed

Interview Tip:

Production systems commonly use:

```text
Hybrid Feed Model
```

---

## Cache Strategy

Use:

```text
Redis
```

Cache:

- Feed Data
- Popular Post
- Community Data

Benefits:

- Lower latency
- Reduced database load

---

## Scaling Strategy

Application:

- Horizontal Scaling

Database:

- Sharding
- Read Replica

Messaging:

- Kafka

---

## Bottleneck

Problems:

- Feed generation pressure
- Viral post traffic
- Ranking calculation load

Solutions:

- Redis
- Kafka
- Cache Layer

---

## Interview Questions

### Q1. Biggest Reddit challenge?

Feed ranking.

---

### Q2. Why Redis used?

Fast feed retrieval.

---

### Q3. Why Kafka used?

Async processing.

---

## Quick Revision

- Reddit → Read heavy
- Ranking → Core problem
- Feed → Main feature
- Redis → Feed cache
- Kafka → Async processing
- Sharding → Scale database
