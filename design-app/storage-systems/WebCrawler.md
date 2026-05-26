

# Web Crawler System Design

## Problem Statement

Design a web crawler like Google crawler.

Features:

- Crawl Web Pages
- Discover New URLs
- Store Crawled Data
- Remove Duplicate URLs
- Handle Large Scale Crawling

Examples:

- Google Search Crawler
- Bing Crawler

---

## Clarifying Questions

Interview starts here.

Questions:

1. Maximum pages to crawl?

2. Real time crawling needed?

3. Duplicate page handling needed?

4. File types?

- HTML
- PDF
- Images

5. Crawl frequency?

---

## Functional Requirements

System should support:

1. URL Discovery

2. Page Crawling

3. Content Extraction

4. Duplicate Detection

5. URL Scheduling

6. Store Crawled Data

---

## Non Functional Requirements

- Scalability
- Reliability
- Fault Tolerance
- High Throughput
- Low Latency

Interview Focus:

```text
Distributed Crawling
+ 
Duplicate Detection
```

---

## Capacity Estimation

Assume:

```text
1 Billion Pages
```

Assume:

```text
10 KB Average Page Metadata
```

Crawler System Focus:

```text
Massive Scale Processing
```

---

## High Level Design

```text
URL Scheduler

↓

Crawler Worker

↓

HTML Parser

↓

Duplicate Checker

↓

Storage
```

Supporting Services:

```text
Redis

Kafka

Distributed Storage
```

---

## URL Scheduler

Interview Focus Topic.

Responsibilities:

- Prioritize URLs
- Retry Failed URLs
- Avoid Duplicate Crawl

Example:

```text
Priority Queue
```

---

## Duplicate Detection

Problem:

```text
Same URL Multiple Times
```

Solution:

```text
Bloom Filter
```

Benefits:

- Fast lookup
- Memory efficient

Interview Tip:

Bloom Filter asked frequently.

---

## HTML Parsing

Responsibilities:

- Extract Links
- Extract Metadata
- Discover New URLs

Flow:

```text
HTML

↓

Parser

↓

Extract Links
```

---

## Scaling Strategy

Crawler Scaling:

- Multiple Workers
- Distributed Queue

Storage Scaling:

- Partitioning
- Replication

Messaging:

- Kafka

---

## Cache Strategy

Use:

```text
Redis
```

Cache:

- URL Metadata
- Crawl State

---

## Bottleneck

Problems:

- Duplicate crawling
- Slow website response
- Queue backlog

Solutions:

- Bloom Filter
- Retry Mechanism
- Distributed Worker

---

## Interview Questions

### Q1. Biggest crawler challenge?

Duplicate handling.

---

### Q2. Why Bloom Filter?

Fast duplicate detection.

---

### Q3. Why Kafka used?

Distributed processing.

---

## Quick Revision

- WebCrawler → Distributed system
- Bloom Filter → Duplicate detection
- Scheduler → URL priority
- Kafka → Worker communication
- Redis → Crawl metadata cache
- Parser → Extract links