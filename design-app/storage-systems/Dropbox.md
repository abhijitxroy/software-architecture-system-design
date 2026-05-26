# Dropbox System Design

## Problem Statement

Design a cloud storage platform like Dropbox.

Features:

- Upload File
- Download File
- File Sharing
- File Sync
- Multi Device Access
- File Versioning

Examples:

- Dropbox
- Google Drive
- OneDrive

---

## Functional Requirements

System should support:

1. Upload File

2. Download File

3. Sync Files Across Devices

4. Share Files

5. Delete Files

6. File Version History

7. Search Files

---

## Non Functional Requirements

- High Availability
- Scalability
- Reliability
- Durability
- Low Latency

Interview Tip:

Dropbox interviews focus heavily on:

```text
File Sync
+
Storage Optimization
```

---

## Capacity Estimation

Assume:

```text
100 Million Users
```

Assume:

```text
1 GB Average Storage / User
```

Storage Needed:

```text
100 PB+
```

Interview Tip:

Storage systems focus heavily on:

```text
Durability
```

---

## API Design

Upload File:

```text
POST /file/upload
```

Download File:

```text
GET /file/{fileId}
```

Share File:

```text
POST /file/share
```

---

## Database Design

User Table:

| UserId | Name |
|--------|------|
| U101 | Roy |

File Table:

| FileId | UserId | FileName |
|--------|--------|----------|
| F101 | U101 | notes.pdf |

Metadata Database:

Common:

- MySQL
- PostgreSQL

Blob Storage:

- S3
- HDFS

---

## High Level Design

```text
Client

↓

Load Balancer

↓

API Service

↓

Metadata Database

↓

Blob Storage
```

Supporting Services:

```text
Kafka

Redis

CDN
```

---

## File Upload Flow

```text
Client

↓

Upload API

↓

Metadata Save

↓

Blob Storage
```

---

## File Sync

Interview Focus Topic.

Problem:

```text
Same File

Multiple Devices
```

Solution:

```text
Change Detection

↓

Sync Engine

↓

Device Update
```

---

## Chunking

Large files split into chunks.

Example:

```text
2 GB File

↓

100 MB Chunks
```

Benefits:

- Faster upload
- Retry failed chunk only

---

## Deduplication

Interview Focus Topic.

Problem:

Multiple users upload same file.

Solution:

```text
Hash File

↓

Reuse Existing Copy
```

Benefits:

- Storage saving
- Lower cost

---

## Cache Strategy

Use:

```text
Redis
```

Cache:

- Metadata
- Recent Files

---

## Scaling Strategy

Storage:

- Replication
- Partitioning

Application:

- Horizontal Scaling

Messaging:

- Kafka

---

## Bottleneck

Problems:

- Large upload spike
- Sync pressure
- Storage growth

Solutions:

- CDN
- Chunk Upload
- Replication

---

## Interview Questions

### Q1. Why chunking used?

Improve upload reliability.

---

### Q2. Why deduplication used?

Reduce storage usage.

---

### Q3. Biggest Dropbox challenge?

File synchronization.

---

## Quick Revision

- Dropbox → Storage system
- Chunking → Large file handling
- Deduplication → Storage optimization
- Blob Storage → File storage
- Redis → Metadata cache
- Sync Engine → Multi device consistency