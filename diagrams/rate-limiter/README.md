

# Rate Limiter Diagram

## Purpose

Rate Limiter protects systems from excessive traffic.

Goals:

- Prevent abuse
- Protect infrastructure
- Improve availability
- Prevent overload
- Improve reliability

---

## High Level Flow

```text
Client Requests
      ↓
Rate Limiter
      ↓

Allowed Request
      ↓
Application Service

OR

Blocked Request
      ↓
429 Too Many Requests
```

---

## Production Flow

```text
Client
 ↓
CDN
 ↓
Load Balancer
 ↓
API Gateway
 ↓
Rate Limiter
 ↓
Application Service
 ↓
Database
```

---

## Why Rate Limiter?

Without Rate Limiter:

```text
Traffic Spike
↓
Service Overload
↓
Higher Latency
↓
Failure Risk
```

Problems:

- Resource exhaustion
- API abuse
- DDoS impact
- Poor availability

With Rate Limiter:

```text
Traffic Control
↓
Stable System
```

---

## Common Algorithms

### Token Bucket

```text
Tokens Added Periodically
↓
Request Uses Token
↓
No Token → Reject
```

Best For:

- Burst traffic

---

### Leaky Bucket

```text
Incoming Requests
↓
Fixed Processing Rate
```

Best For:

- Smooth traffic handling

---

### Fixed Window

```text
100 Requests
Per Minute
```

Best For:

- Simple implementation

---

### Sliding Window

```text
Rolling Time Window
↓
More Accurate Control
```

Best For:

- Production APIs

---

## Production Examples

Rate Limiter commonly used in:

- API Gateway
- Authentication systems
- Payment APIs
- Public APIs

---

## Interview Notes

Common discussion:

```text
Token Bucket vs Leaky Bucket

429 Too Many Requests

Distributed Rate Limiting
```

---

## Quick Revision

```text
Rate Limiter
→ Traffic Protection

Token Bucket
→ Burst Traffic

Sliding Window
→ Better Accuracy

429
→ Too Many Requests
```