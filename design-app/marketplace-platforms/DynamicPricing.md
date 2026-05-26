

# Dynamic Pricing System Design

## Problem Statement

Design a dynamic pricing system like Uber surge pricing, airline pricing or hotel pricing that adjusts price automatically based on supply, demand and business conditions.

Used in:

- Ride Sharing
- Food Delivery
- Hotel Booking
- Airline Ticket Pricing
- Ecommerce Marketplace

System should support:

- Real Time Price Calculation
- Demand Prediction
- Supply Analysis
- Surge Pricing
- Regional Pricing
- Peak Hour Pricing
- Pricing Rules

---

## Functional Requirements

### Core Features

- Calculate price dynamically
- Demand forecasting
- Supply monitoring
- Regional multiplier
- Peak pricing
- Discount support
- Rule engine
- Analytics tracking

---

## Non Functional Requirements

### Scalability

- Millions of pricing requests/day

### Availability

- 99.99% uptime

### Reliability

- Pricing consistency

### Latency

- Price calculation under 100 ms

---

## Why Dynamic Pricing Needed

Without dynamic pricing:

```text
Demand Spike
↓
Limited Supply
↓
Long Wait Time
```

Problems:

- Supply shortage
- Poor marketplace balance
- Revenue loss

Goal:

```text
Balance Supply + Demand
```

---

## Pricing Signals

Inputs:

### Demand

Examples:

- Ride requests
- Orders/minute
- User traffic

### Supply

Examples:

- Available drivers
- Delivery partners
- Hotel inventory

### External Factors

Examples:

- Rain
- Peak hours
- Events
- Holidays

---

## Surge Pricing

Example:

```text
Demand = 500
Supply = 100

Multiplier = 2.5x
```

Formula:

```text
Final Price =
Base Price × Surge Multiplier
```

Example:

```text
₹200 × 2.5
=
₹500
```

---

## Pricing Engine

Components:

```text
Traffic Analyzer
↓
Demand Predictor
↓
Supply Analyzer
↓
Pricing Rules Engine
↓
Price Calculator
```

---

## API Design

### Get Price

```http
GET /pricing
```

Response:

```json
{
 "basePrice":200,
 "surge":2.0,
 "finalPrice":400
}
```

---

## High Level Design

```text
Client
 |
Pricing API
 |
Traffic Service
 |
Demand Forecast Service
 |
Rules Engine
 |
Redis Cache
 |
Pricing Database
 |
Kafka Analytics
```

---

## Pricing Flow

```text
User Request
↓
Collect Demand Signal
↓
Collect Supply Signal
↓
Pricing Rules
↓
Calculate Multiplier
↓
Return Price
```

---

## Demand Prediction

Signals:

- Historical traffic
- Weather
- Peak hours
- Active users

Example:

```text
Friday 6 PM
↓
High Demand Predicted
↓
Increase Price
```

---

## Scaling Strategy

### Redis

Responsibilities:

- Hot pricing cache
- Fast lookup

### Kafka

Responsibilities:

- Pricing analytics
- Event processing

### Partitioning

Partition by:

```text
Region
```

---

## Reliability

Strategies:

- Cache fallback
- Retry mechanism
- Rule versioning
- Multi region deployment

---

## Tradeoffs

| Choice | Benefit | Drawback |
|----------|----------|-----------|
| Aggressive surge | Higher supply | User dissatisfaction |
| Static pricing | Simple | Marketplace imbalance |
| Demand prediction | Better planning | Model complexity |

---

## Interview Questions

1. Why dynamic pricing needed?
2. Surge pricing advantages?
3. Supply vs demand balancing?
4. Why Redis useful?
5. How demand prediction works?
6. Why pricing cache needed?

---

## Quick Revision

- Dynamic pricing balances supply and demand
- Surge pricing improves marketplace balance
- Redis improves latency
- Kafka handles analytics events
- Demand forecasting improves pricing
- Rules engine controls pricing logic