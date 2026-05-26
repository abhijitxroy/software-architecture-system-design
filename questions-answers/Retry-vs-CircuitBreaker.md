

# Retry vs Circuit Breaker

## Why This Comparison Matters?

Retry and Circuit Breaker improve reliability in distributed systems.

Production systems face:

- Network failures
- Service timeout
- Temporary dependency failure
- Traffic spikes
- Partial outages

Choosing the wrong strategy can create:

- Cascading failure
- Higher latency
- Resource exhaustion
- System instability

Understanding reliability patterns is important for:

- System Design Interviews
- Distributed Systems
- Backend Development
- Production Systems

---

## Retry

Retry attempts operation again after failure.

Flow:

```text
Client
 ↓
Service Request
 ↓
Failure
 ↓
Retry
 ↓
Success
```

Goal:

```text
Recover Temporary Failure
```

Best For:

- Network timeout
- Temporary dependency issue
- Transient failure

Pros:

- Higher reliability
- Improves success rate
- Simple implementation

Cons:

- Higher latency
- More resource usage
- Retry storm risk

Common Strategies:

```text
Fixed Retry
Exponential Backoff
Exponential Backoff + Jitter
```

---

## Circuit Breaker

Circuit Breaker stops requests to failing services.

Flow:

```text
Service Failure
 ↓
Circuit Opens
 ↓
Requests Blocked
 ↓
Recovery Check
 ↓
Circuit Closed
```

Goal:

```text
Protect System Stability
```

States:

```text
Closed
↓
Open
↓
Half Open
```

Best For:

- Dependency protection
- Service failure isolation
- Cascading failure prevention

Pros:

- Protects infrastructure
- Prevents overload
- Improves resilience

Cons:

- Operational complexity
- Configuration tuning needed

---

## Key Differences

| Feature | Retry | Circuit Breaker |
|----------|-------|-----------------|
| Goal | Recover Failure | Prevent Failure Spread |
| Request Behavior | Retry Request | Block Request |
| Best For | Temporary Issue | Dependency Failure |
| Latency Impact | Higher | Lower During Failure |
| System Protection | Lower | Better |

---

## Production Example

Payment API Timeout:

```text
Temporary Network Issue
```

Choose:

```text
Retry
```

Database Dependency Failure:

```text
Dependency Unhealthy
```

Choose:

```text
Circuit Breaker
```

---

## Production Reality

Large systems commonly combine both.

Example:

```text
Retry
↓
Recover Temporary Failure

Circuit Breaker
↓
Protect Dependency
```

Production Pattern:

```text
Retry
↓
Circuit Breaker
↓
Fallback Response
```

---

## Interview Shortcut

Remember:

```text
Retry
→ Recover Failure

Circuit Breaker
→ Prevent Failure Spread
```

---

## Interview Questions

1. Retry vs Circuit Breaker?

2. Why retry storm happens?

3. What is exponential backoff?

4. Circuit Breaker states?

5. Why cascading failure happens?

6. Why production systems combine both?

---

## Quick Revision

- Retry handles temporary failure
- Circuit Breaker prevents cascading failure
- Retry increases success rate
- Circuit Breaker protects dependency
- Exponential backoff improves retry strategy
- Large systems combine both patterns
- Reliability patterns are common interview topic