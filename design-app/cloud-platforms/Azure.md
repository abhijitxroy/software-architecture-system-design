

# Azure Cloud Platform Design

## Problem Statement

Understand Microsoft Azure cloud architecture and how Azure services work together to build scalable, reliable and enterprise grade distributed systems.

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

#### Virtual Machines (VM)

Purpose:

- Virtual server hosting
- Application deployment
- Custom infrastructure management

Interview Focus:

- Availability Set
- Availability Zone
- VM Scale Set

---

#### Azure Functions

Purpose:

- Serverless execution
- Event driven processing
- Automation workflow

Examples:

- API backend
- File processing
- Queue consumer

---

#### AKS (Azure Kubernetes Service)

Purpose:

- Kubernetes orchestration
- Container deployment
- Microservice platform

Interview Focus:

- AKS scaling
- Node pool
- Container orchestration

---

## Storage Layer

### Blob Storage

Purpose:

- Object storage
- Backup storage
- Media storage

Features:

- Lifecycle policy
- Geo replication
- Tiered storage

Interview Focus:

- Hot tier
- Cool tier
- Archive tier

---

### Azure Disk Storage

Purpose:

- Persistent block storage

Examples:

- Database disk
- VM storage

---

### Azure Files

Purpose:

- Shared file storage

Use Case:

- Shared filesystem across services

---

## Database Layer

### Azure SQL Database

Purpose:

- Managed relational database

Examples:

- SQL workload
- Enterprise application

Interview Focus:

- Geo replication
- High availability

---

### Cosmos DB

Purpose:

- Globally distributed NoSQL database

Features:

- Multi region replication
- Multiple consistency levels
- Automatic scaling

Consistency Models:

- Strong
- Bounded Staleness
- Session
- Consistent Prefix
- Eventual

---

### Azure Cache for Redis

Purpose:

- Caching layer

Use Case:

- Reduce database latency

---

## Networking

### Virtual Network (VNet)

Concepts:

- Subnet
- Network Security Group
- Peering
- Private Endpoint

---

### Azure Front Door

Purpose:

- Global traffic routing
- CDN capability
- Application acceleration

---

### Azure DNS

Purpose:

- DNS hosting
- Traffic routing

---

## Security

Core Services:

- Azure Active Directory
- Key Vault
- Managed Identity
- Defender for Cloud

Interview Focus:

- RBAC
- Least privilege
- Secret management

---

## Monitoring

### Azure Monitor

Purpose:

- Metrics
- Logs
- Alerting

### Application Insights

Purpose:

- Application telemetry
- Performance monitoring

---

## High Level Architecture

```text
User
 |
Azure DNS
 |
Azure Front Door
 |
Load Balancer
 |
VM / AKS / Azure Functions
 |
Redis Cache
 |
Azure SQL / Cosmos DB
 |
Blob Storage

Azure Monitor
 |
Observability
```

---

## Scaling Strategy

Compute:

- VM Scale Set
- Horizontal scaling

Database:

- Read scaling
- Cache layer

Storage:

- Geo replication
- CDN optimization

---

## Reliability

Strategies:

- Availability Zone
- Backup
- Geo redundancy
- Disaster recovery

---

## Tradeoffs

| Choice | Benefit | Drawback |
|---------|----------|-----------|
| VM | Flexibility | Infrastructure management |
| Azure Functions | Less operations | Cold start |
| Azure SQL | Managed relational DB | Higher cost |
| Cosmos DB | Global scale | Higher pricing |

---

## Interview Questions

1. VM vs Azure Functions?
2. Azure SQL vs Cosmos DB?
3. Why Cosmos DB consistency model important?
4. Availability Set vs Availability Zone?
5. Why Redis useful?
6. How Azure achieves high availability?

---

## Quick Revision

- VM runs compute workload
- Blob Storage stores objects
- Azure SQL manages relational data
- Cosmos DB enables global NoSQL scale
- Front Door improves global performance
- Azure Monitor improves observability