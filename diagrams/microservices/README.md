# Microservices Architecture Diagram

## Why It Matters

Microservices Architecture is an architectural style where an application is built as a collection of small, independently deployable services.

Each service:

- Owns a specific business capability
- Has its own codebase
- Can be deployed independently
- Can scale independently
- Owns its own data

Microservices enable organizations to build large-scale systems while allowing teams to work independently.

Common use cases:

- E-Commerce Platforms
- Banking Systems
- SaaS Applications
- Streaming Platforms
- Ride Sharing Platforms
- Social Media Systems

---

## What Are Microservices?

Instead of building one large application, functionality is divided into smaller services.

Example:

```text
User Service
Order Service
Payment Service
Notification Service
Inventory Service
```

Each service is responsible for a single business domain.

---

## High-Level Architecture

```mermaid
flowchart TD

    Client[Client]

    Gateway[API Gateway]

    User[User Service]
    Order[Order Service]
    Payment[Payment Service]
    Notification[Notification Service]

    Client --> Gateway

    Gateway --> User
    Gateway --> Order
    Gateway --> Payment
    Gateway --> Notification
```

The API Gateway acts as the entry point to the microservice ecosystem.

---

## Production Architecture

```mermaid
flowchart TD

    Client[Client]

    CDN[CDN]

    LB[Load Balancer]

    Gateway[API Gateway]

    User[User Service]
    Order[Order Service]
    Payment[Payment Service]
    Notification[Notification Service]

    Cache[(Cache)]
    DB[(Databases)]

    Broker[Kafka / RabbitMQ]

    Client --> CDN
    CDN --> LB
    LB --> Gateway

    Gateway --> User
    Gateway --> Order
    Gateway --> Payment
    Gateway --> Notification

    User --> Cache
    Order --> Cache

    User --> DB
    Order --> DB
    Payment --> DB

    Order --> Broker
    Payment --> Broker
    Notification --> Broker
```

Modern production environments often combine:

- API Gateway
- Service Discovery
- Message Brokers
- Distributed Caching
- Observability Platforms

---

## Monolith vs Microservices

### Monolithic Architecture

```mermaid
flowchart TD

    Client[Client]

    Monolith[Single Application]

    DB[(Database)]

    Client --> Monolith
    Monolith --> DB
```

Advantages:

- Simpler development
- Easier deployment
- Easier debugging

Disadvantages:

- Tight coupling
- Difficult scaling
- Large deployments
- Slower release cycles

---

### Microservices Architecture

```mermaid
flowchart TD

    Client[Client]

    Gateway[API Gateway]

    User[User Service]
    Order[Order Service]
    Payment[Payment Service]

    Client --> Gateway

    Gateway --> User
    Gateway --> Order
    Gateway --> Payment
```

Advantages:

- Independent deployment
- Independent scaling
- Team autonomy
- Better fault isolation

Disadvantages:

- Operational complexity
- Distributed system challenges

---

## Service Ownership

Each service owns its business domain.

```mermaid
flowchart TD

    User[User Service]

    Order[Order Service]

    Payment[Payment Service]

    UserDB[(User DB)]
    OrderDB[(Order DB)]
    PaymentDB[(Payment DB)]

    User --> UserDB
    Order --> OrderDB
    Payment --> PaymentDB
```

Principle:

```text
Database Per Service
```

Benefits:

- Better isolation
- Independent evolution
- Reduced coupling

---

## Synchronous Communication

Services communicate directly.

### REST

```mermaid
flowchart LR

    Order[Order Service]

    Inventory[Inventory Service]

    Order --> Inventory
```

---

### gRPC

```mermaid
flowchart LR

    ServiceA[Service A]

    ServiceB[Service B]

    ServiceA --> ServiceB
```

Advantages:

- Fast response
- Simpler flow

Disadvantages:

- Tight runtime dependency

---

## Asynchronous Communication

Services communicate using events.

```mermaid
flowchart TD

    Order[Order Service]

    Broker[Kafka]

    Inventory[Inventory Service]

    Notification[Notification Service]

    Analytics[Analytics Service]

    Order --> Broker

    Broker --> Inventory
    Broker --> Notification
    Broker --> Analytics
```

Advantages:

- Loose coupling
- Better scalability
- Failure isolation

---

## Service Discovery

Services need to find each other dynamically.

```mermaid
flowchart TD

    ServiceA[Service A]

    Registry[Service Registry]

    ServiceB[Service B]

    ServiceA --> Registry
    ServiceB --> Registry
```

Common solutions:

- Consul
- Eureka
- Kubernetes DNS

Benefits:

