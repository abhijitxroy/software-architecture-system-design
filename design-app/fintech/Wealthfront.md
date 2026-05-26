# Wealthfront System Design

## Problem Statement

Design an investment management platform like Wealthfront.

Features:

- Portfolio Management
- Goal Based Investment
- Risk Profiling
- Fund Allocation
- Portfolio Rebalancing
- Performance Tracking
- Notification

Examples:

- Wealthfront
- Betterment

---

## Clarifying Questions

Interview starts here.

Questions:

1. Investment recommendation needed?

2. Portfolio rebalancing required?

3. Real time stock price required?

4. Notification needed?

5. User goal tracking needed?

---

## Functional Requirements

System should support:

1. User Registration

2. Risk Assessment

3. Portfolio Recommendation

4. Investment Tracking

5. Portfolio Rebalancing

6. Notification

7. Goal Tracking

---

## Non Functional Requirements

- High Availability
- Scalability
- Reliability
- Security
- Low Latency

Interview Focus:

```text
Portfolio Recommendation
+
Portfolio Rebalancing
```

---

## Capacity Estimation

Assume:

```text
10 Million Users
```

Traffic Type:

```text
Read Heavy System
```

Reason:

Users check portfolio more often than modifying.

---

## API Design

Portfolio:

```text
GET /portfolio
```

Risk Profile:

```text
POST /risk-profile
```

Rebalance:

```text
POST /portfolio/rebalance
```

---

## Database Design

User Table:

| UserId | Name |
|--------|------|
| U101 | Roy |

Portfolio Table:

| PortfolioId | UserId | Risk |
|--------------|--------|------|
| P101 | U101 | Medium |

Investment Table:

| InvestmentId | Asset | Allocation |
|---------------|-------|------------|
| I101 | ETF | 30% |

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

Portfolio Service

↓

Recommendation Engine

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

## Recommendation Engine

Interview Focus Topic.

Inputs:

- Age
- Risk Appetite
- Investment Goal
- Investment Duration

Output:

```text
Portfolio Allocation
```

---

## Portfolio Rebalancing

Goal:

```text
Maintain Target Allocation
```

Example:

```text
Target

Stocks 70%

Bond 30%

↓

Rebalance
```

---

## Cache Strategy

Use:

```text
Redis
```

Cache:

- Portfolio Data
- Market Data

Benefits:

- Lower latency
- Faster dashboard loading

---

## Scaling Strategy

Application:

- Horizontal Scaling

Database:

- Read Replica
- Partitioning

Messaging:

- Kafka

---

## Security

Important:

- Authentication
- Authorization
- Encryption
- Audit Log

---

## Bottleneck

Problems:

- Market traffic spike
- Recommendation load
- Portfolio recalculation

Solutions:

- Redis
- Kafka
- Cache Layer

---

## Interview Questions

### Q1. Biggest Wealthfront challenge?

Portfolio recommendation.

---

### Q2. Why Redis used?

Fast dashboard loading.

---

### Q3. Why Kafka used?

Async processing.

---

## Quick Revision

- Wealthfront → Investment platform
- Recommendation → Core feature
- Redis → Cache
- Kafka → Async processing
- Rebalancing → Portfolio optimization
- Security → Critical requirement
