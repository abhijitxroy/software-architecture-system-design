# API Gateway

## Definition

API Gateway is a single entry point between clients and backend services.

It receives client requests, applies common processing and routes traffic to appropriate backend services.

---

## Why Needed?

Without API Gateway:

```text
Client
 |
 |---- User Service
 |
 |---- Payment Service
 |
 |---- Notification Service
 |
 |---- Order Service
```

Problems:

- Client manages multiple APIs
- Authentication duplicated
- Complex frontend logic
- Tight coupling

With API Gateway:

```text
Client
  |
API Gateway
 /   |    \
User Payment Order
Service Service Service
```

Benefits:

- Single entry point
- Centralized authentication
- Request routing
- Reduced client complexity

---

## How It Works?

Steps:

1. Client sends request
2. API Gateway receives request
3. Authentication validation
4. Rate limiting check
5. Request routing
6. Backend service processing
7. Response returned

---

## Responsibilities

API Gateway commonly handles:

- Authentication
- Authorization
- Routing
- Rate Limiting
- Load Balancing
- Request Validation
- Response Aggregation
- Logging
- Monitoring

---

## Authentication Example

Without gateway:

```text
Frontend

↓

Service validates token
```

With gateway:

```text
Frontend

↓

API Gateway validates token

↓

Backend Service
```

Backend remains cleaner.

---

## Rate Limiting

Protect backend from traffic spikes.

Example:

```text
User Limit

100 Requests / Minute
```

If limit exceeded:

```text
HTTP 429

Too Many Requests
```

---

## Request Aggregation

Gateway combines multiple service responses.

Without aggregation:

```text
Frontend

↓

User API

↓

Order API

↓

Payment API
```

With aggregation:

```text
Frontend

↓

API Gateway

↓

Combined Response
```

Benefits:

- Fewer network calls
- Faster response

---

## API Gateway vs Load Balancer

| Feature | API Gateway | Load Balancer |
|----------|-------------|---------------|
| Authentication | Yes | No |
| Rate Limiting | Yes | No |
| Routing Logic | Smart Routing | Traffic Distribution |
| Response Aggregation | Yes | No |
| Backend Distribution | Limited | Primary Responsibility |

Interview Tip:

Load Balancer → Server distribution

API Gateway → API management

---

## Production Examples

- Kong
- NGINX
- AWS API Gateway
- Spring Cloud Gateway
- Envoy

---

## Real World Usage

Used in:

- Microservices Architecture
- E-Commerce Systems
- Banking Platforms
- Food Delivery Systems
- Streaming Platforms

---

## Common Problems

### Single Point Of Failure

Gateway failure affects application.

Solution:

```text
Deploy Multiple Gateway Instances
```

---

### Increased Latency

Extra network hop increases response time.

Solution:

- Gateway scaling
- Caching
- Efficient routing

---

## Interview Questions

### Q1. API Gateway vs Load Balancer?

API Gateway handles API concerns.

Load Balancer handles traffic distribution.

---

### Q2. Why API Gateway needed in Microservices?

- Centralized authentication
- Reduced frontend complexity
- Unified API management

---

### Q3. Can API Gateway do Load Balancing?

Yes.

But primary purpose:

```text
API Management
```

---

## Quick Revision

- API Gateway → Single entry point
- Authentication → Centralized
- Rate Limiting → Traffic protection
- Aggregation → Multiple APIs → Single response
- Common