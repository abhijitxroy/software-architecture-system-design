

# Ecommerce System Design

## Problem Statement

Design an ecommerce platform like Amazon or Flipkart that supports product discovery, cart management, inventory handling, checkout and order processing at massive scale.

System should support:

- Product Search
- Product Catalog
- Cart Management
- Inventory Tracking
- Checkout Flow
- Payment Processing
- Order Management
- Recommendation System

---

## Functional Requirements

### Core Features

- Search products
- Browse catalog
- Add to cart
- Checkout order
- Payment processing
- Inventory management
- Order history
- Product recommendation

---

## Non Functional Requirements

### Scalability

- Millions of users
- Peak sale traffic handling

### Availability

- 99.99% uptime

### Reliability

- No order loss

### Latency

- Fast product search
- Low checkout latency

---

## Capacity Estimation

Assume:

- 100 Million DAU
- 20 Million orders/day
- 500 Million products

Storage:

Catalog + Inventory + Orders + Analytics

Petabyte scale storage

Peak Traffic:

- Festival sale spike

---

## API Design

### Product Search

```http
GET /products?query=iphone
```

### Add To Cart

```http
POST /cart
```

Request:

```json
{
 "userId":"u123",
 "productId":"p100",
 "quantity":1
}
```

### Checkout

```http
POST /checkout
```

---

## Database Design

### Product Table

| Field | Type |
|--------|-------|
| product_id | UUID |
| name | String |
| price | Decimal |
| stock | Integer |
| metadata | JSON |

### Order Table

| Field | Type |
|--------|-------|
| order_id | UUID |
| customer_id | UUID |
| amount | Decimal |
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
Product Service
 |
Cart Service
 |
Inventory Service
 |
Order Service
 |
Payment Service
 |
Kafka
 |
Notification Service
 |
Redis Cache
 |
Database
```

---

## Core Components

### Product Service

Responsibilities:

- Product catalog
- Search retrieval
- Product metadata

### Inventory Service

Responsibilities:

- Stock tracking
- Inventory reservation
- Prevent overselling

### Cart Service

Responsibilities:

- Add item
- Remove item
- Cart persistence

### Recommendation Service

Responsibilities:

- Similar products
- Personalized feed
- Trending items

---

## Checkout Flow

```text
Browse Product
 ↓
Add To Cart
 ↓
Checkout
 ↓
Payment
 ↓
Inventory Update
 ↓
Order Confirmation
```

---

## Scaling Strategy

### Database

- Read replica
- Sharding
- Partitioning

### Cache

Redis:

- Product cache
- Cart cache

### Queue

Kafka:

- Order processing
- Notification processing
- Analytics event

---

## Reliability

Strategies:

- Retry mechanism
- Idempotency
- Dead letter queue
- Multi region deployment

---

## Bottlenecks

| Problem | Solution |
|----------|-----------|
| Sale traffic spike | Horizontal scaling |
| Inventory contention | Inventory reservation |
| Search latency | Redis cache |
| Order burst | Kafka buffering |

---

## Tradeoffs

| Choice | Benefit | Drawback |
|---------|----------|-----------|
| Aggressive cache | Faster response | Stale inventory |
| Inventory locking | Prevent oversell | Lower throughput |

---

## Interview Questions

1. How inventory consistency maintained?
2. How overselling prevented?
3. Why Kafka useful?
4. How sale spikes handled?
5. Why Redis used?
6. How recommendation scales?

---

## Quick Revision

- Redis improves latency
- Kafka handles order events
- Inventory reservation prevents overselling
- Recommendation improves engagement
- Sharding improves scalability
- Idempotency prevents duplicate orders