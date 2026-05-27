

# Payment Gateway System Design

## Problem Statement

Design a payment gateway system like Stripe, Razorpay or PayPal that can process payments securely, reliably and at large scale.

The system should support:

- Payment Initiation
- Payment Authorization
- Payment Capture
- Refund Processing
- Payment Status Tracking
- Retry Handling
- Idempotency
- Multi Payment Provider Support

---

## Functional Requirements

### Core Features

- User initiates payment
- Validate payment request
- Route payment to payment provider
- Support cards, UPI, net banking, wallet
- Handle success and failure flow
- Retry failed payment safely
- Refund payment
- View transaction history

---

## Non Functional Requirements

### Scalability

- Millions of payments daily
- Horizontal scaling

### Availability

- 99.99% uptime

### Reliability

- No duplicate payment

### Security

- Encryption
- PCI DSS compliance

### Latency

- Payment processing within seconds

---

## Capacity Estimation

Assume:

- 20 Million transactions/day
- Peak TPS: 5000+
- Average payment record: 2 KB

Storage per day:

20M × 2 KB = 40 GB/day

Yearly:

~14 TB/year

---

## API Design

### Create Payment

```http
POST /payments
```

Request:

```json
{
  "userId":"123",
  "amount":500,
  "currency":"INR",
  "paymentMethod":"UPI"
}
```

Response:

```json
{
  "paymentId":"pay_123",
  "status":"PENDING"
}
```

---

### Get Payment Status

```http
GET /payments/{paymentId}
```

---

### Refund Payment

```http
POST /refunds
```

---

## Database Design

### Payment Table

| Field | Type |
|--------|-------|
| payment_id | UUID |
| user_id | UUID |
| amount | Decimal |
| status | String |
| provider | String |
| created_at | Timestamp |

### Refund Table

| Field | Type |
|--------|-------|
| refund_id | UUID |
| payment_id | UUID |
| amount | Decimal |
| status | String |

---

## High Level Design

```text
Client
   |
API Gateway
   |
Payment Service
   |
+----------------+
| Idempotency DB |
+----------------+
   |
Payment Processor
   |
+-----------------------+
| Stripe / Bank / UPI   |
+-----------------------+
   |
Kafka
   |
Notification Service
   |
Email / SMS / Push
```

---

## Core Components

### Payment Service

Responsibilities:

- Validate request
- Create transaction
- Handle retries
- Maintain payment state

### Idempotency Layer

Prevents:

- Double charge
- Duplicate retry processing

Example:

Client retry happens because timeout occurred.

Same idempotency key:

```text
idem_123
```

Existing payment returned instead of creating new charge.

### Payment Processor

Responsibilities:

- Provider routing
- Retry failed provider
- Maintain transaction consistency

### Kafka

Used for:

- Notification
- Analytics
- Audit logging

---

## Payment Lifecycle

```text
PENDING
   ↓
AUTHORIZED
   ↓
CAPTURED
   ↓
SUCCESS
```

Failure Flow:

```text
PENDING
   ↓
FAILED
   ↓
RETRY
```

Refund:

```text
SUCCESS
   ↓
REFUND_PENDING
   ↓
REFUNDED
```

---

## Scaling Strategy

### Database Scaling

- Read Replica
- Partitioning
- Sharding

### Cache

Redis:

- Payment status cache
- Idempotency cache

### Queue

Kafka:

- Async processing
- Event driven architecture

---

## Reliability

Strategies:

- Retry with exponential backoff
- Circuit breaker
- Dead letter queue
- Multi provider fallback

---

## Security

- HTTPS
- Encryption at rest
- Encryption in transit
- PCI DSS compliance
- Tokenization
- Fraud detection

---

## Bottlenecks

| Problem | Solution |
|----------|-----------|
| Duplicate payment | Idempotency |
| Provider downtime | Fallback provider |
| DB hotspot | Sharding |
| Retry storm | Backoff strategy |

---

## Tradeoffs

| Design Choice | Benefit | Drawback |
|---------------|----------|-----------|
| Strong Consistency | Correct payment state | Higher latency |
| Async processing | Better throughput | Eventual consistency |

---

## Interview Questions

1. How to prevent duplicate payment?
2. Why idempotency matters?
3. How refund processing works?
4. How retry logic should work?
5. How to handle provider failure?
6. Why Kafka is useful here?
7. How to scale payment systems?

---

## Quick Revision

- Idempotency prevents duplicate payment
- Kafka enables async processing
- Retry with backoff improves reliability
- Circuit breaker protects dependency failure
- Multi provider improves availability
- Cache improves latency