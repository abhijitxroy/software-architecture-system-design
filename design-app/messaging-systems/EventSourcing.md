

# Event Sourcing

## What is Event Sourcing?

Event Sourcing is an architecture pattern where application state is stored as a sequence of immutable events instead of storing only the latest database state.

Every change in the system generates an event.

Instead of storing:

```text
Account Balance = 5000
```

Event sourcing stores:

```text
Account Created +10000
Money Debited -2000
Money Debited -3000
```

Current state is reconstructed by replaying events.

Event sourcing is commonly used in:

- Banking systems
- Financial platforms
- Audit systems
- Trading systems
- Order processing platforms
- Event driven architecture

---

## Why Event Sourcing?

Problems without event sourcing:

- Audit history missing
- Difficult debugging
- State reconstruction impossible
- Limited historical visibility
- Complex rollback process

Event sourcing improves:

- Complete audit trail
- Historical replay
- Better observability
- Event driven integration
- Temporal analysis

---

## High Level Architecture

```text
Client Request
      |
      v
Command Layer
      |
      v
Business Logic
      |
Generate Event
      |
      v
+----------------+
| Event Store    |
+--------+-------+
         |
         |
+--------v--------+
| Projection Layer|
+--------+--------+
         |
         v
Read Database
```

---

## Core Components

### Command Layer

Receives requests that modify system state.

Examples:

```text
Create Order
Transfer Money
Place Trade
```

Responsibilities:

- Validation
- Business rules
- Event generation

---

### Event Store

Stores immutable events.

Example:

```text
OrderCreated
PaymentProcessed
InventoryReserved
```

Requirements:

- Durability
- Ordering guarantee
- Immutable storage

---

### Projection Layer

Builds query optimized views.

Example:

```text
Events
   ↓
Projection
   ↓
Current Account Balance
```

Benefits:

- Faster reads
- Query optimization

---

### Read Model

Stores materialized views.

Example:

```text
User Dashboard
Order Summary
Analytics View
```

---

## Event Flow Example

Banking example:

```text
Create Account +10000
      ↓
Withdraw -2000
      ↓
Deposit +500
      ↓
Current Balance = 8500
```

State rebuilt using event replay.

---

## Event Sourcing vs Traditional Database

| Feature | Traditional Database | Event Sourcing |
|----------|----------------------|----------------|
| Storage Model | Current State | Event History |
| Audit Trail | Limited | Complete |
| Historical Replay | Difficult | Native Support |
| Debugging | Harder | Easier |
| Storage Growth | Smaller | Larger |

---

## Event Sourcing with CQRS

CQRS commonly works with event sourcing.

Flow:

```text
Write Model
    ↓
Event Store
    ↓
Projection
    ↓
Read Model
```

Benefits:

- Independent scaling
- Better read performance
- Separation of responsibilities

---

## Production Challenges

Common issues:

- Event schema evolution
- Storage growth
- Replay latency
- Complex debugging
- Projection consistency

Solutions:

- Snapshotting
- Event versioning
- Data archival
- Monitoring
- Projection retry handling

---

## Snapshot Strategy

Snapshot reduces replay overhead.

Example:

```text
1000 Events
      ↓
Snapshot Balance=45000
      ↓
Replay Remaining Events
```

Benefits:

- Faster recovery
- Lower replay cost

---

## Production Examples

Examples:

- Banking ledger platform
- Payment systems
- Trading infrastructure
- Audit platform
- Order processing systems

---

## Interview Questions

1. What is Event Sourcing?

2. Why immutable events matter?

3. Event sourcing vs traditional database?

4. Why snapshotting is important?

5. Event sourcing vs CQRS?

6. Production challenges of event sourcing?

---

## Quick Revision

- Event sourcing stores immutable history
- Current state rebuilt using event replay
- Event stores improve audit capability
- Snapshotting reduces replay latency
- CQRS commonly integrates with event sourcing
- Event sourcing improves traceability
- Immutable events improve debugging