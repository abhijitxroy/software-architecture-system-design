

# Database Types Guide

## Why Database Types Matter?

Different databases solve different problems.

Choosing the wrong database can impact:

- Scalability
- Performance
- Reliability
- Cost
- Development Speed

Database selection depends on workload patterns.

Understanding database types is important for:

- System Design Interviews
- Distributed Systems
- Production Architecture
- Scalability Design

---

## Relational Database (SQL)

Relational databases store structured data using tables.

Examples:

- PostgreSQL
- MySQL
- Oracle

Best For:

- Banking Systems
- Payment Platforms
- Order Systems
- Inventory Systems

Pros:

- Strong consistency
- ACID transactions
- Complex query support
- Mature ecosystem

Cons:

- Horizontal scaling harder
- Schema changes slower

Example:

```text
Users Table
Orders Table
Payments Table
```

Interview Shortcut:

```text
SQL
→ Transactions + Consistency
```

---

## Key Value Database

Stores data as:

```text
Key → Value
```

Examples:

- Redis
- DynamoDB

Best For:

- Cache Layer
- Session Store
- Shopping Cart
- Rate Limiter

Pros:

- Very fast
- Easy scaling
- Low latency

Cons:

- Limited query capability
- Poor relationship handling

Example:

```text
User123
↓
Profile Data
```

Interview Shortcut:

```text
Key Value
→ Speed
```

---

## Document Database

Stores JSON like documents.

Examples:

- MongoDB
- Couchbase

Best For:

- Product Catalog
- CMS Platform
- User Profile System

Pros:

- Flexible schema
- Faster development
- Easy schema evolution

Cons:

- Complex joins harder
- Data duplication possible

Example:

```json
{
 "name":"Phone",
 "price":1000
}
```

Interview Shortcut:

```text
Document Database
→ Flexible Schema
```

---

## Wide Column Database

Optimized for distributed scale and write throughput.

Examples:

- Cassandra
- HBase

Best For:

- Analytics Systems
- Time Series Data
- Event Data
- Logging Systems

Pros:

- Massive write scalability
- Distributed by design
- High throughput

Cons:

- Query flexibility lower
- Operational complexity

Interview Shortcut:

```text
Wide Column
→ Large Scale Writes
```

---

## Graph Database

Optimized for relationship queries.

Examples:

- Neo4j

Best For:

- Social Graph
- Recommendation System
- Fraud Detection

Pros:

- Excellent relationship queries
- Graph traversal performance

Cons:

- Horizontal scaling harder
- Less suitable for transactional workload

Example:

```text
User A
 ↓
Friend
 ↓
User B
```

Interview Shortcut:

```text
Graph
→ Relationships
```

---

## Quick Database Mapping

| Use Case | Recommended Database |
|-----------|----------------------|
| Banking | PostgreSQL |
| Cache | Redis |
| Product Catalog | MongoDB |
| Analytics | Cassandra |
| Session Store | Redis |
| Social Graph | Neo4j |
| Recommendation System | Neo4j + Redis |

---

## Interview Questions

1. SQL vs NoSQL?

2. Why Redis is fast?

3. Cassandra vs PostgreSQL?

4. MongoDB vs PostgreSQL?

5. When should graph database be used?

6. Which database works best for recommendation systems?

---

## Quick Revision

- SQL → Transactions + Consistency
- Key Value → Speed
- Document → Flexible Schema
- Wide Column → Scale + Write Throughput
- Graph → Relationships
- Database choice depends on workload
- Database selection is common in interviews