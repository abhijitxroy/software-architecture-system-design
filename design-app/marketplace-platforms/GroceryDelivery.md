

# Grocery Delivery System Design

## Problem Statement

Design a grocery delivery platform like Instamart, Blinkit or Zepto that supports grocery discovery, inventory tracking, warehouse management and fast delivery.

System should support:

- Grocery Search
- Inventory Management
- Cart Management
- Warehouse Selection
- Order Placement
- Delivery Assignment
- ETA Prediction
- Real Time Tracking

---

## Functional Requirements

### Core Features

- Search grocery items
- Add products to cart
- Place order
- Inventory validation
- Warehouse assignment
- Delivery partner assignment
- Real time tracking
- Order history

---

## Non Functional Requirements

### Scalability

- Millions of users
- Peak traffic during evening hours

### Availability

- 99.99% uptime

### Reliability

- No order loss

### Latency

- Fast inventory lookup
- Real time tracking updates

---

## Capacity Estimation

Assume:

- 10 Million DAU
- 5 Million orders/day
- 500000 inventory items

Storage:

Inventory + Orders + Tracking + Analytics

Multi TB yearly storage

Peak Traffic:

- Festival demand
- Weekend spikes

---

## API Design

### Search Product

```http
GET /products?query=milk
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
 "quantity":2
}
```

### Place Order

```http
POST /orders
```

### Track Order

```http
GET /orders/{orderId}
```

---

## Database Design

### Product Table

| Field | Type |
|--------|-------|
| product_id | UUID |
| name | String |
| stock | Integer |
| warehouse_id | UUID |

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
Catalog Service
 |
Inventory Service
 |
Warehouse Service
 |
Order Service
 |
Delivery Assignment Service
 |
Kafka
 |
Tracking Service
 |
Redis Cache
 |
Database
```

---

## Core Components

### Inventory Service

Responsibilities:

- Stock validation
- Inventory update
- Prevent overselling

### Warehouse Service

Responsibilities:

- Nearest warehouse selection
- Warehouse inventory lookup

### Delivery Assignment Service

Responsibilities:

- Assign delivery partner
- ETA optimization

Techniques:

- GeoHash
- Distance calculation

### Tracking Service

Responsibilities:

- Delivery tracking
- Live location updates

---

## Order Lifecycle

```text
ORDER_PLACED
 ↓
INVENTORY_RESERVED
 ↓
PACKING
 ↓
OUT_FOR_DELIVERY
 ↓
DELIVERED
```

---

## Scaling Strategy

### Cache

Redis:

- Inventory cache
- Product cache

### Queue

Kafka:

- Order processing
- Tracking events

### Database

- Read replica
- Sharding

---

## Reliability

Strategies:

- Retry mechanism
- Inventory reservation
- Dead letter queue
- Multi region deployment

---

## Bottlenecks

| Problem | Solution |
|----------|-----------|
| Inventory contention | Reservation system |
| Delivery spike | Dynamic allocation |
| Search latency | Redis cache |
| Order burst | Kafka buffering |

---

## Tradeoffs

| Choice | Benefit | Drawback |
|---------|----------|-----------|
| Inventory reservation | Prevent overselling | Lower throughput |
| Aggressive cache | Faster lookup | Stale inventory |

---

## Interview Questions

1. How inventory consistency maintained?
2. How nearest warehouse selected?
3. Why inventory reservation needed?
4. How delivery assignment works?
5. Why Kafka useful?
6. How tracking scales?

---

## Quick Revision

- Inventory reservation prevents overselling
- GeoHash improves warehouse lookup
- Kafka handles order events
- Redis improves latency
- Warehouse optimization improves delivery speed
- Sharding improves scalability