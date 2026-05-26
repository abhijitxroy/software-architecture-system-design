

# Chat System Design

## Problem Statement

Design a chat system like WhatsApp, Slack or Messenger that supports real time communication at massive scale.

System should support:

- One to One Chat
- Group Chat
- Online Presence
- Message Delivery Status
- Push Notification
- Media Sharing
- Message History
- Read Receipt

---

## Functional Requirements

### Core Features

- Send messages
- Receive messages
- Store chat history
- Group messaging
- Online offline status
- Message retry
- Push notification
- Media attachment

---

## Non Functional Requirements

### Scalability

- Millions of concurrent users
- Horizontal scaling

### Availability

- 99.99% uptime

### Reliability

- No message loss

### Latency

- Message delivery under 100 ms

---

## Capacity Estimation

Assume:

- 100 Million DAU
- 50 messages/user/day

Messages/day:

100M × 50

= 5 Billion messages/day

Assume:

Average message size = 1 KB

Storage/day:

≈ 5 TB/day

---

## API Design

### Send Message

```http
POST /messages
```

Request:

```json
{
 "senderId":"u1",
 "receiverId":"u2",
 "message":"Hello"
}
```

Response:

```json
{
 "messageId":"msg_123",
 "status":"SENT"
}
```

---

### Fetch Chat

```http
GET /messages/{chatId}
```

---

## Database Design

### Message Table

| Field | Type |
|--------|-------|
| message_id | UUID |
| sender_id | UUID |
| receiver_id | UUID |
| content | Text |
| created_at | Timestamp |
| status | String |

---

## High Level Design

```text
Client
 |
Load Balancer
 |
Chat Service
 |
WebSocket Gateway
 |
Kafka
 |
Message Service
 |
Redis Cache
 |
Message Database

Presence Service
 |
Redis

Notification Service
 |
Push Notification
```

---

## Core Components

### WebSocket Gateway

Responsibilities:

- Persistent connection
- Real time communication
- Delivery acknowledgment

Why WebSocket?

- Low latency
- Full duplex communication

### Chat Service

Responsibilities:

- Message validation
- Routing
- Retry handling

### Kafka

Used for:

- Message queue
- Event streaming
- Decouple services

### Presence Service

Responsibilities:

- Online status
- Last seen
- Active device tracking

### Notification Service

Responsibilities:

- Push notification
- Offline notification

---

## Message Lifecycle

```text
SENT
 ↓
DELIVERED
 ↓
READ
```

Retry Flow:

```text
SEND
 ↓
FAILED
 ↓
RETRY
```

---

## Scaling Strategy

### Database

- Sharding by user id
- Read replica

### Cache

Redis:

- Active connection cache
- Presence cache

### Queue

Kafka:

- Async delivery
- Retry handling

---

## Reliability

Strategies:

- Retry with backoff
- Dead letter queue
- Replication
- Multi region deployment

---

## Bottlenecks

|      Problem	      |      Solution       |
|---------------------|---------------------|
| Hot user traffic    | Partition chat data |
| Message spikes      | Kafka buffering     |
| DB overload         | Cache + Replica     |
| Connection overload | WebSocket cluster.  |

---

## Tradeoffs

| Choice | Benefit | Drawback |
|---------|----------|-----------|
| WebSocket | Real time | Persistent connection cost |
| Async processing | Scalability | Eventual consistency |

---

## Interview Questions

1. Why WebSocket over HTTP?
2. How online presence works?
3. How messages ordered?
4. Why Kafka useful?
5. How chat system scales?
6. How retry works?

---

## Quick Revision

- WebSocket enables real time communication
- Kafka improves scalability
- Redis improves latency
- Sharding improves scale
- Presence service tracks online users
- Retry improves reliability