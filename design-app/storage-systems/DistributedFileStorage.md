# Distributed File Storage System Design

## Problem Statement

Design a distributed file storage system like Google Drive, HDFS or Dropbox backend that supports large file upload, chunk storage, replication and reliable retrieval at massive scale.

System should support:

- File Upload
- File Download
- Chunk Storage
- Replication
- Metadata Management
- File Sharing
- Fault Tolerance
- Data Recovery

---

## Functional Requirements

### Core Features

- Upload file
- Download file
- Delete file
- File sharing
- File metadata retrieval
- Chunk large files
- Replicate data
- Recover failed storage node

---

## Non Functional Requirements

### Scalability

- Billions of files
- Petabyte scale storage

### Availability

- 99.99% uptime

### Reliability

- No file loss

### Durability

- Multi copy storage

### Latency

- Fast upload and download

---

## Capacity Estimation

Assume:

- 200 Million users
- 1 Billion files
- Average file size: 10 MB

Storage:

1B × 10 MB

≈ 10 PB storage

Replication Factor:

3 Copies

Total:

≈ 30 PB storage

---

## API Design

### Upload File

```http
POST /files
```

### Download File

```http
GET /files/{fileId}
```

### Delete File

```http
DELETE /files/{fileId}
```

---

## Database Design

### File Metadata Table

| Field | Type |
|--------|-------|
| file_id | UUID |
| owner_id | UUID |
| file_name | String |
| size | Integer |
| created_at | Timestamp |

### Chunk Table

| Field | Type |
|--------|-------|
| chunk_id | UUID |
| file_id | UUID |
| storage_node | String |
| replica_count | Integer |

---

## High Level Design

```text
Client
 |
Load Balancer
 |
API Gateway
 |
Metadata Service
 |
Redis Cache
 |
Metadata Database
 |
Chunk Service
 |
Storage Nodes
 |
Replication Service

Kafka
 |
Analytics + Recovery
```

---

## Core Components

### Metadata Service

Responsibilities:

- File metadata storage
- Chunk location mapping
- Ownership validation

### Chunk Service

Responsibilities:

- Split large file
- Chunk allocation
- Chunk retrieval

Example:

100 MB File

```text
Chunk 1 → 25 MB
Chunk 2 → 25 MB
Chunk 3 → 25 MB
Chunk 4 → 25 MB
```

### Replication Service

Responsibilities:

- Data replication
- Failure recovery
- Replica balancing

### Storage Nodes

Responsibilities:

- Chunk persistence
- Chunk retrieval
- Node health reporting

---

## Upload Flow

```text
Upload File
 ↓
Chunk Split
 ↓
Metadata Store
 ↓
Chunk Distribution
 ↓
Replication
 ↓
Success
```

---

## Scaling Strategy

### Database

- Sharding
- Read replica

### Cache

Redis:

- Metadata cache
- Chunk location cache

### Queue

Kafka:

- Recovery workflow
- Analytics event

---

## Reliability

Strategies:

- Replication factor 3
- Multi region backup
- Checksum validation
- Node recovery

---

## Bottlenecks

| Problem | Solution |
|----------|-----------|
| Large upload traffic | Chunk upload |
| Node failure | Replication |
| Metadata overload | Redis cache |
| Hot files | CDN cache |

---

## Tradeoffs

| Choice | Benefit | Drawback |
|---------|----------|-----------|
| More replication | Better durability | Higher storage cost |
| Large chunk size | Lower metadata cost | Slower recovery |

---

## Interview Questions

1. Why chunking needed?
2. Why replication important?
3. How metadata scales?
4. How node failure handled?
5. Why checksum validation useful?
6. How hot file traffic handled?

---

## Quick Revision

- Metadata stores file mapping
- Chunking improves scalability
- Replication improves durability
- Redis improves metadata latency
- Kafka handles recovery workflow
- Checksum prevents corruption