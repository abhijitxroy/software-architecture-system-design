

# Saga Pattern

## What is Saga Pattern?

Saga Pattern is a distributed transaction management pattern used in microservices architecture to maintain data consistency across multiple services without using a global database transaction.

Instead of one large transaction, Saga breaks business operations into smaller local transactions.

Each service:

- Executes local transaction
- Publishes event
- Triggers next service
- Performs compensation action if failure occurs

Saga pattern supports eventual consistency across distributed systems.

---

## Why Saga Pattern?

Problems without Saga:

- Distributed transaction complexity
- Database locking issues
- Poor scalability
- Tight service coupling
- Two Phase Commit performance overhead

Saga improves:

- Scalability
- Fault tolerance
- Service independence
- Reliability
- Distributed transaction handling

---

## High Level Architecture

```text
Order Service
     |
Create Order
     |
     v
Payment Service
     |
Process Payment
     |
     v
Inventory Service
     |
Reserve Inventory
     |
     v
Shipping Service

Failure
   |
   v
Compensation Actions
```

---

## Core Components

### Local Transaction

Each service performs database operations independently.

Example:

```text
Payment Service
→ Debit Amount
→ Commit Transaction
```

Local transactions avoid distributed database locking.

---

### Event Communication

Services communicate through events.

Examples:

- Kafka
- RabbitMQ
- Pulsar

Example:

```text
OrderCreated
PaymentCompleted
InventoryReserved
```

---

### Compensation Transaction

Compensation reverses completed operations.

Example:

```text
Payment Success
Inventory Failure
↓
Refund Payment
```

Compensation maintains business consistency.

---

## Saga Execution Models

### Choreography Pattern

Services communicate directly using events.

Flow:

```text
Order Service
      ↓
Payment Service
      ↓
Inventory Service
      ↓
Shipping Service
```

Advantages:

- Decentralized
- Lower coordination dependency

Disadvantages:

- Complex debugging
- Event dependency growth

---

### Orchestration Pattern

Central orchestrator controls execution.

Flow:

```text
Saga Orchestrator
       |
+------+------+------+
|      |      |      |
v      v      v      v
Order Payment Inventory Shipping
```

Advantages:

- Easier monitoring
- Better workflow visibility

Disadvantages:

- Central coordinator dependency

---

## Banking Example

Money transfer workflow:

```text
Debit Account
      ↓
Credit Account
      ↓
Send Notification
```

Failure case:

```text
Debit Success
Credit Failure
↓
Refund Debit
```

---

## Saga vs Two Phase Commit

| Feature | Saga Pattern | Two Phase Commit |
|----------|--------------|------------------|
| Consistency | Eventual | Strong |
| Scalability | Higher | Lower |
| Service Coupling | Lower | Higher |
| Performance | Better | Slower |
| Failure Handling | Compensation | Rollback |

---

## Production Challenges

Common issues:

- Duplicate events
- Compensation complexity
- Event ordering
- Debugging difficulty
- Long running transactions

Solutions:

- Idempotency
- Retry handling
- Event tracing
- Dead letter queue
- Monitoring

---

## Production Examples

Examples:

- Banking platform
- Payment processing system
- Order management system
- Trading platform
- FinTech infrastructure

---

## Interview Questions

1. What is Saga Pattern?

2. Why Saga instead of Two Phase Commit?

3. Choreography vs orchestration?

4. What is compensation transaction?

5. Saga challenges in production?

6. Eventual consistency vs strong consistency?

---

## Quick Revision

- Saga manages distributed transactions
- Local transactions improve scalability
- Compensation handles failure recovery
- Choreography uses events directly
- Orchestration uses central coordinator
- Saga provides eventual consistency
- Saga reduces distributed transaction coupling