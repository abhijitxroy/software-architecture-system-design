# Database Selection Guide

## Why Database Selection Matters?

Choosing the right database impacts:

- Scalability
- Reliability
- Query Performance
- Infrastructure Cost
- Development Speed
- Operational Complexity

No single database solves every problem.

Database choice depends on workload and system requirements.

---

## Step 1: Understand Access Pattern

Questions:

```text
Read Heavy?
Write Heavy?
Need Low Latency?
Need High Throughput?
Need Complex Query?
Need Strong Consistency?
```

Examples:

```text
Twitter Timeline
→ Read Heavy

Payment Platform
→ Consistency Heavy

Analytics Platform
→ Large Aggregation Query
```

---

## Step 2: SQL vs NoSQL

| Feature | SQL | NoSQL |
|----------|------|--------|
| Schema | Fixed | Flexible |
| Scaling | Vertical | Horizontal |
| Transactions | Strong | Limited |
| Query Capability | Strong | Moderate |
| Consistency | Strong | Eventual Possible |
| Best For | Transaction Systems | Large Scale Systems |
| Examples | PostgreSQL, MySQL | MongoDB, Cassandra, DynamoDB |

Use SQL when:

- Strong consistency required
- Complex joins required
- Financial systems
- Transaction systems

Use NoSQL when:

- Massive scale needed
- Flexible schema required
- Distributed systems
- High throughput workload

---

## Step 3: Database Type Selection

### Relational Database

Examples:

- PostgreSQL
- MySQL

Best for:

- Banking Systems
- Order Systems
- Payment Systems

---

### Key Value Database

Examples:

- Redis
- DynamoDB

Best for:

- Cache Layer
- Session Store
- Rate Limiter

---

### Document Database

Examples:

- MongoDB
- Couchbase

Best for:

- Product Catalog
- Content Platform
- Flexible Schema Data

---

### Wide Column Database

Examples:

- Cassandra
- HBase

Best for:

- Analytics Platform
- Time Series Data
- Large Scale Write Workload

---

### Graph Database

Examples:

- Neo4j

Best for:

- Social Network
- Fraud Detection
- Recommendation System

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

## Step 4: CAP Theorem Consideration

Priority selection:

```text
Consistency
Availability
Partition Tolerance
```

Examples:

```text
Banking Platform
→ Consistency

Social Feed
→ Availability
```

---

## Production Examples

| System | Database Choice |
|---------|-----------------|
| Payment Platform | PostgreSQL |
| Timeline System | Cassandra + Redis |
| Product Catalog | MongoDB |
| Recommendation System | Redis + Cassandra |
| Social Graph | Neo4j |

---

## Database Selection Checklist

Before choosing database:

- Read vs Write ratio
- Data growth expectation
- Query complexity
- Availability target
- Multi region requirement
- Operational complexity
- Consistency requirement
- Latency requirement

---

## Interview Shortcut

Remember:

```text
SQL
→ Transactions + Correctness

NoSQL
→ Scale + Flexibility

Redis
→ Speed

Cassandra
→ Large Scale Write
```

---

## Interview Questions

1. SQL vs NoSQL?

2. Database selection factors?

3. Cassandra vs PostgreSQL?

4. Why Redis is not primary database?

5. Banking database choice?

6. Social feed database choice?

---

## Quick Revision

- SQL focuses on consistency and transactions
- NoSQL focuses on scale and flexibility
- Redis improves latency
- Cassandra handles large write workload
- PostgreSQL is common for transaction systems
- Database choice depends on workload
- Banking commonly prefers SQL
- Social feed systems commonly use NoSQL + Cache
- Database selection is a common interview topic