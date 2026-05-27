

# Trading Platform System Design

## Problem Statement

Design a trading platform like Zerodha, Groww or Robinhood that supports order placement, portfolio tracking, market data processing and low latency trading.

System should support:

- Buy Order
- Sell Order
- Portfolio Management
- Market Data Streaming
- Order Matching
- Trade History
- Watchlist
- Risk Validation

---

## Functional Requirements

### Core Features

- Place buy order
- Place sell order
- View portfolio
- Live stock price update
- Order history
- Watchlist management
- Position tracking
- PnL tracking

---

## Non Functional Requirements

### Scalability

- Millions of users
- High throughput trading

### Availability

- 99.99% uptime

### Reliability

- No order loss

### Latency

- Millisecond execution latency

### Consistency

- Strong consistency for orders

---

## Capacity Estimation

Assume:

- 20 Million users
- 200 Million market events/day
- 50 Million orders/day

Peak traffic:

- Market open traffic spike

Storage:

Trade history + portfolio + analytics

Multi TB yearly storage

---

## API Design

### Place Order

```http
POST /orders
```

Request:

```json
{
 "symbol":"RELIANCE",
 "type":"BUY",
 "quantity":10,
 "price":2500
}
```

Response:

```json
{
 "orderId":"ord_123",
 "status":"PLACED"
}
```

---

### Portfolio

```http
GET /portfolio/{userId}
```

---

### Market Data

```http
GET /marketdata/{symbol}
```

---

## Database Design

### Order Table

| Field | Type |
|--------|-------|
| order_id | UUID |
| user_id | UUID |
| symbol | String |
| quantity | Integer |
| price | Decimal |
| status | String |
| created_at | Timestamp |

### Portfolio Table

| Field | Type |
|--------|-------|
| user_id | UUID |
| symbol | String |
| quantity | Integer |
| avg_price | Decimal |

---

## High Level Design

```text
Client
 |
Load Balancer
 |
API Gateway
 |
Order Service
 |
Risk Service
 |
Order Matching Engine
 |
Kafka
 |
Trade Processor
 |
Portfolio Service
 |
Redis Cache
 |
Primary Database

Market Data Feed
 |
Streaming Pipeline
```

---

## Core Components

### Order Matching Engine

Responsibilities:

- Match buy order
- Match sell order
- Price priority
- Time priority

Matching Rule:

```text
Best Price
   ↓
Earliest Order
```

### Risk Service

Responsibilities:

- Margin validation
- Trading limit validation
- Fraud detection

### Market Data Service

Responsibilities:

- Price streaming
- Live market update
- Event processing

### Portfolio Service

Responsibilities:

- Holdings tracking
- Profit and loss
- Position calculation

---

## Trading Flow

```text
Place Order
 ↓
Risk Validation
 ↓
Order Matching
 ↓
Trade Execution
 ↓
Portfolio Update
 ↓
Notification
```

---

## Scaling Strategy

### Database

- Read replica
- Partitioning
- Sharding

### Cache

Redis:

- Portfolio cache
- Market data cache

### Queue

Kafka:

- Trade event processing
- Analytics pipeline

---

## Reliability

Strategies:

- Retry mechanism
- Multi region deployment
- Replication
- Dead letter queue

---

## Security

- MFA
- Encryption
- Audit log
- Rate limiting
- Fraud monitoring

---

## Bottlenecks

| Problem | Solution |
|----------|-----------|
| Market spike | Queue buffering |
| Portfolio read load | Redis cache |
| Matching latency | In memory engine |
| Traffic surge | Horizontal scaling |

---

## Tradeoffs

| Choice | Benefit | Drawback |
|---------|----------|-----------|
| In memory engine | Faster execution | Higher memory usage |
| Strong consistency | Correct trading state | Higher latency |

---

## Interview Questions

1. Why matching engine needed?
2. How order priority works?
3. Why Redis useful?
4. How market spike handled?
5. How low latency achieved?
6. Why Kafka useful?

---

## Quick Revision

- Matching engine drives trade execution
- Kafka handles market events
- Redis improves latency
- Strong consistency protects trade correctness
- Risk service validates trading rules
- In memory processing improves execution speed