

# RAG Pipeline System Design

## Problem Statement

Design a Retrieval Augmented Generation (RAG) pipeline that improves LLM responses using enterprise documents and external knowledge.

Used in:

- Enterprise Chatbot
- AI Search
- Customer Support Bot
- Internal Knowledge Assistant
- Documentation Assistant
- AI Agent Platform

System should support:

- Document Ingestion
- Chunking
- Embedding Generation
- Vector Retrieval
- Metadata Filtering
- Context Injection
- LLM Response Generation
- Feedback Loop

---

## Functional Requirements

### Core Features

- Upload documents
- Chunk documents
- Generate embeddings
- Similarity retrieval
- Metadata filtering
- Top K retrieval
- Context generation
- Response generation

---

## Non Functional Requirements

### Scalability

- Millions of documents
- Thousands of queries/sec

### Availability

- 99.99% uptime

### Reliability

- No document loss

### Latency

- Response under 2 seconds

---

## Why RAG Needed

Without RAG:

```text
User Question
↓
LLM
↓
Possible Hallucination
```

Problems:

- Hallucination
- Outdated knowledge
- Missing enterprise context

Goal:

```text
Retrieve Context
+
Ground LLM Response
```

---

## Core Concepts

### Chunking

Large document:

```text
500 Page PDF
```

Problem:

```text
Too large for context window
```

Solution:

```text
Split Document
↓
Smaller Chunks
```

Chunk Size Example:

```text
500 Tokens
Overlap 50 Tokens
```

---

### Embedding

Convert:

```text
Text
↓
Vector Representation
```

Example:

```text
"Kubernetes deployment"
↓
[0.23,0.55,0.90]
```

Purpose:

Semantic search.

---

### Vector Search

Flow:

```text
Question
↓
Embedding Model
↓
Vector Search
↓
Top K Similar Chunks
```

Search Types:

- Cosine Similarity
- ANN Search
- HNSW

---

### Metadata Filtering

Example:

```text
Team = Platform
Year = 2026
Region = India
```

Purpose:

Reduce irrelevant retrieval.

---

## RAG Pipeline Flow

```text
PDF
Wiki
Confluence
Database
↓
Document Ingestion
↓
Chunking
↓
Embedding Model
↓
Vector Database
↓
User Query
↓
Embedding Generation
↓
Similarity Search
↓
Top K Retrieval
↓
Prompt Construction
↓
LLM
↓
Final Response
```

---

## High Level Design

```text
Client
 |
Query API
 |
Embedding Service
 |
Vector Database
 |
Retriever Service
 |
Prompt Builder
 |
LLM Gateway
 |
Response Service
```

---

## Retrieval Flow

```text
Question
↓
Embedding
↓
ANN Search
↓
Metadata Filter
↓
Top K Chunks
↓
Prompt Builder
↓
LLM
```

---

## Ranking Strategy

Signals:

- Similarity score
- Metadata match
- Freshness
- Source priority

Example:

```text
Engineering Wiki
Priority = High
```

---

## Scaling Strategy

### Vector Database

Responsibilities:

- Similarity retrieval
- ANN indexing

### Cache

Redis:

- Query cache
- Embedding cache

### Partitioning

Partition by:

```text
Namespace
Tenant
```

---

## Reliability

Strategies:

- Retry mechanism
- Multi region deployment
- Embedding cache
- Retrieval fallback

---

## Tradeoffs

| Choice | Benefit | Drawback |
|----------|----------|-----------|
| Large chunk | More context | Lower retrieval precision |
| Small chunk | Better retrieval | Higher retrieval count |
| Top K large | More information | Larger prompt cost |

---

## Interview Questions

1. Why RAG needed?
2. Why chunk overlap needed?
3. ANN vs Full Search?
4. Why metadata filtering useful?
5. Why embeddings needed?
6. Hallucination vs retrieval issue?

---

## Quick Revision

- RAG reduces hallucination
- Chunking improves retrieval
- Embeddings enable semantic search
- Vector DB powers retrieval
- Metadata filtering improves relevance
- Prompt construction grounds LLM