- Dynamic service location
- Easier scaling

---

## API Gateway

Acts as the central entry point.

Responsibilities:

- Authentication
- Authorization
- Routing
- Rate Limiting
- Logging

```mermaid
flowchart TD

    Client[Client]

    Gateway[API Gateway]

    Services[Microservices]

    Client --> Gateway
    Gateway --> Services
```

Benefits:

- Centralized security
- Simplified clients

---

## Distributed Transactions Problem

### Example

```text
Order Created
      ↓
Payment Charged
      ↓
Inventory Reserved
```

If payment succeeds but inventory fails:

```text
Inconsistent State
```

Challenge:

```text
Multiple Databases
```

---

## Saga Pattern

A common solution for distributed transactions.

```mermaid
flowchart TD

    Order[Create Order]

    Payment[Process Payment]

    Inventory[Reserve Inventory]

    Complete[Complete Order]

    Order --> Payment
    Payment --> Inventory
    Inventory --> Complete
```

If a step fails:

```text
Compensating Actions Execute
```

Benefits:

- Eventual consistency
- No global transaction manager

---

## Fault Isolation

Failure in one service should not bring down the entire system.

```mermaid
flowchart TD

    User[User Service]

    Payment[Payment Service]

    Failure[Payment Failure]

    User --> Payment
    Payment --> Failure
```

Desired behavior:

```text
Payment Fails

User Service Continues
```

---

## Circuit Breaker Pattern

Prevents cascading failures.

```mermaid
flowchart TD

    Request[Request]

    Circuit[Circuit Breaker]

    Service[Remote Service]

    Request --> Circuit
    Circuit --> Service
```

Benefits:

- Failure isolation
- Faster recovery

---

## Observability

Microservices require strong observability.

Components:

```text
Logs
Metrics
Tracing
Alerting
```

### Observability Architecture

```mermaid
flowchart TD

    Services[Microservices]

    Logs[Logs]

    Metrics[Metrics]

    Traces[Distributed Tracing]

    Services --> Logs
    Services --> Metrics
    Services --> Traces
```

Common tools:

- Prometheus
- Grafana
- Jaeger
- OpenTelemetry

---

## Production Examples

### Netflix

Uses:

- Thousands of microservices
- API Gateway
- Service Discovery

---

### Amazon

Uses:

- Service-oriented architecture
- Independent teams
- Distributed ownership

---

### Uber

Uses:

- Large-scale microservices
- Event-driven communication

---

### Spotify

Uses:

- Domain-oriented services
- Independent deployment

---

## Common Production Problems

### Distributed Tracing

Symptoms:

```text
Difficult Debugging
```

Cause:

```text
Request Crosses Many Services
```

---

### Service Dependency Failure

Symptoms:

```text
Cascading Outages
```

Cause:

```text
Tight Runtime Dependencies
```

---

### Data Consistency

Symptoms:

```text
Different Services Show Different Data
```

Cause:

```text
Distributed Databases
```

---

### Deployment Complexity

Symptoms:

```text
Operational Overhead
```

Cause:

```text
Large Number Of Services
```

---

## When Not To Use Microservices

Avoid Microservices when:

```text
Small Team

Small Product

Simple Business Logic

Early Startup
```

A monolith is often the better choice initially.

---

## Interview Questions

### Basic

- What are Microservices?
- Why do we use them?
- Monolith vs Microservices?

### Intermediate

- API Gateway role?
- Service Discovery?
- Database Per Service?

### Advanced

- How would you handle distributed transactions?
- What is the Saga Pattern?
- How would you prevent cascading failures?
- How would you observe hundreds of services?

---

## Quick Revision

```text
Microservices
→ Independent Services

API Gateway
→ Entry Point

Database Per Service
→ Ownership Model

REST / gRPC
→ Synchronous Communication

Kafka / RabbitMQ
→ Asynchronous Communication

Service Discovery
→ Find Services

Saga Pattern
→ Distributed Transactions

Circuit Breaker
→ Failure Protection

Observability
→ Logs Metrics Traces
```

---

## Key Concepts

| Concept | Description |
|----------|----------|
| Microservices | Independent business services |
| API Gateway | Central entry point |
| Service Discovery | Dynamic service lookup |
| REST | HTTP-based communication |
| gRPC | High-performance RPC |
| Kafka | Event streaming platform |
| Saga Pattern | Distributed transaction pattern |
| Circuit Breaker | Failure isolation mechanism |
| Database Per Service | Independent data ownership |
| Observability | Logs, metrics, traces |
| Fault Isolation | Limit failure impact |
| Independent Deployment | Release services separately |