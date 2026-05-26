

# Airbnb System Design

## Problem Statement

Design a property booking platform like Airbnb.

Features:

- Property Listing
- Search Property
- Book Property
- Payment
- Review System
- Availability Tracking

Examples:

- Airbnb
- Booking.com

---

## Functional Requirements

System should support:

1. Property Listing

2. Property Search

3. Booking Property

4. Payment Processing

5. User Review

6. Availability Calendar

7. Cancellation

---

## Non Functional Requirements

- High Availability
- Scalability
- Reliability
- Low Latency
- Fault Tolerance

Interview Tip:

Airbnb interviews focus heavily on:

```text
Search System
+ 
Booking Consistency
```

---

## Capacity Estimation

Assume:

```text
100 Million Users
```

Assume:

```text
10 Million Property Listings
```

Traffic Type:

```text
Read Heavy System
```

Reason:

Users search much more than booking.

---

## API Design

Search Property:

```text
GET /property/search
```

Book Property:

```text
POST /booking/create
```

Property Details:

```text
GET /property/{id}
```

---

## Database Design

User Table:

| UserId | Name |
|--------|------|
| U101 | Roy |

Property Table:

| PropertyId | HostId | City |
|------------|--------|------|
| P101 | H101 | Bangalore |

Booking Table:

| BookingId | UserId | PropertyId |
|------------|--------|------------|
| B101 | U101 | P101 |

Common Databases:

- PostgreSQL
- MySQL

Search Engine:

- Elasticsearch

---

## High Level Design

```text
Client

↓

Load Balancer

↓

API Service

↓

Search Service

↓

Booking Service

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

## Search System

Interview Focus Topic.

Search Filters:

- Location
- Price
- Rating
- Date

Common Solution:

```text
Elasticsearch
```

Reason:

Fast filtering.

---

## Booking Consistency

Interview Focus Topic.

Problem:

```text
Same Room

Booked By Two Users
```

Solution:

- Database Transaction
- Distributed Lock

Goal:

```text
Prevent Double Booking
```

---

## Cache Strategy

Use:

```text
Redis
```

Cache:

- Property Details
- Search Result
- Popular Listing

Benefits:

- Faster response
- Lower database load

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

- Search traffic spike
- Booking conflict
- Database hotspot

Solutions:

- Redis
- Elasticsearch
- Read Replica

---

## Interview Questions

### Q1. Biggest Airbnb challenge?

Search and booking consistency.

---

### Q2. Why Elasticsearch used?

Fast search filtering.

---

### Q3. How prevent double booking?

Transaction and locking.

---

## Quick Revision

- Airbnb → Read heavy
- Elasticsearch → Search system
- Redis → Cache
- Kafka → Async processing
- Locking → Prevent double booking
- Read Replica → Scale database