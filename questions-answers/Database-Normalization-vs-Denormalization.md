

# Database Normalization vs Denormalization

## Why This Comparison Matters?

Normalization and Denormalization are database design approaches.

System design interviews frequently ask database design tradeoffs because production systems balance:

- Data consistency
- Query performance
- Storage optimization
- Scalability
- Read latency

Choosing the wrong design can create:

- Duplicate data
- Slow queries
- Complex joins
- Data inconsistency

Understanding database design is important for:

- System Design Interviews
- Backend Development
- Database Design
- Production Systems

---

## Normalization

Normalization reduces duplicate data.

Goal:

```text
Reduce Redundancy
Improve Consistency
```

Example:

Without Normalization:

```text
Orders Table

OrderID
CustomerName
CustomerAddress
CustomerPhone
```

Repeated customer information creates duplication.

Normalized Design:

```text
Customers Table

CustomerID
Name
Address
Phone

Orders Table

OrderID
CustomerID
```

Best For:

- Banking Systems
- Payment Systems
- Transaction Systems

Pros:

- Less duplicate data
- Better consistency
- Lower storage usage

Cons:

- More joins
- Read query slower

---

## Denormalization

Denormalization intentionally adds duplicate data.

Goal:

```text
Faster Reads
Lower Query Complexity
```

Example:

```text
Orders Table

OrderID
CustomerName
CustomerAddress
CustomerPhone
```

Customer information duplicated.

Read becomes faster.

Best For:

- Analytics Systems
- Social Feed Systems
- Read Heavy Platforms

Pros:

- Faster reads
- Fewer joins
- Better read performance

Cons:

- Data duplication
- Higher storage usage
- Update complexity

---

## Key Differences

| Feature | Normalization | Denormalization |
|----------|---------------|-----------------|
| Duplicate Data | Lower | Higher |
| Storage Usage | Lower | Higher |
| Read Performance | Lower | Better |
| Write Consistency | Better | Harder |
| Join Requirement | Higher | Lower |
| Best For | Transactions | Read Heavy Systems |

---

## Production Example

Banking Platform:

```text
Correct Data
Consistency Required
```

Choose:

```text
Normalization
```

Social Feed Platform:

```text
Fast Feed Read
Massive Traffic
```

Choose:

```text
Denormalization
```

---

## Production Reality

Large systems commonly combine both.

Example:

```text
Orders Database
↓
Normalized

Analytics Database
↓
Denormalized
```

---

## Interview Shortcut

Remember:

```text
Normalization
→ Correctness

Denormalization
→ Performance
```

---

## Interview Questions

1. Normalization vs Denormalization?

2. Why normalization improves consistency?

3. Why denormalization improves performance?

4. Banking database choice?

5. Why joins impact performance?

6. Why production systems combine both?

---

## Quick Revision

- Normalization reduces duplication
- Denormalization improves read speed
- Normalization improves consistency
- Denormalization reduces joins
- Production systems commonly combine both
- Database design tradeoff is common interview topic