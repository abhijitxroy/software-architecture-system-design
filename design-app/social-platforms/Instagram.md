# Instagram System Design

## Problem Statement

Design a social media platform like Instagram.

Features:

- Upload Photo
- Upload Video
- Feed Generation
- Like Post
- Comment
- Follow User
- Notification

Examples:

- Instagram
- Threads

---

## Functional Requirements

System should support:

1. Upload Post

2. View Feed

3. Follow User

4. Like Post

5. Comment Post

6. Notification

7. User Profile

---

## Non Functional Requirements

- High Availability
- Low Latency
- Scalability
- Reliability
- High Read Throughput

Interview Tip:

Instagram interviews focus heavily on:

```text
Feed Generation
+
Scalability
```

---

## Capacity Estimation

Assume:

```text
500 Million Daily Active Users
```

Assume:

```text
100 Feed Requests / User / Day
```

System becomes:

```text
Read Heavy System
```

---

## API Design

Upload Post:

```text
POST /post/upload
```

Get Feed:

```text
GET /feed
```

Follow User:

```text
POST /follow
```

Like Post:

```text
POST /post/like
```

---

## Database Design

User Table:

| UserId | Name |
|--------|------|
| U101 | Roy |

Post Table:

| PostId | UserId | MediaUrl |
|--------|--------|----------|
| P101 | U101 | img.jpg |

Follower Table:

| UserId | FollowerId |
|--------|------------|
| U101 | U201 |

Common Databases:

- PostgreSQL
- Cassandra

---

## High Level Design

```text
Mobile Client

↓

Load Balancer

↓

API Service

↓

Feed Service

↓

Redis

↓

Database
```

Supporting Services:

```text
Notification Service

Kafka

Media Storage
```

---

## Feed Generation

Interview Focus Topic.

Two approaches:

### Fan Out On Write

Flow:

```text
Create Post

↓

Push Feed To Followers
```

Benefits:

- Fast feed loading

Problem:

Celebrity users.

---

### Fan Out On Read

Flow:

```text
Open Feed

↓

Generate Feed Runtime
```

Benefits:

- Lower write load

Problem:

Slower reads.

Interview Tip:

Production systems often use:

```text
Hybrid Model
```

---

## Media Storage

Store media outside database.

Examples:

- S3
- CDN

Benefits:

- Better scalability
- Lower database pressure

---

## Cache Strategy

Use:

```text
Redis
```

Cache:

- Feed Data
- User Profile
- Popular Post

Benefits:

- Faster feed loading
- Reduced database load

---

## Scaling Strategy

Application:

- Horizontal Scaling
- Load Balancer

Database:

- Sharding
- Replication

Messaging:

- Kafka

---

## Bottleneck

Problems:

- Celebrity users
- Feed generation pressure
- Media upload spike

Solutions:

- Redis
- CDN
- Kafka
- Sharding

---

## Interview Questions

### Q1. Biggest Instagram challenge?

Feed generation.

---

### Q2. Fan Out On Write vs Read?

Write:

Fast feed.

Read:

Lower write load.

---

### Q3. Why Redis used?

Reduce database load.

---

### Q4. Why CDN needed?

Fast media delivery.

---

## Quick Revision

- Instagram → Read heavy
- Redis → Feed cache
- Kafka → Async processing
- CDN → Media delivery
- Fan Out → Feed generation
- Hybrid → Production approach