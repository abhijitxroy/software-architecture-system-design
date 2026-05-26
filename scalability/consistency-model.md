# Consistency Model

## Definition

Consistency model defines how data remains synchronized across distributed systems.

It determines when users can see updated data after write operations.

Goal:

- Data correctness
- Predictable behavior
- Better distributed system design

---

## Why Needed?

Single database:

```text
User

↓

Database

↓

Read Latest Data
```

No problem.

Distributed system:

```text
User A

↓

Server 1

↓

Database Replica 1
```

```text
User B

↓

Server 2

↓

Database Replica 2
```

Problem:

```text
User A Updated Profile

↓

Replica 1 Updated

↓

Replica 2 Delayed
```

User B may see old data.

This creates:

- Inconsistent data
- User confusion
- Wrong business decisions

---

## Strong Consistency

Definition:

Every read gets latest written value.

Example:

```text
User Updates Balance

₹1000 → ₹1200
```

Immediately:

```text
All Servers

↓

₹1200
```

Benefits:

- Data correctness
- Predictable behavior

Problems:

- Higher latency
- Lower availability

Examples:

- Banking systems
- Payment systems

Interview Tip:

Banking systems usually prefer Strong Consistency.

---

## Eventual Consistency

Definition:

System becomes consistent after some time.

Example:

```text
User Updates Profile Picture
```

Replica 1:

```text
Updated Immediately
```

Replica 2:

```text
Updated After Few Seconds
```

Eventually:

```text
All Replicas Same Data
```

Benefits:

- Better scalability
- Better availability

Problems:

- Temporary stale data

Examples:

- Social Media
- DNS
- Caching systems

Interview Tip:

Social media systems commonly use eventual consistency.

---

## Weak Consistency

Definition:

No guarantee when updated data becomes visible.

Example:

```text
User Posts Comment

↓

Some users see immediately

↓

Others later
```

Benefits:

- Better performance

Problems:

- Less predictable

Examples:

- Real time analytics
- Large cache systems

---

## Strong vs Eventual Consistency

| Feature | Strong Consistency | Eventual Consistency |
|----------|--------------------|----------------------|
| Latest Data Guaranteed | Yes | No |
| Availability | Lower | Higher |
| Performance | Lower | Better |
| Scalability | Lower | Better |
| Use Cases | Banking | Social Media |

Interview Tip:

Strong → Correctness

Eventual → Scalability

---

## CAP Theorem Relation

Distributed systems choose tradeoffs.

Example:

```text
Consistency

vs

Availability
```

Examples:

Strong consistency systems:

- PostgreSQL
- Traditional RDBMS

Eventual consistency systems:

- Cassandra
- DynamoDB

---

## Real World Example

Instagram Like Count:

User likes post.

```text
Server 1

100 Likes
```

Server 2:

```text
99 Likes
```

Few seconds later:

```text
Both Servers

100 Likes
```

Eventual consistency.

---

## Interview Questions

### Q1. Strong vs Eventual Consistency?

Strong:

Always latest data.

Eventual:

Data sync happens later.

---

### Q2. Why eventual consistency used?

Better scalability and availability.

---

### Q3. Banking system consistency type?

Strong consistency.

---

## Quick Revision

- Consistency → Data synchronization
- Strong → Latest data always
- Eventual → Sync happens later
- Weak → No guarantee
- Banking → Strong consistency
- Social Media → Eventual consistency
- Scalability → Eventual consistency