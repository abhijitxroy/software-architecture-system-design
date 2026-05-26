

# Event Driven Architecture Diagram

## Purpose

Event Driven Architecture enables systems to communicate asynchronously.

Goals:

- Loose coupling
- Scalability
- Independent services
- Better reliability
- Higher throughput

---

## High Level Flow

```text
Order Service
 ↓ Event
Message Broker
 ↓
Inventory Service
 ↓
Notification Service
 ↓
Analytics Service
```

Producer publishes event.

Consumers process event independently.

---

## Production Flow

```text
Client
 ↓
Order Service
 ↓
Event Broker
(Kafka / RabbitMQ)
 ↓
Consumer Services
 ↓
Database
```

---

## Why Event Driven?

Without Event Driven:

```text
Order Service
 ↓
Inventory Service
 ↓
Notification Service
 ↓
Analytics Service
```

Problems:

- Tight coupling
- Higher latency
- Dependency failures
- Harder scaling

With Event Driven:

```text
Producer
↓
Broker
↓
Independent Consumers
```

Benefits:

- Better scalability
- Independent deployment
- Failure isolation

---

## Production Examples

Common use cases:

- Order processing
- Payment workflow
- Notification systems
- Analytics pipeline
- User activity tracking

---

## Common Components

```text
Producer
Broker
Consumer
Dead Letter Queue
Retry System
```

---

## Interview Notes

Common discussion:

```text
Kafka vs RabbitMQ

Event Driven vs Request Response

Message Queue vs Event Streaming
```

---

## Quick Revision

```text
Producer
→ Creates Event

Broker
→ Routes Event

Consumer
→ Processes Event

Event Driven
→ Loose Coupling
```