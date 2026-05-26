# Rate Limiter

## Definition

Rate limiter controls how many requests a user or system can make within a specific time period.

It protects backend systems from traffic spikes, abuse and overload.

---

## Why Needed?

Without rate limiter:

```text
User

↓

Backend Service

100000 Requests / Minute
```

Problems:

- Server overload
- Application slowdown
- System crash
- API abuse
- Bot attacks

With rate limiter:

```text
User

↓

Rate Limiter

↓

Backend Service
```

Benefits:

- Protect backend services
- Prevent abuse
- Improve availability
- Improve system stability

---

## Example

API Limit:

```text
100 Requests / Minute
```

Scenario:

```text
User → 95 Requests

Allowed
```

User sends:

```text
110 Requests
```

Response:

```text
HTTP 429

Too Many Requests
```

---

## How It Works?

Steps:

1. User sends request
2. Rate limiter checks request count
3. Compare against configured limit
4. Allow or reject request

Example:

```text
Limit = 100 Requests / Minute

Current User Count = 75

75 < 100

Request Allowed
```

---

## Rate Limiting Algorithms

## 1. Fixed Window Counter

Requests counted within fixed time window.

Example:

```text
10 Requests / Minute
```

Timeline:

```text
12:00 → Counter Start

12:00–12:59

10 Requests Allowed

11th Request Rejected
```

Problem:

Traffic spike near window boundary.

---

## 2. Sliding Window

Request count moves continuously.

Example:

```text
Previous 60 Seconds
```

Benefits:

- Better traffic control
- More accurate limiting

Common production choice.

---

## 3. Token Bucket

Bucket stores tokens.

Request processing:

```text
1 Request

↓

Consume 1 Token
```

Example:

Bucket:

```text
100 Tokens
```

Refill:

```text
10 Tokens / Second
```

Benefits:

- Supports traffic burst
- Flexible control

Used heavily in production.

---

## 4. Leaky Bucket

Requests processed at constant speed.

Example:

```text
Incoming Burst

1000 Requests

↓

Process

100 Requests / Second
```

Benefits:

- Smooth traffic flow
- Stable backend utilization

---

## Fixed Window vs Sliding Window

| Feature | Fixed Window | Sliding Window |
|----------|---------------|----------------|
| Accuracy | Lower | Higher |
| Complexity | Simple | More Complex |
| Burst Handling | Weak | Better |
| Production Usage | Medium | High |

---

## Token Bucket vs Leaky Bucket

| Feature | Token Bucket | Leaky Bucket |
|----------|---------------|---------------|
| Burst Traffic | Allowed | Controlled |
| Traffic Pattern | Flexible | Constant |
| Complexity | Medium | Medium |

Interview Tip:

Token Bucket → Burst allowed

Leaky Bucket → Constant flow

---

## Production Examples

- API Gateway
- Payment Systems
- Login APIs
- OTP APIs
- Banking Systems
- Public APIs

Production Tools:

- Redis
- NGINX
- Kong
- AWS API Gateway

---

## Real World Example

Login API:

```text
5 Login Attempts

Per Minute
```

Exceed limit:

```text
HTTP 429

Too Many Requests
```

Prevents:

- Brute force attack
- Credential abuse

---

## Interview Questions

### Q1. Why Rate Limiter needed?

Protect backend systems from overload and abuse.

---

### Q2. Which algorithm commonly used?

Token Bucket

Sliding Window

---

### Q3. Why Redis used for Rate Limiter?

- Fast
- Distributed
- Atomic counter support

---

## Quick Revision

- Rate limiter → Traffic control
- HTTP 429 → Too Many Requests
- Token Bucket → Burst support
- Leaky Bucket → Constant processing
- Sliding Window → Better accuracy
- Redis → Common production implementation
