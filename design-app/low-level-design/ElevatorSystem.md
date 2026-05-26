# Elevator System Low Level Design

## Problem Statement

Design an elevator system for a multi floor building that efficiently handles elevator requests, floor scheduling and passenger movement.

System should support:

- Multiple Elevators
- Floor Request Handling
- Internal Elevator Request
- External Elevator Request
- Direction Management
- Elevator Scheduling
- Emergency Handling
- Capacity Validation

---

## Functional Requirements

### Core Features

- User requests elevator
- Select destination floor
- Assign best elevator
- Move elevator up and down
- Open and close door
- Handle multiple requests
- Emergency stop
- Overload detection

---

## Non Functional Requirements

### Performance

- Low waiting time
- Fast elevator assignment

### Reliability

- No request loss

### Scalability

- Multiple elevators
- High traffic buildings

### Availability

- Elevator service always operational

---

## Core Classes

### Elevator

Attributes:

```text
id
currentFloor
direction
status
capacity
currentLoad
requests
```

Methods:

```text
move()
openDoor()
closeDoor()
addRequest()
processRequest()
```

---

### ElevatorController

Responsibilities:

- Assign elevator
- Schedule requests
- Optimize movement

Methods:

```text
assignElevator()
findOptimalElevator()
```

---

### Floor

Attributes:

```text
floorNumber
upButton
downButton
```

---

### Request

Attributes:

```text
sourceFloor
destinationFloor
direction
requestTime
```

---

## High Level Design

```text
User
 |
Floor Button
 |
Elevator Controller
 |
+----------------+
| Elevator 1     |
| Elevator 2     |
| Elevator 3     |
+----------------+
 |
Request Queue
```

---

## Scheduling Algorithm

### Nearest Elevator Strategy

Rules:

- Same direction preferred
- Closest elevator preferred
- Idle elevator preferred

Example:

```text
Elevator A → Floor 3 → UP
Elevator B → Floor 7 → DOWN

Request:
Floor 4 → UP

Assign Elevator A
```

---

## State Design

### Elevator States

```text
IDLE
MOVING_UP
MOVING_DOWN
DOOR_OPEN
MAINTENANCE
```

---

## Request Flow

```text
User Request
 ↓
Controller
 ↓
Find Best Elevator
 ↓
Add Request Queue
 ↓
Move Elevator
 ↓
Open Door
```

---

## Edge Cases

- Elevator overload
- Elevator failure
- Multiple simultaneous request
- Emergency stop
- Power failure

---

## Design Patterns

### Strategy Pattern

Used for:

- Scheduling algorithm

### State Pattern

Used for:

- Elevator state management

### Observer Pattern

Used for:

- Request notification

---

## Tradeoffs

| Choice | Benefit | Drawback |
|---------|----------|-----------|
| Nearest elevator | Faster response | Possible imbalance |
| Complex scheduling | Better optimization | More computation |

---

## Interview Questions

1. How elevator scheduling works?
2. How nearest elevator selected?
3. Which design patterns useful?
4. How overload handled?
5. How multiple elevators coordinated?

---

## Quick Revision

- Controller assigns elevator
- State pattern manages elevator states
- Strategy pattern manages scheduling
- Queue handles requests
- Nearest elevator reduces waiting time
