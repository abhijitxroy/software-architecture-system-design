

# Database Indexing

## Why Database Indexing Matters?

Database indexing improves query performance.

Without indexing:

```text
Database
↓
Full Table Scan
↓
Higher Latency
↓
Slow Application
```

Production systems use indexing to reduce query execution time.

Understanding indexing is important for:

- System Design Interviews
- Backend Development
- Database Optimization
- Production Systems

---

## What Is Database Index?

Database index is a data structure that improves data lookup speed.

Example:

Without Index:

```text
Find User ID = 1000000
↓
Scan Entire Table
```

With Index:

```text
Find User ID = 1000000
↓
Direct Lookup
```

Goal:

```text
Faster Reads
Lower Query Latency
```

---

## B Tree Index

Most relational databases commonly use B Tree indexes.

Example:

```text
10
↓
5    20
↓    ↓
2 8 15 25
```

Best For:

- Equality Search
- Range Query
- Sorting

Examples:

```sql
SELECT * FROM users
WHERE id = 100;
```

Pros:

- Fast lookup
- Supports sorting
- Supports range queries

Cons:

- Storage overhead
- Write overhead

---

## Hash Index

Hash index uses hash functions.

Goal:

```text
Fast Equality Lookup
```

Example:

```sql
SELECT * FROM users
WHERE email='user@example.com';
```

Best For:

- Exact match search

Pros:

- Very fast lookup

Cons:

- Range query not supported

---

## Composite Index

Single index across multiple columns.

Example:

```text
(first_name,last_name)
```

Query:

```sql
SELECT *
FROM users
WHERE first_name='John'
AND last_name='Smith';
```

Best For:

- Multi column filtering

---

## Index Tradeoff

Benefits:

- Faster read queries
- Lower latency
- Better application performance

Problems:

- Extra storage
- Slower writes
- More maintenance

Rule:

```text
More Index
↓
Faster Read
↓
Slower Write
```

---

## Production Example

E Commerce:

Query:

```sql
SELECT *
FROM products
WHERE category='Phone';
```

Index:

```text
category
```

Social Platform:

Query:

```sql
SELECT *
FROM posts
WHERE user_id=100;
```

Index:

```text
user_id
```

---

## Production Strategy

Index:

- Frequently queried columns
- WHERE clause columns
- JOIN columns
- ORDER BY columns

Avoid:

- Over indexing
- Indexing every column

---

## Interview Shortcut

Remember:

```text
Index
→ Faster Read

Too Many Indexes
→ Slower Write
```

---

## Interview Questions

1. Why indexing matters?

2. B Tree vs Hash Index?

3. Composite index use case?

4. Why indexes slow writes?

5. Which columns should be indexed?

6. Why not index every column?

---

## Quick Revision

- Index improves query speed
- B Tree supports range queries
- Hash index supports exact lookup
- Composite index supports multi column query
- Index improves reads
- Index increases write overhead
- Index optimization is common interview topic