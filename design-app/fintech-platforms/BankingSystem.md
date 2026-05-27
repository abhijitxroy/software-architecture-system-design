

# Banking System Design

## Problem Statement

Design a banking system that supports account management, deposits, withdrawals, transfers and transaction processing securely at large scale.

System should support:

- Account Creation
- Deposit Money
- Withdraw Money
- Balance Inquiry
- Money Transfer
- Transaction History
- Notification
- Fraud Detection

---

## Functional Requirements

### Core Features

- Create account
- Deposit money
- Withdraw money
- Transfer money
- View account balance
- Transaction history
- Daily transaction limit
- User notification

---

## Non Functional Requirements

### Scalability

- Millions of customers
- High transaction throughput

### Availability

- 99.99% uptime

### Reliability

- No transaction loss

### Consistency

- Strong consistency

### Security

- Encryption
- Authentication
- Authorization

---

## Capacity Estimation

Assume:

- 50 Million users
- 100 Million transactions/day
- Average transaction record: 1 KB

Storage/day:

100M × 1 KB

≈ 100 GB/day

Yearly:

≈ 36 TB/year

---

## API Design

### Create Account

```http
POST /accounts
```

### Deposit Money

```http
POST /deposit
```

Request:

```json
{
 "accountId":"123",
 "amount":5000
}
```

### Transfer Money

```http
POST /transfer
```

Request:

```json
{
 "from":"A123",
 "to":"B456",
 "amount":1000
}
```

---

## Database Design

### Account Table

| Field | Type |
|--------|-------|
| account_id | UUID |
| customer_id | UUID |
| balance | Decimal |
| created_at | Timestamp |

### Transaction Table

| Field | Type |
|--------|-------|
| transaction_id | UUID |
| from_account | UUID |
| to_account | UUID |
| amount | Decimal |
| status | String |
| created_at | Timestamp |

---

## High Level Design

```text
Client
 |
API Gateway
 |
Authentication Service
 |
Banking Service
 |
Transaction Service
 |
Redis Cache
 |
Primary Database
 |
Replica Database
 |
Kafka
 |
Notification Service
```

---

## Core Components

### Banking Service

Responsibilities:

- Account management
- Balance validation
- Transaction creation

### Transaction Service

Responsibilities:

- Money transfer
- Transaction consistency
- Retry failed operation

### ACID Properties

A → Atomicity

- Complete transaction fully or rollback

C → Consistency

- Valid banking state maintained

I → Isolation

- Parallel transactions safe

D → Durability

- Data survives failures

### Redis

Used for:

- Balance cache
- User session cache

### Kafka

Used for:

- Notification
- Audit event
- Analytics

---

## Transfer Flow

```text
Validate Account
 ↓
Check Balance
 ↓
Debit Sender
 ↓
Credit Receiver
 ↓
Commit Transaction
 ↓
Send Notification
```

---

## Scaling Strategy

### Database

- Read replica
- Partitioning
- Sharding

### Cache

Redis:

- Account cache
- Transaction cache

---

## Reliability

Strategies:

- Retry with backoff
- Replication
- Multi region backup
- Dead letter queue

---

## Security

- TLS Encryption
- MFA
- Audit Log
- Fraud Detection
- Rate Limiting

---

## Bottlenecks

| Problem | Solution |
|----------|-----------|
| DB overload | Replica database |
| Duplicate transfer | Idempotency |
| Fraud traffic | Rate limiting |
| Transaction spike | Queue buffering |

---

## Tradeoffs

| Choice | Benefit | Drawback |
|---------|----------|-----------|
| Strong consistency | Correct balance | Higher latency |
| Cache balance | Faster response | Cache invalidation |

---

## Interview Questions

1. Why ACID important?
2. Why banking requires strong consistency?
3. How duplicate transaction prevented?
4. How transfer rollback works?
5. Why replica database needed?
6. How banking scales?

---

## Quick Revision

- ACID critical for banking
- Strong consistency preferred
- Redis improves latency
- Replica improves scalability
- Kafka supports async processing
- Idempotency prevents duplicate transaction