

# API Gateway System Design

## Problem Statement

Design an API Gateway platform that acts as a single entry point for clients and routes requests to backend services.

Used in:

- Microservices
- Kubernetes Platforms
- Cloud Native Systems
- Mobile Backend Systems
- AI Platforms

Examples:

- Kong
- NGINX
- Envoy
- AWS API Gateway

System should support:

- Request Routing
- Authentication
- Authorization
- Rate Limiting
- Load Balancing
- Request Validation
- API Aggregation
- Monitoring

---

## Functional Requirements

### Core Features

- Route request
- JWT validation
- API key validation
- Rate limiting
- Request transformation
- Response aggregation
- Retry support
- Circuit breaker

---

## Non Functional Requirements

### Scalability

- Millions of requests/minute

### Availability

- 99.99% uptime

### Reliability

- No routing failure

### Latency

- Gateway overhead under 20 ms

---

## Why API Gateway Needed

Without gateway:

```text
Mobile App
 ↓
User Service
Order Service
Payment Service
Notification Service
```

Problems:

- Multiple endpoints
- Authentication duplication
- Client complexity

Goal:

```text
Single Entry Point
↓
Centralized Control
```

---

## Core Responsibilities

### Authentication

Examples:

- JWT
- OAuth
- API Key

Purpose:

```text
Validate identity
```

---

### Rate Limiting

Example:

```text
100 Requests / Minute
```

Algorithms:

- Token Bucket
- Sliding Window
- Leaky Bucket

Purpose:

Protect backend systems.

---

### Request Routing

Example:

```text
/api/users
↓
User Service

/api/orders
↓
Order Service
```

---

### API Aggregation

Example:

Without aggregation:

```text
Client
↓
User API
Order API
Payment API
```

With gateway:

```text
Client
↓
Gateway
↓
Combined Response
```

---

### Circuit Breaker

Problem:

```text
Payment Service Down
```

Solution:

```text
Fail Fast
↓
Fallback Response
```

States:

- Closed
- Open
- Half Open

---

## High Level Design

```text
Client
 |
Load Balancer
 |
API Gateway
 |
Authentication Layer
 |
Rate Limiter
 |
Routing Layer
 |
Service Discovery
 |
Backend Services
```

---

## Request Flow

```text
Client Request
↓
Authentication
↓
Rate Limiting
↓
Routing
↓
Backend Service
↓
Response
```

---

## Scaling Strategy

### Horizontal Scaling

Add gateway instances.

### Redis

Responsibilities:

- Rate limit counters
- Session cache

### Service Discovery

Examples:

- Consul
- Kubernetes Service Discovery

---

## Monitoring

Track:

- Request latency
- Error rate
- Throughput
- Gateway failures

---

## Reliability

Strategies:

- Retry mechanism
- Circuit breaker
- Multi region deployment
- Health checks

---

## Tradeoffs

| Choice | Benefit | Drawback |
|----------|----------|-----------|
| Centralized gateway | Simpler clients | Gateway bottleneck |
| Aggregation | Fewer calls | More gateway complexity |
| Strict rate limiting | Protection | Possible throttling |

---

## Interview Questions

1. Why API gateway needed?
2. Gateway vs Load Balancer?
3. Why rate limiting useful?
4. Why circuit breaker needed?
5. Why aggregation useful?
6. How API gateway scales?

---

## Quick Revision

- Gateway provides single entry point
- Rate limiting protects backend
- Circuit breaker improves resilience
- Aggregation reduces client calls
- JWT improves authentication
- Redis supports rate limiting