# Twitter System Design

## Problem Statement

Design a Twitter-like social media platform.

Features:

- Post Tweet
- Follow User
- Like Tweet
- Retweet
- Timeline Feed
- Search Tweet

Examples:

- Twitter (X)
- Threads

---

## Functional Requirements

System should support:

1. Create Tweet

2. View Timeline

3. Follow User

4. Like Tweet

5. Retweet

6. Search Tweet

---

## Non Functional Requirements

- High Availability
- Scalability
- Low Latency
- Fault Tolerance
- High Throughput

Interview Tip:

Twitter interview mainly tests:

```text
Feed Generation
+
Scalability
```

---

## Capacity Estimation

Assume:

```text
300 Million Daily Active Users
```

Assume:

```text
200 Million Tweets / Day
```

Interview Tip:

Twitter system is:

```text
Read Heavy
```

Timeline reads are huge.

---

## API Design

Create Tweet:

```text
POST /tweet/create
```

Get Timeline:

```text
GET /timeline/{userId}
```

Follow User:

```text
POST /follow
```

Like Tweet:

```text
POST /tweet/like
```

---

## Database Design

User Table:

| UserId | Name |
|---------|------|
| U101 | Roy |

Tweet Table:

| TweetId | UserId | Content |
|----------|--------|----------|
| T101 | U101 | Hello |

Follow Table:

| UserId | FollowUserId |
|---------|---------------|
| U101 | U102 |

Database:

SQL:

- PostgreSQL

NoSQL:

- Cassandra

Interview Tip:

Timeline systems usually need:

```text
High Read Throughput
```

---

## High Level Design

```text
Mobile Client

↓

Load Balancer

↓

API Gateway

↓

Tweet Service

↓

Kafka

↓

Feed Service

↓

Redis

↓

Database
```

---

## Feed Generation

Most important interview topic.

### Fan Out On Write

New Tweet:

```text
Create Tweet

↓

Push To Followers Feed
```

Benefits:

- Faster reads

Problem:

Celebrity users.

Example:

```text
100 Million Followers
```

Heavy write pressure.

---

### Fan Out On Read

Flow:

```text
Open Timeline

↓

Fetch Tweets

↓

Generate Feed
```

Benefits:

- Lower write overhead

Problem:

Slower reads.

---

## Push vs Pull

| Feature | Push | Pull |
|----------|------|------|
| Read Speed | Faster | Slower |
| Write Cost | Higher | Lower |
| Celebrity Issue | Yes | Better |

Interview Tip:

Production systems use:

```text
Hybrid Model
```

---

## Cache Strategy

Use:

```text
Redis
```

Cache:

- User Timeline
- Tweet Data
- User Profile

Benefits:

- Lower latency
- Reduced database load
- Faster timeline loading

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
- Cache miss spike

Solutions:

- Redis
- Kafka
- Sharding
- Hybrid Feed Model

---

## Interview Questions

### Q1. Biggest Twitter challenge?

Feed generation.

---

### Q2. Fan Out On Write vs Fan Out On Read?

Write:

Fast reads.

Read:

Lower write cost.

---

### Q3. Why Redis used?

Reduce database load.

---

## Quick Revision

- Twitter → Read heavy
- Redis → Timeline cache
- Kafka → Async processing
- Fan Out On Write → Fast read
- Fan Out On Read → Lower write cost
- Hybrid → Production approach