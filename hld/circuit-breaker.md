# Circuit Breaker

## Definition

Circuit Breaker prevents repeated calls to a failing service.

It protects backend systems from cascading failures and improves system stability.

---

## Why Needed?

Without Circuit Breaker:

```text
Service A

↓

Service B (Down)

↓

Retry

↓

Retry

↓

Retry

↓

System Slowdown
```

Problems:

- Cascading failure
- Thread exhaustion
- Increased latency
- Resource wastage
- Service unavailability

---

## With Circuit Breaker

```text
Client

↓

Service A

↓

Circuit Breaker

↓

Service B
```

If Service B fails repeatedly:

```text
Circuit Open

↓

Request Blocked
```

Benefits:

- Prevent overload
- Faster failure handling
- Better resilience
- System protection

---

## How It Works?

Steps:

1. Service call starts normally
2. Failures monitored
3. Failure threshold exceeded
4. Circuit opens
5. Requests blocked temporarily
6. Recovery check happens
7. Service resumes

---

## Circuit Breaker States

## 1. Closed State

Normal operation.

```text
Request

↓

Backend Service
```

All requests allowed.

---

## 2. Open State

Too many failures detected.

```text
Request

↓

Circuit Breaker

↓

Rejected
```

Backend not called.

Benefits:

- Protect failing system
- Reduce resource usage

---

## 3. Half Open State

System tests recovery.

```text
Small Request Sample

↓

Backend Service
```

If successful:

```text
Half Open

↓

Closed
```

If failure:

```text
Half Open

↓

Open
```

---

## State Flow

```text
Closed

↓

Failure Threshold Crossed

↓

Open

↓

Recovery Timeout

↓

Half Open

↓

Success → Closed

Failure → Open
```

---

## Example

Payment Service:

```text
Order Service

↓

Payment Service
```

Payment service becomes slow.

Without Circuit Breaker:

```text
5000 Requests

↓

Timeout

↓

Application Slow
```

With Circuit Breaker:

```text
Failures Detected

↓

Circuit Open

↓

Fallback Response
```

Example fallback:

```text
Payment Service Currently Unavailable
```

---

## Fallback Mechanism

Fallback provides alternate response.

Examples:

- Cached response
- Default value
- Friendly error message

Example:

```text
Recommendation Service Down

↓

Return Cached Recommendations
```

---

## Production Tools

Java:

- Resilience4j
- Hystrix (Legacy)

Cloud:

- Istio
- Envoy

---

## Real World Usage

Used in:

- Payment Systems
- Microservices
- Banking Systems
- E-Commerce Platforms
- Notification Services

---

## Circuit Breaker vs Retry

| Feature | Circuit Breaker | Retry |
|----------|-----------------|-------|
| Prevent Failure Storm | Yes | No |
| Auto Recovery | Yes | No |
| Protect Backend | Yes | No |
| Retry Failed Request | No | Yes |

Interview Tip:

Retry handles temporary failure.

Circuit Breaker protects failing systems.

---

## Interview Questions

### Q1. Why Circuit Breaker needed?

Prevent cascading failures.

---

### Q2. Circuit Breaker states?

- Closed
- Open
- Half Open

---

### Q3. Retry vs Circuit Breaker?

Retry retries.

Circuit Breaker blocks.

---

## Quick Revision

- Prevent cascading failure
- Closed → Open → Half Open
- Open → Block requests
- Half Open → Recovery validation
- Common in Microservices
- Improves resilience