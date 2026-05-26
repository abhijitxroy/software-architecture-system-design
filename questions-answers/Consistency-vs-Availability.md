

# Consistency vs Availability

## Why This Comparison Matters?

Consistency and Availability are core distributed system concepts.

System design interviews commonly ask tradeoff questions around both.

Choosing the wrong priority can impact:

- User experience
- Reliability
- Data correctness
- Scalability
- Production stability

Understanding tradeoffs is important for:

- System Design Interviews
- Distributed Systems
- Database Design
- Production Architecture

---

## Consistency

Consistency means users always see the latest data.

Example:

```text
User A Updates Balance
       ↓
Database Updated
       ↓
User B Reads Balance
       ↓
Latest Value Returned
```

Goal:

- Correct data
- No stale reads
- Same data everywhere

Examples:

- Banking systems
- Payment systems
- Inventory systems

Advantages:

- Data correctness
- Predictable behavior

Challenges:

- Higher latency possible
- Availability tradeoff

---

## Availability

Availability means system responds even during failures.

Example:

```text
Node A Failed
     ↓
Node B Responds
     ↓
User Gets Response
```

Goal:

- High uptime
- Faster response
- Better user experience

Examples:

- Social media feed
- Video streaming
- Recommendation systems

Advantages:

- Better uptime
- Better resilience

Challenges:

- Stale data possible

---

## Key Differences

| Feature | Consistency | Availability |
|----------|-------------|---------------|
| Goal | Correct Data | System Uptime |
| Focus | Data Accuracy | Service Reliability |
| User Experience | Latest Data | Faster Response |
| Failure Scenario | May Reject Request | Continue Serving |
| Banking System | Preferred | Less Important |
| Social Platform | Less Important | Preferred |

---

## Production Example

Banking Platform:

```text
Wrong Balance
→ Not Acceptable
```

Priority:

```text
Consistency
```

Social Platform:

```text
Feed Slightly Delayed
→ Acceptable
```

Priority:

```text
Availability
```

---

## Interview Shortcut

Remember:

```text
Consistency
→ Correct Data

Availability
→ System Always Responds
```

---

## Tradeoff Example

Example:

```text
Network Partition Happens
```

Choose:

```text
Serve Old Data
OR
Reject Request
```

Serve old data:

```text
Availability Priority
```

Reject request:

```text
Consistency Priority
```

---

## Interview Questions

1. Consistency vs Availability?

2. Banking system preference?

3. Social media preference?

4. Why stale reads happen?

5. Why distributed systems require tradeoffs?

6. CAP theorem relation?

---

## Quick Revision

- Consistency means latest data
- Availability means uptime
- Banking systems prioritize consistency
- Social systems commonly prioritize availability
- Distributed systems require tradeoffs
- Network failures force design decisions
- CAP theorem connects both concepts