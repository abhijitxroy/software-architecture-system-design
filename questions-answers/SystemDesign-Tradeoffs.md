# System Design Tradeoffs

## Why Tradeoffs Matter?

System Design is about tradeoffs.

There is no perfect design.

Improving one area often impacts another.

Examples:

```text
Higher Consistency
↓
Lower Availability

Lower Latency
↓
Higher Infrastructure Cost
```

System design interviews frequently test tradeoff understanding.

Understanding tradeoffs is important for:

- System Design Interviews
- Distributed Systems
- Production Architecture
- Scalability Design

---

## Consistency vs Availability

Question:

```text
Correct Data
OR
Always Available
```

Example:

Banking Platform:

```text
Prefer Consistency
```

Social Feed:

```text
Prefer Availability
```

Tradeoff:

```text
Correctness
vs
User Experience
```

---

## Latency vs Consistency

Question:

```text
Latest Data
OR
Fast Response
```

Example:

Strong Consistency:

```text
Correct Data
Higher Latency
```

Eventual Consistency:

```text
Faster Response
Possible Delay
```

---

## Read Optimization vs Write Optimization

Question:

```text
Fast Reads
OR
Fast Writes
```

Example:

Fan Out On Write:

```text
Faster Feed Read
Higher Write Cost
```

Fan Out On Read:

```text
Lower Write Cost
Higher Read Latency
```

---

## SQL vs NoSQL

Question:

```text
Transactions
OR
Massive Scale
```

SQL:

```text
Correctness
Complex Query
```

NoSQL:

```text
Scale
Flexibility
```

---

## Monolith vs Microservices

Question:

```text
Simplicity
OR
Independent Scaling
```

Monolith:

```text
Lower Complexity
```

Microservices:

```text
Higher Scalability
```

---

## Cache vs Database

Question:

```text
Performance
OR
Durability
```

Cache:

```text
Low Latency
```

Database:

```text
Source Of Truth
```

---

## Replication vs Sharding

Question:

```text
Availability
OR
Write Scalability
```

Replication:

```text
Read Scaling
```

Sharding:

```text
Massive Scale
```

---

## Production Reality

Large systems combine approaches.

Example:

```text
PostgreSQL
↓
Orders

Redis
↓
Cache

Kafka
↓
Events

Cassandra
↓
Analytics
```

No single technology solves everything.

---

## Interview Shortcut

Remember:

```text
System Design
=
Tradeoffs
```

Question interviewers ask:

```text
Why choose this design?

What problems appear later?

How will system scale?
```

---

## Interview Questions

1. Why tradeoffs matter?

2. Consistency vs Availability?

3. Cache vs Database?

4. SQL vs NoSQL?

5. Monolith vs Microservices?

6. Why production systems combine technologies?

---

## Quick Revision

- System design is tradeoff driven
- No perfect architecture exists
- Scalability creates complexity
- Consistency impacts latency
- Availability impacts correctness
- Production systems combine technologies
- Tradeoff discussion is interview favorite