# Uber System Design

## Problem Statement

Design a ride booking platform like Uber.

Features:

- Book Ride
- Find Nearby Driver
- Real Time Driver Location
- Ride Tracking
- Payment
- Notification

Examples:

- Uber
- Ola
- Lyft

---

## Functional Requirements

System should support:

1. User Registration

2. Driver Registration

3. Ride Booking

4. Driver Matching

5. Ride Tracking

6. Payment Processing

7. Ride History

---

## Non Functional Requirements

- High Availability
- Low Latency
- Scalability
- Fault Tolerance
- Real Time Updates

Interview Tip:

Uber interviews focus heavily on:

```text
Location Service
+ 
Driver Matching
```

---

## Capacity Estimation

Assume:

```text
50 Million Daily Active Users
```

Assume:

```text
5 Rides Per User
```

Total:

```text
250 Million Ride Requests / Day
```

---

## API Design

Book Ride:

```text
POST /ride/book
```

Nearby Driver:

```text
GET /driver/nearby
```

Ride Status:

```text
GET /ride/{rideId}
```

---

## Database Design

User Table:

| UserId | Name |
|--------|------|
| U101 | Roy |

Driver Table:

| DriverId | Name | Location |
|-----------|------|-----------|
| D101 | Alex | Bangalore |

Ride Table:

| RideId | UserId | DriverId | Status |
|--------|--------|-----------|--------|
| R101 | U101 | D101 | Started |

Common Databases:

- PostgreSQL
- Cassandra

---

## High Level Design

```text
Mobile Client

↓

Load Balancer

↓

Ride Service

↓

Driver Matching Service

↓

Location Service

↓

Database
```

Supporting Services:

```text
Notification Service

Payment Service

Kafka

Redis
```

---

## Driver Matching

Interview Focus Topic.

Goal:

```text
Find Nearest Driver
```

Techniques:

- Geohash
- QuadTree

Example:

```text
User Location

↓

Nearby Drivers

↓

Nearest Match
```

---

## Real Time Location

Driver updates location continuously.

Example:

```text
Driver

↓

Kafka

↓

Location Service

↓

Passenger
```

Interview Tip:

Real time systems commonly use:

```text
WebSocket
```

---

## Cache Strategy

Use:

```text
Redis
```

Cache:

- Driver Location
- Hot Ride Data

Benefits:

- Lower latency
- Faster lookup

---

## Scaling Strategy

Application:

- Horizontal Scaling
- Load Balancer

Database:

- Replication
- Sharding

Messaging:

- Kafka

---

## Bottleneck

Problems:

- Driver location update spike
- Traffic surge
- Database hotspot

Solutions:

- Redis
- Kafka
- Read Replica

---

## Interview Questions

### Q1. Biggest Uber challenge?

Nearest driver matching.

---

### Q2. Why Kafka used?

Real time event processing.

---

### Q3. Why Redis used?

Fast location lookup.

---

### Q4. Why WebSocket used?

Real time location update.

---

## Quick Revision

- Uber → Location heavy system
- Kafka → Event streaming
- Redis → Fast lookup
- Geohash → Nearby search
- WebSocket → Real time updates
- Driver matching → Core problem