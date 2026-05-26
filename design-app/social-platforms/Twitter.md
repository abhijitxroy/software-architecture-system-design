# Twitter System Design

## What is Twitter System?

Twitter (X) is a large scale social platform that allows users to publish short messages, follow users and consume real time content.

Twitter system design focuses heavily on feed generation, scalability, cache strategy and distributed systems.

Twitter architecture is commonly used in system design interviews because it combines:

- Feed generation
- Real time updates
- Distributed cache
- Event driven systems
- Large scale storage
- High read throughput

---

## Functional Requirements

System should support:

- Post Tweet
- Delete Tweet
- Follow User
- Unfollow User
- Like Tweet
- Retweet
- View Timeline
- Search Tweet

---

## Non Functional Requirements

Requirements:

- High Availability
- Scalability
- Low Latency
- Fault Tolerance
- Reliability
- High Throughput

Twitter is primarily:

```text
Read Heavy System
```

Timeline generation dominates traffic.

---

## Capacity Estimation

Assumptions:

```text
300 Million DAU
200 Million Tweets Per Day
Timeline Reads >> Tweet Writes
```

Design implications:

- Cache required
- Async processing required
- Distributed storage required

---

## High Level Architecture

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
Redis Cache
      ↓
Database
```

---

## Core Components

### Tweet Service

Responsibilities:

- Create tweet
- Delete tweet
- Store metadata

---

### User Graph Service

Stores:

```text
Follower Relationship
Following Relationship
```

Example:

```text
User A → User B
```

---

### Feed Service

Responsible for timeline generation.

Responsibilities:

- Feed ranking
- Timeline generation
- Tweet aggregation

---

### Cache Layer

Examples:

- Redis

Cache stores:

- Timeline cache
- User profile
- Tweet metadata

Benefits:

- Lower latency
- Reduced database load

---

## Feed Generation Strategies

### Fan Out On Write

Flow:

```text
Create Tweet
    ↓
Push To Followers
    ↓
Timeline Updated
```

Advantages:

- Faster reads

Problems:

- Celebrity user problem

Example:

```text
100 Million Followers
```

---

### Fan Out On Read

Flow:

```text
Open Timeline
      ↓
Generate Feed
      ↓
Return Tweets
```

Advantages:

- Lower write pressure

Problems:

- Higher read latency

---

### Hybrid Model

Production systems commonly use:

```text
Normal User → Fan Out On Write
Celebrity User → Fan Out On Read
```

Benefits:

- Better scalability

---

## Database Design

Tweet Table:

| TweetId | UserId | Content |
|----------|---------|----------|
| T1001 | U123 | Hello |

Follower Table:

| UserId | FollowingId |
|---------|-------------|
| U123 | U456 |

Storage examples:

SQL:

- PostgreSQL

NoSQL:

- Cassandra

---

## Scaling Strategy

Application:

- Horizontal scaling
- Load balancing

Database:

- Sharding
- Replication

Messaging:

- Kafka

Cache:

- Redis Cluster

---

## Production Challenges

Common issues:

- Celebrity user problem
- Cache invalidation
- Feed latency
- Timeline scaling
- Database hotspot

Solutions:

- Hybrid feed generation
- Distributed cache
- Queue systems
- Sharding
- Async processing

---

## Interview Questions

1. Fan Out On Write vs Fan Out On Read?

2. Why Twitter is read heavy?

3. Celebrity user problem?

4. Why Redis improves timeline performance?

5. How feed generation scales?

6. Twitter production bottlenecks?

---

## Quick Revision

- Twitter is read heavy
- Redis improves feed latency
- Kafka enables async processing
- Hybrid feed model improves scaling
- Cache reduces database pressure
- Timeline generation drives architecture
- Distributed systems improve scalability