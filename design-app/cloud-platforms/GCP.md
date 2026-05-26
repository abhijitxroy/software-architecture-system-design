# GCP Cloud Platform Design

## Problem Statement

Understand Google Cloud Platform (GCP) architecture and how GCP services work together to build scalable, reliable and distributed systems.

Coverage:

- Compute Services
- Storage Services
- Database Services
- Networking
- Monitoring
- Security
- Scaling
- Disaster Recovery

---

## Core Services

### Compute Layer

#### Compute Engine

Purpose:

- Virtual machine service
- Infrastructure hosting
- Application deployment

Interview Focus:

- Managed Instance Group
- Auto Scaling
- Load Balancing

---

#### Cloud Functions

Purpose:

- Serverless execution
- Event driven processing
- Background jobs

Examples:

- API backend
- File processing
- Event handling

---

#### GKE (Google Kubernetes Engine)

Purpose:

- Kubernetes orchestration
- Container deployment
- Microservice platform

Interview Focus:

- Node Pool
- Auto Scaling
- Container orchestration

---

## Storage Layer

### Cloud Storage

Purpose:

- Object storage
- Backup
- Static content storage

Storage Classes:

- Standard
- Nearline
- Coldline
- Archive

Interview Focus:

- Durability
- Lifecycle policy

---

### Persistent Disk

Purpose:

- VM block storage

Examples:

- Database storage
- VM persistent volume

---

### Filestore

Purpose:

- Managed file storage

Use Case:

- Shared filesystem

---

## Database Layer

### Cloud SQL

Purpose:

- Managed relational database

Examples:

- MySQL
- PostgreSQL

Interview Focus:

- High Availability
- Read Replica

---

### Bigtable

Purpose:

- Large scale NoSQL database

Use Case:

- Time series workload
- Massive analytical workload

---

### Firestore

Purpose:

- Document database

Features:

- Real time sync
- Serverless scale

---

### Memorystore

Purpose:

- Redis cache

Use Case:

- Reduce database latency

---

## Networking

### VPC

Concepts:

- Subnet
- Firewall Rule
- Private Connectivity
- Load Balancer

---

### Cloud CDN

Purpose:

- Content delivery
- Global acceleration

---

### Cloud DNS

Purpose:

- DNS hosting
- Traffic routing

---

## Security

Core Services:

- IAM
- Secret Manager
- Cloud Armor
- KMS

Interview Focus:

- Least privilege
- Encryption
- Identity management

---

## Monitoring

### Cloud Monitoring

Purpose:

- Metrics
- Alerting
- Dashboard

### Cloud Logging

Purpose:

- Log aggregation
- Debugging

---

## Data Analytics

### Pub/Sub

Purpose:

- Event streaming
- Messaging system

### BigQuery

Purpose:

- Analytics warehouse

Interview Focus:

- Large scale analytics
- OLAP workload

---

## High Level Architecture

```text
User
 |
Cloud DNS
 |
Cloud CDN
 |
Load Balancer
 |
Compute Engine / GKE / Cloud Functions
 |
Redis Cache
 |
Cloud SQL / Firestore / Bigtable
 |
Cloud Storage

Cloud Monitoring
 |
Observability
