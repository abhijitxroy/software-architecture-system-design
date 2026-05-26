

# Ad Serving System Design

## Problem Statement

Design an ad serving platform like Google Ads or Meta Ads that supports ad targeting, ad ranking, bidding and low latency ad delivery at massive scale.

System should support:

- Ad Creation
- Ad Targeting
- Ad Ranking
- Bid Processing
- Impression Tracking
- Click Tracking
- Campaign Management
- Analytics Dashboard

---

## Functional Requirements

### Core Features

- Create campaign
- Upload advertisement
- Audience targeting
- Ad bidding
- Ad delivery
- Impression tracking
- Click tracking
- Analytics reporting

---

## Non Functional Requirements

### Scalability

- Billions of ad requests/day
- Millions of campaigns

### Availability

- 99.99% uptime

### Reliability

- No event loss

### Latency

- Ad serving under 100 ms

### Durability

- Historical analytics persistence

---

## Capacity Estimation

Assume:

- 5 Billion ad requests/day
- 100 Million clicks/day
- 10 Million campaigns

Storage:

Campaign + Impression + Click Analytics

Petabyte scale storage

Peak Traffic:

- Festival events
- Sports events

---

## API Design

### Create Campaign

```http
POST /campaigns
```

### Serve Ad

```http
GET /ads?userId=u123
```

### Analytics API

```http
GET /analytics/{campaignId}
```

---

## Database Design

### Campaign Table

| Field | Type |
|--------|-------|
| campaign_id | UUID |
| advertiser_id | UUID |
| budget | Decimal |
| status | String |
| created_at | Timestamp |

### Impression Table

| Field | Type |
|--------|-------|
| event_id | UUID |
| ad_id | UUID |
| user_id | UUID |
| timestamp | Timestamp |
| click | Boolean |

---

## High Level Design

```text
Client
 |
Load Balancer
 |
Ad API
 |
Targeting Service
 |
Ranking Service
 |
Bid Engine
 |
Redis Cache
 |
Ad Database
 |
Kafka
 |
Analytics Pipeline
```

---

## Core Components

### Targeting Service

Responsibilities:

- Audience filtering
- Geo targeting
- Interest targeting

### Ranking Service

Responsibilities:

- Ad scoring
- Ranking decision
- CTR optimization

Ranking Factors:

- Bid amount
- CTR
- Relevance score

### Bid Engine

Responsibilities:

- Auction execution
- Bid validation
- Winner selection

### Analytics Pipeline

Responsibilities:

- Impression analytics
- Click analytics
- Campaign reporting

---

## Ad Serving Flow

```text
Ad Request
 ↓
Targeting
 ↓
Bid Auction
 ↓
Ranking
 ↓
Ad Selection
 ↓
Analytics Event
```

---

## Scaling Strategy

### Cache

Redis:

- Campaign cache
- Hot ad cache

### Queue

Kafka:

- Impression events
- Click events

### Database

- Sharding
- Read replica

---

## Reliability

Strategies:

- Retry mechanism
- Replication
- Dead letter queue
- Multi region deployment

---

## Bottlenecks

| Problem | Solution |
|----------|-----------|
| Traffic spike | Horizontal scaling |
| Ranking latency | Redis cache |
| Analytics overload | Kafka buffering |
| Hot campaign traffic | Partitioning |

---

## Tradeoffs

| Choice | Benefit | Drawback |
|---------|----------|-----------|
| Aggressive cache | Lower latency | Stale targeting |
| Complex ranking | Better relevance | Higher compute |

---

## Interview Questions

1. How ad ranking works?
2. How bid engine works?
3. Why Kafka useful?
4. How CTR impacts ranking?
5. How analytics scale?
6. Why Redis useful?

---

## Quick Revision

- Bid engine selects winning ad
- Ranking improves relevance
- Kafka handles analytics events
- Redis improves latency
- Targeting improves conversion
- Sharding improves scalability