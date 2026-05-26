

# Vector Database System Design

## Problem Statement

Design a vector database that stores embeddings and performs semantic similarity search for AI applications like RAG systems, recommendation systems and semantic search.

Used in:

- RAG Applications
- Chatbot Memory
- Semantic Search
- Recommendation Systems
- Image Search
- Document Retrieval

System should support:

- Embedding Storage
- Similarity Search
- Metadata Filtering
- Vector Indexing
- High Throughput Query
- Large Scale Retrieval

---

## Functional Requirements

### Core Features

- Store embeddings
- Query similar vectors
- Metadata filtering
- Delete vector
- Update embedding
- Top K retrieval
- Namespace isolation
- Batch insertion

---

## Non Functional Requirements

### Scalability

- Billions of vectors
- Millions of queries/day

### Availability

- 99.99% uptime

### Reliability

- No embedding loss

### Latency

- Query under 100 ms

---

## Capacity Estimation

Assume:

- 500 Million embeddings
- Vector dimension: 1536
- Float32 storage

Single vector:

```text
1536 × 4 Bytes
≈ 6 KB
```

Storage:

```text
500M × 6 KB
≈ Multi TB storage
```

---

## API Design

### Insert Embedding

```http
POST /vectors
```

Request:

```json
{
 "id":"doc123",
 "embedding":[0.11,0.21,0.32],
 "metadata":{
   "team":"backend"
 }
}
```

### Query Similar Vectors

```http
POST /query
```

Request:

```json
{
 "topK":5,
 "embedding":[0.1,0.2,0.3]
}
```

---

## Embedding Concept

Embedding converts:

```text
Text
Image
Audio
```

Into:

```text
High dimensional vectors
```

Example:

```text
"Apple phone"
↓
[0.21,0.55,0.90]
```

Goal:

Semantic similarity.

---

## Similarity Algorithms

### Cosine Similarity

Measures:

```text
Angle between vectors
```

Good for:

- Semantic search
- Embedding retrieval

### Euclidean Distance

Measures:

```text
Absolute distance
```

Good for:

- Spatial data

### Dot Product

Good for:

- Recommendation systems

---

## ANN Search

Full scan:

```text
O(N)
```

Problem:

Too expensive.

Solution:

```text
ANN
Approximate Nearest Neighbor
```

Benefits:

- Faster search
- Lower latency

Tradeoff:

```text
Small accuracy compromise
```

---

## HNSW

Hierarchical Navigable Small World.

Idea:

```text
Graph based index
```

Benefits:

- Very fast retrieval
- High recall

Used for:

```text
Large vector search systems
```

---

## IVF

Inverted File Index.

Flow:

```text
Vector
↓
Cluster Assignment
↓
Search Selected Cluster
↓
Retrieve Result
```

Benefits:

- Lower search cost
- Faster retrieval

---

## Metadata Filtering

Example:

```text
Search:
"Kubernetes deployment"

Filter:
Team=Backend
Year=2026
```

Purpose:

Reduce search space.

---

## RAG Pipeline

Flow:

```text
Document
↓
Chunking
↓
Embedding Model
↓
Vector Database
↓
Similarity Search
↓
Retrieved Context
↓
LLM
```

---

## High Level Design

```text
Client
 |
Embedding Service
 |
Vector API
 |
Metadata Service
 |
Vector Index
 |
Distributed Storage
 |
Query Engine
```

---

## Query Flow

```text
User Query
↓
Embedding Model
↓
ANN Search
↓
Metadata Filter
↓
Top K Results
↓
Return Context
```

---

## Scaling Strategy

### Partitioning

Partition vector index.

### Replication

Improve reliability.

### Cache

Hot embedding cache.

---

## Tradeoffs

| Choice | Benefit | Drawback |
|----------|----------|-----------|
| HNSW | Better recall | More memory |
| IVF | Faster search | Lower accuracy |
| Full Scan | Exact result | Very expensive |

---

## Interview Questions

1. Why ANN needed?
2. HNSW vs IVF?
3. Cosine similarity vs Euclidean?
4. Why metadata filtering needed?
5. Why chunking important?
6. Why vector database useful for RAG?

---

## Quick Revision

- Embedding converts data to vectors
- ANN improves retrieval speed
- HNSW uses graph indexing
- IVF uses cluster based retrieval
- Metadata filtering reduces search cost
- Vector DB powers RAG systems