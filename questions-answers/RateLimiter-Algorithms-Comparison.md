# Rate Limiter Algorithms Comparison

## Why This Comparison Matters?

Rate Limiting protects systems from overload.

System design interviews commonly ask rate limiter design because production systems need protection against:

- Traffic spikes
- Abuse
- DDoS attacks
- API overuse
- Infrastructure overload

Understanding rate limiting is important for:

- System Design Interviews
- API Design
- Distributed Systems
- Production Architecture

---

## Fixed Window Counter

Requests are counted inside a fixed time window.

Flow:

```text
Limit = 100 Requests
Window = 1 Minute

Minute Starts
      ↓
Count Requests
      ↓
Limit Reached?
 ↓         ↓
No         Yes
 ↓          ↓
Allow     Reject
```

Example:

```text
100 Requests Per Minute
```

Pros:

- Simple implementation
- Low memory usage
- Fast processing

Cons:

- Burst traffic issue

Problem:

```text
100 Requests
59th Second
+
100 Requests
1st Second

200 Requests Allowed
```

---

## Sliding Window Log

Store request timestamps.

Flow:

```text
New Request
    ↓
Remove Old Entries
    ↓
Count Active Requests
    ↓
Allow Or Reject
```

Pros:

- Better accuracy
- Smooth traffic handling

Cons:

- Higher memory usage
- More storage needed

Best For:

- Security systems
- API protection

---

## Sliding Window Counter

Combines:

```text
Fixed Window
+
Sliding Window
```

Goal:

```text
Lower Memory
+
Better Accuracy
```

Pros:

- Better traffic smoothing
- Lower memory than log approach

Cons:

- Slight complexity

Best For:

- Production APIs

---

## Token Bucket

System generates tokens continuously.

Request consumes token.

Flow:

```text
Bucket Size = 100

Token Available?
 ↓        ↓
Yes       No
 ↓         ↓
Allow    Reject
```

Pros:

- Handles burst traffic
- Flexible traffic control
- Common production choice

Cons:

- Configuration tuning needed

Best For:

- API Gateway
- User API protection

---

## Leaky Bucket

Requests enter bucket.

Requests leave bucket at fixed speed.

Flow:

```text
Traffic
  ↓
Bucket
  ↓
Constant Output Rate
```

Pros:

- Smooth traffic
- Predictable output

Cons:

- Burst traffic delayed

Best For:

- Network traffic shaping

---

## Key Differences

| Algorithm | Burst Support | Memory Usage | Accuracy | Complexity |
|------------|---------------|--------------|-----------|------------|
| Fixed Window | Weak | Low | Lower | Simple |
| Sliding Log | Better | Higher | Best | Higher |
| Sliding Counter | Better | Medium | Better | Medium |
| Token Bucket | Strong | Low | Better | Medium |
| Leaky Bucket | Moderate | Low | Better | Medium |

---

## Production Example

Public API:

```text
Need Burst Handling
```

Choose:

```text
Token Bucket
```

Security API:

```text
Need Accuracy
```

Choose:

```text
Sliding Window
```

---

## Interview Shortcut

Remember:

```text
Fixed Window
→ Simple

Sliding Window
→ Accurate

Token Bucket
→ Burst Traffic

Leaky Bucket
→ Smooth Traffic
```

---

## Interview Questions

1. Token Bucket vs Leaky Bucket?

2. Fixed Window limitation?

3. Why sliding window improves accuracy?

4. Which algorithm handles burst traffic?

5. API Gateway rate limiter choice?

6. Distributed rate limiter design?

---

## Quick Revision

- Fixed Window is simplest
- Sliding Window improves accuracy
- Token Bucket handles burst traffic
- Leaky Bucket smooths traffic
- Rate limiting protects infrastructure
- API Gateway commonly uses rate limiting
- Rate limiter design is common interview topic
