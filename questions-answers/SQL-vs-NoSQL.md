

# SQL vs NoSQL

## Why This Comparison Matters?

SQL and NoSQL databases solve different problems.

System design interviews frequently ask when SQL works better and when NoSQL becomes necessary.

Choosing the wrong database can create:

- Scalability problems
- Query performance issues
- Higher infrastructure cost
- Development complexity
- Reliability limitations

Understanding database choices is important for:

- System Design Interviews
- Database Design
- Distributed Systems
- Production Architecture

---

## SQL Database

SQL databases store structured data using tables.

Example:

```text
Users Table

ID | Name | Email
```

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

- ACID transactions
- Strong consistency
- Complex query support
- Mature ecosystem

Cons:

- Horizontal scaling harder
- Schema changes slower

---

## NoSQL Database

NoSQL databases support flexible data models.

Types:

```text
Key Value
Document
Wide Column
Graph
```

Examples:

- MongoDB
- Cassandra
- Redis
- DynamoDB

Best For:

- Social Platforms
- Analytics Systems
- Event Platforms
- Large Scale Systems

Pros:

- Horizontal scaling
- Flexible schema
- High throughput
- Better distributed scaling

Cons:

- Complex joins harder
- Consistency tradeoffs possible
- Query capability varies

---

## Key Differences

| Feature | SQL | NoSQL |
|----------|-----|--------|
| Schema | Fixed | Flexible |
| Scaling | Vertical | Horizontal |
| Transaction Support | Strong | Limited / Depends |
| Consistency | Strong | Eventual Possible |
| Query Capability | Strong | Varies |
| Large Scale Distribution | Harder | Better |
| Best For | Transactions | Scale |

---

## Production Example

Banking Platform:

```text
Need Correct Data
Need Transactions
```

Choose:

```text
SQL
```

Social Feed Platform:

```text
Massive Traffic
Large Scale Writes
```

Choose:

```text
NoSQL
```

---

## Production Reality

Large systems commonly use both.

Example:

```text
PostgreSQL
↓
Orders + Payments

Redis
↓
Cache Layer

Cassandra
↓
Analytics
```

---

## Interview Shortcut

Remember:

```text
SQL
→ Transactions + Correctness

NoSQL
→ Scale + Flexibility
```

---

## Interview Questions

1. SQL vs NoSQL?

2. Why SQL supports transactions better?

3. Why NoSQL scales horizontally?

4. Banking system database choice?

5. Social feed database choice?

6. Why production systems commonly use both?

---

## Quick Revision

- SQL focuses on transactions
- SQL provides strong consistency
- NoSQL improves scalability
- NoSQL supports flexible schema
- SQL commonly powers banking systems
- NoSQL commonly powers large distributed systems
- Database choice depends on workload