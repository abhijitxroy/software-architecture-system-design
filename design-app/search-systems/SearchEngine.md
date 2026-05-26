

# Search Engine System Design

## Problem Statement

Design a search engine like Google Search that can crawl web pages, index content and return relevant search results with low latency.

System should support:

- Web Crawling
- Indexing
- Ranking
- Query Processing
- Search Suggestions
- Spell Correction
- Result Retrieval

---

## Functional Requirements

### Core Features

- Crawl internet pages
- Store crawled pages
- Build searchable index
- Support keyword search
- Rank search results
- Auto complete suggestions
- Spell correction
- Show top relevant pages

---

## Non Functional Requirements

### Scalability

- Billions of pages
- Millions of search requests

### Availability

- 99.99% uptime

### Reliability

- Accurate indexing

### Latency

- Search response under 200 ms

---

## Capacity Estimation

Assume:

- 5 Billion pages
- Average page size: 500 KB
- 100 Million search/day

Storage:

5B × 500 KB

≈ Petabyte scale storage

---

## API Design

### Search API

```http
GET /search?q=system+design
```

Response:

```json
{
  "results":[
    {
      "title":"System Design Guide",
      "url":"example.com"
    }
  ]
}
```

---

### Suggestion API

```http
GET /suggest?q=sys
```

---

## Database Design

### Crawled Page

| Field | Type |
|--------|-------|
| page_id | UUID |
| url | String |
| content | Text |
| crawl_time | Timestamp |

### Inverted Index

| Keyword | Document IDs |
|----------|---------------|
| cache | 1,5,8 |
| kafka | 2,7 |

---

## High Level Design

```text
User
 |
Load Balancer
 |
Search API
 |
Query Processor
 |
+-------------+
| Cache Redis |
+-------------+
 |
Indexer
 |
Inverted Index
 |
Document Store

Crawler Service
 |
URL Frontier Queue
 |
Page Downloader
 |
Parser
```

---

## Core Components

### Web Crawler

Responsibilities:

- Discover pages
- Download pages
- Avoid duplicate crawling

Techniques:

- BFS crawling
- Robots.txt support
- Rate limiting

### URL Frontier

Maintains:

- Pending URLs
- Crawl priority

### Parser

Responsibilities:

- HTML parsing
- Metadata extraction
- Link extraction

### Indexer

Responsibilities:

- Build inverted index
- Update search index

### Query Processor

Responsibilities:

- Parse query
- Fetch relevant documents
- Ranking

---

## Ranking System

Factors:

- TF-IDF
- Page Rank
- Freshness
- Click signals

---

## Search Optimization

### Cache

Redis:

- Hot query cache
- Search suggestion cache

### Sharding

Shard index by:

- Keyword range
- Document partition

### Replication

Improve:

- Availability
- Read scalability

---

## Reliability

Strategies:

- Retry crawling
- Replication
- Queue retry
- Dead letter queue

---

## Bottlenecks

| Problem | Solution |
|----------|-----------|
| Slow ranking | Cache hot results |
| Crawl overload | Rate limit crawler |
| Large index | Sharding |
| Duplicate crawl | URL deduplication |

---

## Tradeoffs

| Choice | Benefit | Drawback |
|---------|----------|-----------|
| Aggressive cache | Faster response | Stale results |
| Frequent crawling | Fresh results | Higher cost |

---

## Interview Questions

1. Why inverted index is important?
2. How ranking works?
3. How duplicate crawling prevented?
4. Why cache search result?
5. How crawler scales?
6. Why sharding needed?

---

## Quick Revision

- Inverted index powers fast search
- Cache reduces latency
- Crawler discovers pages
- Ranking improves relevance
- Sharding improves scalability
- Replication improves availability