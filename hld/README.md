# High Level Design (HLD)

## Purpose

High Level Design (HLD) explains system architecture and how major components work together to build scalable and reliable systems.

HLD focuses on:

- System components
- Data flow
- Scalability
- Availability
- Reliability
- Performance
- Failure handling

Interview Goal:

```text
Requirements
↓
Architecture
↓
Database
↓
Cache
↓
Scaling
↓
Reliability
↓
Tradeoffs
```

---

## Why HLD Matters?

Without HLD:

```text
Features Added

↓

System Complexity Increased

↓

Difficult Maintenance
```

Problems:

- Poor scalability
- Bottlenecks
- Single point of failure
- Hard troubleshooting

Benefits:

- Better scalability
- Better reliability
- Clear architecture understanding
- Easier system evolution

---

## HLD Building Blocks

Common components:

### Client

Examples:

- Web Application
- Mobile Application

---

### Load Balancer

Distributes traffic across servers.

Example:

```text
Users

↓

Load Balancer

↓

Backend Servers
```

---

### API Gateway

Single entry point for backend services.

Responsibilities:

- Authentication
- Routing
- Rate Limiting

---

### Application Servers

Business logic processing.

Examples:

- User Service
- Payment Service
- Order Service

---

### Database

Stores application data.

Examples:

- MySQL
- PostgreSQL
- MongoDB

---

### Cache

Improves response time.

Examples:

- Redis
- Memcached

---

### Message Queue

Supports asynchronous communication.

Examples:

- Kafka
- RabbitMQ

---

## Basic HLD Flow

Example:

```text
Client
↓
CDN
↓
Load Balancer
↓
API Gateway
↓
Application Service
↓
Cache
↓
Database
```

---

## Common Scalability Techniques

- Load Balancing
- Database Replication
- Database Sharding
- Caching
- CDN
- Asynchronous Processing
- Read Replica
- Rate Limiting

---

## Availability Techniques

Examples:

- Replication
- Failover
- Multi Region Deployment
- Circuit Breaker
- Retry
- Health Check

---

## Interview Approach

Interview Flow:

### Step 1

Clarify requirements

Example:

```text
Users?

Traffic?

Read Heavy?

Write Heavy?
```

---

### Step 2

Estimate scale

Example:

```text
10 Million Users

100K Requests / Second
```

---

### Step 3

Design components

Examples:

- Database
- Cache
- API Layer
- Queue

---

### Step 4

Discuss bottlenecks

Examples:

- Database overload
- Cache miss
- Traffic spike

---

### Step 5

Discuss scaling

Examples:

- Sharding
- Replication
- Horizontal Scaling

---

## Common HLD Interview Problems

- Tiny URL
- Instagram
- WhatsApp
- Uber
- YouTube
- Twitter
- Notification System
- News Feed
- Payment System
- Search System

---

## Interview Questions

### Q1. HLD vs LLD?

HLD:

System architecture.

LLD:

Class level design.

---

### Q2. Why cache used?

Reduce database load.

Improve performance.

---

### Q3. Why queue needed?

Handle asynchronous workload.

---

## Quick Revision

- HLD → Big picture architecture
- LLD → Component implementation
- Load Balancer → Traffic distribution
- Cache → Faster response
- Queue → Async processing
- Database → Persistent storage
- API Gateway → Single entry point
- Replication → Availability
- Sharding → Scalability
- CDN → Faster content delivery
- Retry → Temporary failure recovery
- Circuit Breaker → Failure isolation
- Rate Limiting → Traffic protection