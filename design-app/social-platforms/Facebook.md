# Facebook System Design

## Problem Statement

Design a social media platform like Facebook.

Features:

- Create Post
- Like Post
- Comment Post
- Friend Request
- News Feed
- Notification
- Photo Upload
- Search User

Examples:

- Facebook
- LinkedIn

---

## Clarifying Questions

Interview starts here.

Questions:

1. Core feature only or complete platform?

2. Number of active users?

3. Read heavy or write heavy?

4. Feed generation needed?

5. Photo and video upload needed?

Interview Tip:

Always ask questions before design.

---

## Functional Requirements

System should support:

1. Create Post

2. Friend Request

3. News Feed

4. Like and Comment

5. Notification

6. Search User

7. Media Upload

---

## Non Functional Requirements

- High Availability
- Scalability
- Reliability
- Low Latency
- Fault Tolerance

Interview Focus:

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

Traffic Type:

```text
Read Heavy System
```

Reason:

Users read more than creating posts.

Estimate:

- Requests Per Second
- Storage Growth
- Feed Read Traffic

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

Add Friend:

```text
POST /friend/request
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

| PostId | UserId | Content |
|--------|--------|---------|
| P101 | U101 | Hello |

Friend Table:

| User1 | User2 |
|-------|-------|
| U101 | U201 |

Common Databases:

- PostgreSQL
- Cassandra

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

Database
```

Supporting Services:

```text
Redis

Kafka

Notification Service
```

---

## Feed Generation

Interview Focus Topic.

### Fan Out On Write

```text
Create Post

↓

Push Feed
```

Benefits:

- Faster reads

Problem:

Celebrity users.

---

### Fan Out On Read

```text
Open Feed

↓

Generate Feed
```

Benefits:

- Lower write pressure

Interview Tip:

Production systems commonly use:

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

- Feed Data
- User Profile
- Popular Post

Benefits:

- Lower latency
- Faster feed loading

---

## Scaling Strategy

Application:

- Horizontal Scaling
- Load Balancer

Database:

- Read Replica
- Sharding

Messaging:

- Kafka

---

## Bottleneck

Problems:

- Viral traffic spike
- Feed generation pressure
- Database hotspot

Solutions:

- Redis
- Kafka
- Cache Layer

---

## Interview Questions

### Q1. Biggest Facebook challenge?

Feed generation.

---

### Q2. Why Redis used?

Fast feed loading.

---

### Q3. Why Kafka used?

Async processing.

---

## Quick Revision

- Facebook → Read heavy
- Feed → Core feature
- Redis → Cache
- Kafka → Async processing
- Hybrid Feed → Production approach
- Sharding → Scale database


<!-- #social media app

Ask clarifying questions
-
    Is the interviewer looking for a design of the core features, or a high-level overview of the whole service?
    What are the constraints of the system?
    What are your assumptions? (traffic distribution, number of active users and tweets, read vs write-heavy)

Design high-level
-
    Back-of-the-envelope calculations: average KBs per tweet, size of new tweet content per month, read requests and tweets per second, etc.
    High-level components: write, read, and search APIs; types of databases; SQL vs NoSQL; etc

Drill down on your design
-
    Potential bottlenecks: adding a load balancer with multiple web servers, scalability issues, fanout service slowing down tweets and @replies, etc.
    Components that you could dive into: how a user views the home timeline or posts a tweet, the intricacies of the database design, etc.

Bring it all together
-
    Consider: does the final design address the bottlenecks you’ve identified? Does it meet the goals you discussed at the beginning of the interview? Do you have any questions for the interviewer?

Tutorial: https://www.youtube.com/watch?v=KmAyPUv9gOY&t=1s -->