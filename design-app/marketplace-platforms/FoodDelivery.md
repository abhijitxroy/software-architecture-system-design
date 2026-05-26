

# Food Delivery System Design

## Problem Statement

Design a food delivery platform like Swiggy, Zomato or Uber Eats that supports restaurant discovery, food ordering, driver assignment and real time order tracking.

System should support:

- Restaurant Search
- Food Ordering
- Driver Assignment
- Order Tracking
- ETA Prediction
- Payment Processing
- Notification
- Rating System

---

## Functional Requirements

### Core Features

- Search restaurants
- Browse menu
- Place order
- Track order live
- Driver assignment
- Payment processing
- Order history
- Restaurant rating

---

## Non Functional Requirements

### Scalability

- Millions of users
- Peak meal hour traffic

### Availability

- 99.99% uptime

### Reliability

- No order loss

### Latency

- Fast restaurant search
- Real time tracking updates

---

## Capacity Estimation

Assume:

- 20 Million DAU
- 10 Million orders/day
- Peak traffic lunch and dinner hours

Storage:

Orders + Menu + Tracking + Analytics

Multi TB yearly storage

---

## API Design

### Search Restaurant

```http
GET /restaurants?location=bangalore
```

### Place Order

```http
POST /orders
```

Request:

```json
{
 "restaurantId":"r123",
 "items":[101,102],
 "payment":"UPI"
}
```

### Track Order

```http
GET /orders/{orderId}
```

---

## Database Design

### Restaurant Table

| Field | Type |
|--------|-------|
| restaurant_id | UUID |
| name | String |
| location | Geo |
| rating | Decimal |

### Order Table

| Field | Type |
|--------|-------|
| order_id | UUID |
| customer_id | UUID |
| restaurant_id | UUID |
| driver_id | UUID |
| status | String |
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
Restaurant Service
 |
Order Service
 |
Driver Assignment Service
 |
Kafka
 |
Tracking Service
 |
Redis Cache
 |
Database
 |
Notification Service
```

---

## Core Components

### Restaurant Service

Responsibilities:

- Restaurant discovery
- Menu retrieval
- Rating retrieval

### Driver Assignment Service

Responsibilities:

- Find nearest driver
- ETA optimization
- Delivery allocation

Techniques:

- GeoHash
- Distance calculation

### Tracking Service

Responsibilities:

- Real time location tracking
- Delivery updates
- ETA updates

### Notification Service

Responsibilities:

- Order updates
- Delivery alerts
- Push notification

---

## Order Lifecycle

```text
PLACED
 ↓
RESTAURANT_ACCEPTED
 ↓
PREPARING
 ↓
PICKED_UP
 ↓
DELIVERED
```

---

## Scaling Strategy

### Database

- Sharding
- Read replica

### Cache

Redis:

- Restaurant cache
- Menu cache

### Queue

Kafka:

- Tracking event processing
- Notification processing

---

## Reliability

Strategies:

- Retry mechanism
- Driver reassignment
- Multi region deployment
- Dead letter queue

---

## Bottlenecks

| Problem | Solution |
|----------|-----------|
| Peak order traffic | Horizontal scaling |
| Driver shortage | Dynamic allocation |
| Tracking load | Kafka buffering |
| Restaurant search latency | Redis cache |

---

## Tradeoffs

| Choice | Benefit | Drawback |
|---------|----------|-----------|
| Aggressive cache | Faster search | Stale menu |
| Frequent GPS updates | Better ETA | Higher cost |

---

## Interview Questions

1. How driver assignment works?
2. Why GeoHash useful?
3. How ETA calculated?
4. How order spikes handled?
5. Why Kafka useful?
6. How live tracking scales?

---

## Quick Revision

- GeoHash improves nearby search
- Kafka handles tracking events
- Redis improves latency
- ETA improves delivery experience
- Driver allocation impacts scalability
- Queue improves reliability