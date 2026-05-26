# Microservices Architecture Diagram

## Purpose

Microservices architecture breaks application functionality into independent services.

Goals:

- Independent deployment
- Better scalability
- Team autonomy
- Fault isolation
- Faster development

---

## High Level Flow

```text
Client
 ↓
API Gateway
 ↓

+----------------+
| User Service   |
+----------------+

+----------------+
| Order Service  |
+----------------+

+----------------+
| Payment Service|
+----------------+

+----------------+
| Notification   |
+----------------+
```

Each service owns its business logic.

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
Cache / Database
 ↓
Message Broker
```

---

## Why Microservices?

Monolith Problems:

```text
Single Deployment
↓
Tight Coupling
↓
Scaling Difficulty
↓
Slower Delivery
```

Microservices Benefits:

```text
Independent Services
↓
Independent Scaling
↓
Independent Deployment
```

---

## Communication Patterns

Synchronous:

```text
REST

gRPC
```

Asynchronous:

```text
Kafka

RabbitMQ
```

---

## Production Examples

Microservices commonly used in:

- E Commerce systems
- FinTech systems
- Media platforms
- Social platforms

---

## Challenges

Problems:

- Distributed tracing
- Service discovery
- Deployment complexity
- Data consistency
- Observability

---

## Interview Notes

Common discussion:

```text
Monolith vs Microservices

Service Discovery

Database Per Service

Distributed Transactions
```

---

## Quick Revision

```text
Microservices
→ Independent Services

API Gateway
→ Entry Point

Message Broker
→ Async Communication

Service Discovery
→ Service Coordination
```
