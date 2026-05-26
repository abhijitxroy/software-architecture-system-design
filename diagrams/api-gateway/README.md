

# API Gateway Diagram

## Purpose

API Gateway acts as a single entry point for clients.

Responsibilities:

- Authentication
- Authorization
- Rate Limiting
- Request Routing
- SSL Termination
- Request Validation
- Observability

---

## High Level Flow

```text
Mobile App
Web App
Third Party Client
       ↓

+----------------+
|  API Gateway   |
+----------------+

Authentication
Rate Limiting
Routing
Logging

 ↓      ↓      ↓

User Service
Order Service
Payment Service
```

---

## Production Flow

```text
Client
 ↓
CDN
 ↓
Load Balancer
 ↓
API Gateway
 ↓
Microservices
 ↓
Database
```

---

## Why API Gateway?

Without API Gateway:

```text
Client
 ↓
Multiple Services

Authentication Everywhere
Rate Limiting Everywhere
Routing Everywhere
```

Problems:

- Duplicate logic
- Operational complexity
- Harder observability

With API Gateway:

```text
Single Entry Point
Centralized Policies
Better Security
```

---

## Interview Notes

API Gateway handles:

- Authentication
- Authorization
- Routing
- Throttling
- Logging
- Metrics

Common interview discussion:

```text
API Gateway vs Load Balancer
```

---

## Quick Revision

```text
API Gateway
→ Entry Point

Authentication
→ Security

Rate Limiting
→ Traffic Protection

Routing
→ Service Discovery
```