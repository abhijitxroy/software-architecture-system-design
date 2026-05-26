

# Rate Limiter System

## What is Rate Limiter?

Rate Limiter is a system design pattern used to control how many requests a user, client, service or API can perform within a specific time window.

Rate limiting protects systems from overload, abuse and traffic spikes.

Rate limiters are critical for improving reliability, fairness and platform protection.

Rate limiters are commonly used in:

- API Gateway
- Authentication systems
- Payment platforms
- Cloud infrastructure
- Developer APIs
- Public web services

---

## Why Rate Limiter?

Problems without rate limiting:

- API abuse
- Denial of service risk
- Resource exhaustion
- Traffic spikes
- Unfair resource usage

Rate limiting improves:

- Reliability
- Platform protection
- Fair resource sharing
- Stability
- Availability

---

## High Level Architecture

```text
Client Request
      |
      v
+----------------+
| Rate Limiter   |
| Validation     |
+--------+-------+
         |
 +-------+-------+
 |               |
Allowed        Rejected
 |               |
 v               v
API Service   HTTP 429
```

---

## Core Components

### Request Identifier

Identifies request owner.

Examples:

```text
User ID
API Key
IP Address
Session ID
```

Responsibilities:

- Traffic ownership
- Rate tracking

---

### Counter Store

Stores request count.

Examples:

- Redis
- Memcached
- In Memory Cache

Requirements:

- Low latency
- Fast updates
- Scalability

---

### Window Manager

Tracks time interval.

Examples:

```text
100 Requests
Per Minute
```

Responsibilities:

- Window expiration
- Counter reset

---

## Rate Limiting Algorithms

### Fixed Window Counter

Requests counted within fixed interval.

Example:

```text
100 Requests
Per Minute
```

Advantages:

- Simple implementation

Disadvantages:

- Boundary burst issue

---

### Sliding Window Log

Stores timestamp of requests.

Example:

```text
Current Time - 60 Seconds
↓
Count Requests
```

Advantages:

- Better accuracy

Disadvantages:

- Higher memory usage

---

### Sliding Window Counter

Combines fixed windows with weighted calculation.

Advantages:

- Better efficiency
- Lower memory usage

---

### Token Bucket

Requests consume tokens.

Flow:

```text
Bucket Capacity = 100
Token Refill = 10 Per Second
```

Advantages:

- Burst traffic handling

Common usage:

- API Gateway
- Cloud systems

---

### Leaky Bucket

Processes traffic at fixed rate.

Flow:

```text
Incoming Requests
       ↓
Bucket Queue
       ↓
Constant Processing
```

Advantages:

- Smooth traffic flow

---

## Distributed Rate Limiting

Production systems commonly use centralized counters.

Architecture:

```text
API Node A
API Node B
API Node C
      ↓
Redis Cluster
      ↓
Shared Counter
```

Benefits:

- Consistent enforcement
- Horizontal scaling

---

## Rate Limiting Headers

Common HTTP headers:

```text
X-RateLimit-Limit
X-RateLimit-Remaining
Retry-After
```

Example:

```text
HTTP 429 Too Many Requests
```

---

## Production Challenges

Common issues:

- Distributed counter consistency
- Traffic burst handling
- Hot key problem
- Counter storage bottleneck
- False throttling

Solutions:

- Redis cluster
- Token bucket
- Sharding
- Cache optimization
- Monitoring

---

## Production Examples

Examples:

- API Gateway platform
- Banking API protection
- Authentication system
- Payment infrastructure
- Cloud API platform

---

## Interview Questions

1. What is Rate Limiter?

2. Token bucket vs leaky bucket?

3. Fixed window vs sliding window?

4. Why Redis is common for rate limiting?

5. Distributed rate limiting challenges?

6. Why HTTP 429 matters?

---

## Quick Revision

- Rate limiter protects systems from overload
- Token bucket handles burst traffic
- Sliding window improves accuracy
- Redis commonly stores counters
- HTTP 429 indicates throttling
- Distributed counters improve scalability
- Rate limiting improves reliability