# CAP Theorem Diagram

## Definition

CAP Theorem states that a distributed system can guarantee only two out of three properties:

- Consistency (C)
- Availability (A)
- Partition Tolerance (P)

Interview Tip:

Distributed systems must always handle network partition.

So real choice becomes:

```text
CP

or

AP
```

---

## CAP Components

### Consistency (C)

All users see same latest data.

Example:

```text
User A Updates Profile

↓

All Servers Show Updated Value
```

Benefits:

- Correct data
- Predictable behavior

Example Systems:

- Banking Systems
- Payment Systems

---

### Availability (A)

Every request gets response.

Even if some nodes fail.

Example:

```text
User Request

↓

System Responds Always
```

Benefits:

- Better uptime
- Better user experience

Example Systems:

- Social Media
- E-Commerce

---

### Partition Tolerance (P)

System continues working despite network failures.

Example:

Before issue:

```text
Server A

↓

Server B
```

Network failure:

```text
Server A X Server B
```

System still operates.

Partition tolerance is mandatory in distributed systems.

---

## CAP Visualization

```text
        Consistency
             /\
            /  \
           /    \
          /      \
         /        \
Availability ---- Partition Tolerance
```

Cannot guarantee:

```text
C + A + P
```

Together.

---

## CP System

Choose:

```text
Consistency

+

Partition Tolerance
```

Sacrifice:

```text
Availability
```

Example:

Network failure:

```text
Reject Request

↓

Maintain Correct Data
```

Examples:

- HBase
- MongoDB (certain configurations)

Best for:

- Banking
- Financial systems

---

## AP System

Choose:

```text
Availability

+

Partition Tolerance
```

Sacrifice:

```text
Strong Consistency
```

Example:

```text
Request Accepted

↓

Data Sync Later
```

Examples:

- Cassandra
- DynamoDB

Best for:

- Social Media
- Feed Systems

---

## Real World Example

Instagram Like Count:

User A:

```text
100 Likes
```

User B:

```text
99 Likes
```

Few seconds later:

```text
100 Likes
```

System favors:

```text
Availability
```

Example:

AP system.

---

## Banking Example

Balance Update:

```text
₹1000

↓

₹500
```

All servers must show:

```text
₹500
```

System favors:

```text
Consistency
```

Example:

CP system.

---

## CAP Interview Questions

### Q1. Can distributed systems support C + A + P?

No.

Only two possible.

---

### Q2. Why Partition Tolerance mandatory?

Network failures happen.

Distributed systems must survive.

---

### Q3. Banking prefers CP or AP?

CP.

---

### Q4. Social media prefers CP or AP?

Mostly AP.

---

## Quick Revision

- C → Same latest data
- A → Always response
- P → Network failure tolerance
- CP → Correctness priority
- AP → Availability priority
- Banking → CP
- Social Media → AP
# CAP Theorem Diagram

## Purpose

CAP Theorem explains tradeoffs in distributed systems.

Goals:

- Understand distributed system behavior
- Learn consistency tradeoffs
- Design reliable systems
- Understand network partition handling
- Improve system design decisions

---

## What Is CAP Theorem?

Distributed systems can guarantee only two properties during network partition.

Properties:

- Consistency (C)
- Availability (A)
- Partition Tolerance (P)

Interview Rule:

```text
Distributed Systems
↓
Partition Happens
↓
Choose:
CP
or
AP
```

---

## Consistency (C)

Definition:

All users see same latest data.

Example:

```text
User Updates Profile
↓
All Servers Show Same Value
```

Benefits:

- Correct data
- Predictable behavior

Best For:

- Banking systems
- Payment systems

---

## Availability (A)

Definition:

System always responds.

Example:

```text
Request
↓
System Responds
```

Benefits:

- Better uptime
- Better user experience

Best For:

- Social platforms
- E commerce systems

---

## Partition Tolerance (P)

Definition:

System continues operating despite network failure.

Before Failure:

```text
Node A
↓
Node B
```

Network Partition:

```text
Node A X Node B
```

System continues working.

Interview Rule:

```text
Partition Tolerance
→ Mandatory
```

---

## CAP Visualization

```text
       Consistency
            /\
           /  \
          /    \
         /      \
Availability----Partition Tolerance
```

Impossible:

```text
C + A + P
```

Together during partition.

---

## CP System

Choose:

```text
Consistency
+
Partition Tolerance
```

Sacrifice:

```text
Availability
```

Example:

```text
Network Failure
↓
Reject Request
↓
Protect Data Correctness
```

Examples:

- HBase
- MongoDB (certain configurations)

Best For:

- Banking systems
- Financial systems

---

## AP System

Choose:

```text
Availability
+
Partition Tolerance
```

Sacrifice:

```text
Strong Consistency
```

Example:

```text
Request Accepted
↓
Data Sync Later
```

Examples:

- Cassandra
- DynamoDB

Best For:

- Feed systems
- Social platforms

---

## Production Example

Social Feed:

```text
User A
→ 100 Likes

User B
→ 99 Likes

Few Seconds Later
↓
100 Likes
```

System favors:

```text
Availability
```

---

## Banking Example

```text
Balance
1000
↓
500
```

Requirement:

```text
All Servers
↓
500
```

System favors:

```text
Consistency
```

---

## Interview Notes

Common discussion:

```text
CP vs AP

Partition Tolerance Mandatory

Strong Consistency vs Eventual Consistency
```

---

## Quick Revision

```text
C
→ Same Latest Data

A
→ Always Respond

P
→ Survive Network Failure

CP
→ Correctness Priority

AP
→ Availability Priority
```