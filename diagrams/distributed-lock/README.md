

# Distributed Lock Diagram

## Purpose

Distributed Lock prevents multiple distributed services from modifying shared resources simultaneously.

Goals:

- Prevent duplicate processing
- Prevent race conditions
- Protect shared resources
- Improve consistency
- Coordinate distributed systems

---

## High Level Flow

```text
Service A
 ↓
Acquire Lock
 ↓ Success
Critical Section
 ↓
Release Lock


Service B
 ↓
Acquire Lock
 ↓ Failed
Wait / Retry
```

---

## Production Flow

```text
Application Instance A
        ↓
Application Instance B
        ↓
Application Instance C
        ↓

+----------------+
| Distributed Lock |
| Redis / ZooKeeper |
+----------------+

        ↓
Shared Resource
(Database / File / Payment)
```

---

## Why Distributed Lock?

Without Lock:

```text
Server A
 ↓
Update Inventory

Server B
 ↓
Update Inventory

Race Condition
```

Problems:

- Duplicate order processing
- Double payment execution
- Inventory inconsistency
- Data corruption

With Lock:

```text
Single Owner
↓
Safe Update
```

---

## Production Examples

Distributed Lock commonly used in:

- Payment processing
- Scheduler systems
- Inventory management
- Leader election
- Distributed jobs

---

## Common Implementations

```text
Redis SET NX EX

ZooKeeper

Database Row Lock
```

---

## Interview Notes

Common discussion:

```text
Distributed Lock vs Optimistic Lock

Redis Lock Failure

Lock Timeout
```

---

## Quick Revision

```text
Distributed Lock
→ Coordination

Race Condition
→ Multiple Writers

Lock Timeout
→ Failure Protection

Redis Lock
→ Common Implementation
```