

# Notification System Design

## Problem Statement

Design a notification system like email notifications, push notifications and SMS delivery platforms that supports reliable notification delivery at large scale.

System should support:

- Push Notification
- Email Notification
- SMS Notification
- User Preference Management
- Retry Mechanism
- Notification Scheduling
- Delivery Tracking
- Multi Channel Delivery

---

## Functional Requirements

### Core Features

- Send notification
- Schedule notification
- Retry failed notification
- Track delivery status
- User notification preference
- Multi channel notification
- Notification template management
- Rate limiting

---

## Non Functional Requirements

### Scalability

- Billions of notifications/day
- Millions of active users

### Availability

- 99.99% uptime

### Reliability

- No notification loss

### Latency

- Fast notification delivery

---

## Capacity Estimation

Assume:

- 100 Million DAU
- 20 notifications/user/day

Notifications/day:

100M × 20

≈ 2 Billion notifications/day

Storage:

Notification logs + templates + analytics

Multi TB yearly storage

---

## API Design

### Send Notification

```http
POST /notifications
```

Request:

```json
{
 "userId":"u123",
 "channel":"PUSH",
 "message":"Order Delivered"
}
```

### Notification Status

```http
GET /notifications/{notificationId}
```

---

## Database Design

### Notification Table

| Field | Type |
|--------|-------|
| notification_id | UUID |
| user_id | UUID |
| channel | String |
| status | String |
| created_at | Timestamp |

### User Preference Table

| Field | Type |
|--------|-------|
| user_id | UUID |
| push_enabled | Boolean |
| sms_enabled | Boolean |
| email_enabled | Boolean |

---

## High Level Design

```text
Producer Service
 |
Notification API
 |
Preference Service
 |
Kafka
 |
Notification Processor
 |
+----------------+
| Push Service   |
| SMS Service    |
| Email Service  |
+----------------+
 |
Redis Cache
 |
Database
 |
Analytics Pipeline
```

---

## Core Components

### Notification API

Responsibilities:

- Accept notification request
- Validate payload
- Publish event

### Preference Service

Responsibilities:

- User preference validation
- Channel selection

Example:

```text
User Disabled SMS
 ↓
Send Email Only
```

### Notification Processor

Responsibilities:

- Retry failed delivery
- Channel routing
- Delivery tracking

### Kafka

Responsibilities:

- Queue buffering
- Retry workflow
- Async processing

---

## Notification Flow

```text
Event Generated
 ↓
Notification API
 ↓
Kafka
 ↓
Preference Check
 ↓
Channel Selection
 ↓
Notification Delivery
 ↓
Analytics Update
```

---

## Scaling Strategy

### Queue

Kafka:

- Notification buffering
- Retry processing

### Cache

Redis:

- User preference cache
- Template cache

### Database

- Sharding
- Read replica

---

## Reliability

Strategies:

- Dead letter queue
- Retry mechanism
- Idempotency
- Multi region deployment

---

## Bottlenecks

| Problem | Solution |
|----------|-----------|
| Notification spike | Queue buffering |
| Preference lookup latency | Redis cache |
| Delivery failure | Retry mechanism |
| Traffic burst | Horizontal scaling |

---

## Tradeoffs

| Choice | Benefit | Drawback |
|---------|----------|-----------|
| Async processing | Better scalability | Delivery delay |
| Retry mechanism | Better reliability | Extra compute |

---

## Interview Questions

1. Why Kafka useful?
2. Why notification preference needed?
3. How retry mechanism works?
4. Why idempotency important?
5. How notification delivery scales?
6. How failed delivery handled?

---

## Quick Revision

- Kafka improves scalability
- Retry improves reliability
- Redis improves lookup latency
- User preference improves experience
- Queue buffering handles spikes
- Idempotency prevents duplicate notifications