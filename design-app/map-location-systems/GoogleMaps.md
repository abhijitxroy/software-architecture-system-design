

# Google Maps System Design

## Problem Statement

Design a map platform like Google Maps that supports route search, navigation, ETA prediction and real time traffic updates at global scale.

System should support:

- Location Search
- Route Planning
- Navigation
- Traffic Updates
- ETA Prediction
- Nearby Places
- Real Time Location Tracking

---

## Functional Requirements

### Core Features

- Search location
- Find shortest route
- Turn by turn navigation
- Show traffic condition
- Estimate arrival time
- Save favorite places
- Nearby restaurant and fuel search
- Real time location sharing

---

## Non Functional Requirements

### Scalability

- Billions of locations
- Millions of requests/sec

### Availability

- 99.99% uptime

### Reliability

- Accurate navigation

### Latency

- Route generation under seconds

---

## Capacity Estimation

Assume:

- 500 Million DAU
- 100 Billion location records
- 50 Million routing requests/day

Storage:

Map metadata + traffic + route index

Petabyte scale storage

---

## API Design

### Search Location

```http
GET /search?q=airport
```

---

### Find Route

```http
GET /route?source=A&destination=B
```

---

### Share Location

```http
POST /location/share
```

---

## Database Design

### Location Table

| Field | Type |
|--------|-------|
| location_id | UUID |
| latitude | Decimal |
| longitude | Decimal |
| metadata | JSON |

### Traffic Table

| Field | Type |
|--------|-------|
| road_id | UUID |
| congestion | Integer |
| updated_at | Timestamp |

---

## High Level Design

```text
Client
 |
Load Balancer
 |
Map API Service
 |
Geo Service
 |
+----------------+
| GeoHash Index  |
+----------------+
 |
Route Service
 |
Traffic Service
 |
Redis Cache
 |
Map Database

GPS Stream
 |
Kafka
 |
Traffic Processing
```

---

## Core Components

### GeoHash

Used for:

- Nearby search
- Geo partitioning
- Faster lookup

### Route Service

Responsibilities:

- Route generation
- Shortest path calculation
- Alternative routes

Algorithms:

- Dijkstra
- A*

### Traffic Service

Responsibilities:

- Traffic aggregation
- Congestion prediction
- ETA optimization

### ETA Service

Factors:

- Traffic
- Distance
- Historical travel pattern

---

## Scaling Strategy

### Database

- Geo partitioning
- Replication
- Sharding

### Cache

Redis:

- Popular route cache
- Hot location cache

### Queue

Kafka:

- GPS stream processing
- Traffic analytics

---

## Reliability

Strategies:

- Multi region deployment
- Replication
- Retry mechanism
- Cache fallback

---

## Bottlenecks

| Problem | Solution |
|----------|-----------|
| Traffic spike | Cache routes |
| Large geo data | Geo partition |
| ETA latency | Cache computation |
| GPS stream load | Kafka buffering |

---

## Tradeoffs

| Choice | Benefit | Drawback |
|---------|----------|-----------|
| Aggressive cache | Faster response | Stale route |
| Frequent GPS update | Better ETA | Higher cost |

---

## Interview Questions

1. Why GeoHash needed?
2. How ETA calculated?
3. Why Kafka useful?
4. How nearby search optimized?
5. How routing scales?
6. Why cache routes?

---

## Quick Revision

- GeoHash improves geo search
- Kafka handles GPS stream
- Cache improves latency
- Dijkstra and A* optimize routing
- Sharding improves scalability
- Traffic data improves ETA