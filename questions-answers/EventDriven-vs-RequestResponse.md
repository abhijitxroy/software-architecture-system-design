

# Event Driven vs Request Response

## Why This Comparison Matters?

Event Driven and Request Response are common communication patterns in distributed systems.

System design interviews frequently ask when to choose one over another.

Choosing the wrong pattern can create:

- Higher latency
- Tight coupling
- Scalability problems
- Operational complexity
- Reliability issues

Understanding communication patterns is important for:

- System Design Interviews
- Distributed Systems
- Microservices Design
- Production Architecture

---

## Request Response

Request Response follows a direct communication model.

Flow:

```text
Service A
   ↓ Request
Service B
   ↓ Response
Service A
```

Example:

```text
User Opens Profile
      ↓
Frontend Calls User Service
      ↓
User Service Returns Data
```

Examples:

- REST API
- gRPC
- GraphQL

Best For:

- User Login
- Profile Lookup
- Payment Validation
- Inventory Check

Pros:

- Simple implementation
- Immediate response
- Easier debugging

Cons:

- Tight coupling
- Higher dependency between services
- Failure propagation

---

## Event Driven Architecture

Event Driven systems communicate using events.

Producer creates event.

Consumer processes event asynchronously.

Flow:

```text
Order Service
      ↓
Publish Event
      ↓
Message Queue
   ↓      ↓
Email   Inventory
Service Service
```

Examples:

- Kafka
- RabbitMQ
- PubSub

Best For:

- Notification System
- Analytics Pipeline
- Order Processing
- Activity Tracking

Pros:

- Better scalability
- Loose coupling
- Async processing
- Failure isolation

Cons:

- Debugging harder
- Event ordering challenges
- Operational complexity

---

## Key Differences

| Feature | Request Response | Event Driven |
|----------|------------------|---------------|
| Communication | Direct | Async |
| Coupling | Tighter | Looser |
| Response | Immediate | Delayed Possible |
| Scalability | Moderate | Better |
| Reliability | Lower | Better |
| Complexity | Lower | Higher |
| Best For | User APIs | Async Workload |

---

## Production Example

Login System:

```text
Need Immediate Response
```

Choose:

```text
Request Response
```

Order Platform:

```text
Order Created
 ↓
Send Email
Update Inventory
Analytics Update
```

Choose:

```text
Event Driven
```

---

## Interview Shortcut

Remember:

```text
Request Response
→ Immediate Reply

Event Driven
→ Async Processing
```

---

## Interview Questions

1. Event Driven vs Request Response?

2. Why event driven improves scalability?

3. When request response works better?

4. Why event driven systems are loosely coupled?

5. Kafka use case?

6. Notification system architecture choice?

---

## Quick Revision

- Request response gives immediate reply
- Event driven improves scalability
- Event driven supports async processing
- Request response creates tighter coupling
- Kafka commonly powers event driven systems
- Communication pattern depends on workload
- Event driven is common interview topic