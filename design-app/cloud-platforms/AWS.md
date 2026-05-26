# AWS Cloud Platform Design

## Problem Statement

Understand AWS cloud architecture and how core AWS services work together to build scalable, reliable and highly available distributed systems.

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

#### EC2

Purpose:

- Virtual machine service
- Run applications
- Auto scaling workload

Interview Focus:

- Auto Scaling Group
- Launch Template
- Load Balancer

---

#### Lambda

Purpose:

- Serverless execution
- Event driven processing
- Background jobs

Examples:

- Image processing
- Event pipeline
- API backend

---

#### ECS / EKS

Purpose:

- Container orchestration
- Microservice deployment

Interview Focus:

- ECS vs EKS
- Container scaling

---

## Storage Layer

### S3

Purpose:

- Object storage
- Backup
- Static website hosting

Features:

- Versioning
- Lifecycle Policy
- Cross Region Replication

Interview Focus:

- Durability
- Availability

---

### EBS

Purpose:

- Persistent block storage

Example:

- Database disk
- EC2 storage

---

### EFS

Purpose:

- Shared file storage

Use Case:

- Multiple EC2 shared filesystem

---

## Database Layer

### RDS

Purpose:

- Managed relational database

Examples:

- MySQL
- PostgreSQL

Interview Focus:

- Multi AZ
- Read Replica

---

### DynamoDB

Purpose:

- NoSQL database
- Key value storage

Features:

- Partition Key
- Global Secondary Index
- Auto Scaling

---

### ElastiCache

Purpose:

- Redis cache
- Memcached

Use Case:

- Reduce DB latency

---

## Networking

### VPC

Concepts:

- Public subnet
- Private subnet
- NAT Gateway
- Internet Gateway

---

### CloudFront

Purpose:

- CDN
- Global content delivery

---

### Route53

Purpose:

- DNS management
- Traffic routing

---

## Security

Core Services:

- IAM
- Security Group
- KMS
- Secrets Manager

Interview Focus:

- Least privilege access
- Encryption at rest
- Encryption in transit

---

## Monitoring

### CloudWatch

Purpose:

- Metrics
- Logging
- Alerting

### CloudTrail

Purpose:

- API audit logging

---

## High Level Architecture

```text
User
 |
Route53
 |
CloudFront
 |
Load Balancer
 |
EC2 / ECS / EKS
 |
Redis Cache
 |
RDS / DynamoDB
 |
S3

CloudWatch
 |
Monitoring
```

---

## Scaling Strategy

Compute:

- Auto Scaling Group
- Horizontal scaling

Database:

- Read replica
- Cache layer

Storage:

- CDN
- Multi region replication

---

## Reliability

Strategies:

- Multi AZ deployment
- Backup
- Disaster recovery
- Cross region replication

---

## Tradeoffs

| Choice | Benefit | Drawback |
|---------|----------|-----------|
| EC2 | Flexibility | Infrastructure management |
| Lambda | Less operations | Cold start |
| RDS | Managed DB | Higher cost |
| DynamoDB | Massive scale | Query limitation |

---

## Interview Questions

1. EC2 vs Lambda?
2. RDS vs DynamoDB?
3. Why CloudFront needed?
4. Multi AZ vs Read Replica?
5. Why ElastiCache useful?
6. How AWS achieves high availability?

---

## Quick Revision

- EC2 runs compute workload
- S3 provides object storage
- RDS provides relational DB
- DynamoDB provides NoSQL scale
- CloudFront reduces latency
- CloudWatch improves observability
