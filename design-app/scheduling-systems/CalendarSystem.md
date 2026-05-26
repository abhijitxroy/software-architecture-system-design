

# Calendar System Design

## Problem Statement

Design a calendar system like Google Calendar or Outlook Calendar that supports event scheduling, recurring meetings, reminders and conflict detection at large scale.

System should support:

- Event Creation
- Event Update
- Event Deletion
- Recurring Events
- Calendar Sharing
- Reminder Notification
- Conflict Detection
- Time Zone Support

---

## Functional Requirements

### Core Features

- Create calendar event
- Update event
- Delete event
- Invite participants
- Recurring meetings
- Reminder notification
- Calendar sharing
- Conflict handling

---

## Non Functional Requirements

### Scalability

- Millions of active users
- Millions of scheduled events/day

### Availability

- 99.99% uptime

### Reliability

- No event loss

### Latency

- Fast event creation

### Consistency

- Consistent scheduling state

---

## Capacity Estimation

Assume:

- 50 Million DAU
- 500 Million events/day
- Average event size: 2 KB

Storage/day:

500M × 2 KB

≈ 1 TB/day

Yearly:

≈ 365 TB/year

---

## API Design

### Create Event

```http
POST /events
```

Request:

```json
{
 "title":"System Design Meeting",
 "start":"2026-06-10T10:00:00",
 "end":"2026-06-10T11:00:00"
}
```

### Get Calendar

```http
GET /calendar/{userId}
```

### Update Event

```http
PATCH /events/{eventId}
```

---

## Database Design

### Event Table

| Field | Type |
|--------|-------|
| event_id | UUID |
| owner_id | UUID |
| start_time | Timestamp |
| end_time | Timestamp |
| recurrence | String |

### Reminder Table

| Field | Type |
|--------|-------|
| reminder_id | UUID |
| event_id | UUID |
| notify_time | Timestamp |

---

## High Level Design

```text
Client
 |
Load Balancer
 |
Calendar API
 |
Event Service
 |
Conflict Detection Service
 |
Reminder Service
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

### Event Service

Responsibilities:

- Create event
- Update event
- Recurring event generation

### Conflict Detection Service

Responsibilities:

- Time overlap validation
- Schedule conflict detection

Example:

```text
Meeting A → 10:00 - 11:00
Meeting B → 10:30 - 11:30

Conflict Found
```

### Reminder Service

Responsibilities:

- Notification scheduling
- Reminder delivery

### Time Zone Service

Responsibilities:

- Time conversion
- Global scheduling support

---

## Scheduling Flow

```text
Create Event
 ↓
Conflict Validation
 ↓
Persist Event
 ↓
Reminder Scheduling
 ↓
Notification
```

---

## Scaling Strategy

### Cache

Redis:

- User calendar cache
- Event cache

### Queue

Kafka:

- Reminder events
- Notification processing

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
| Reminder spike | Queue buffering |
| Calendar read traffic | Redis cache |
| Conflict validation load | Partitioning |
| Notification burst | Kafka scaling |

---

## Tradeoffs

| Choice | Benefit | Drawback |
|---------|----------|-----------|
| Aggressive caching | Faster reads | Stale calendar data |
| Complex recurrence engine | Better UX | Higher complexity |

---

## Interview Questions

1. How recurring events stored?
2. How conflict detection works?
3. Why Kafka useful?
4. How reminders scale?
5. Why cache calendar data?
6. How time zones handled?

---

## Quick Revision

- Conflict detection prevents overlap
- Kafka handles reminder events
- Redis improves latency
- Recurring events increase complexity
- Time zone handling critical globally
- Sharding improves scalability