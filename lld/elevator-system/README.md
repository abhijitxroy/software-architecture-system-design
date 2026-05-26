# Elevator System - Low Level Design (LLD)

## Problem Statement

Design an Elevator System for a multi-floor building.

System should support:

- Multiple Elevators
- Multiple Floors
- Internal Elevator Request
- External Elevator Request
- Up Direction
- Down Direction

Examples:

- Office Buildings
- Shopping Mall
- Hospital
- Apartment Complex

---

## Functional Requirements

System should support:

1. Request Elevator

2. Move Elevator

3. Open Door

4. Close Door

5. Select Destination Floor

6. Handle Multiple Requests

---

## Non Functional Requirements

- Low Waiting Time
- High Availability
- Fault Tolerance
- Efficient Scheduling

---

## Core Entities

## Elevator

```java
public class Elevator {

    private int elevatorId;

    private int currentFloor;

    private Direction direction;

    private ElevatorState state;

}
```

---

## Floor

```java
public class Floor {

    private int floorNumber;

}
```

---

## Direction

```java
public enum Direction {

    UP,

    DOWN,

    IDLE

}
```

---

## Elevator State

```java
public enum ElevatorState {

    MOVING,

    IDLE,

    MAINTENANCE

}
```

---

## Elevator Controller

```java
public class ElevatorController {

    public void requestElevator(
        int floor,
        Direction direction
    ) {

    }

}
```

Responsibilities:

- Assign elevator
- Process requests
- Scheduling

---

## Class Diagram

```text
ElevatorController
        |
        |
Elevator
        |
        |
Floor
```

---

## User Flow

Example:

User presses:

```text
Floor 5

↓

UP
```

Flow:

```text
Request Elevator

↓

Controller

↓

Find Best Elevator

↓

Move Elevator

↓

Open Door
```

---

## Internal Request Flow

User enters elevator.

Select:

```text
Floor 10
```

Flow:

```text
Button Click

↓

Request Added

↓

Elevator Moves

↓

Floor Reached
```

---

## Scheduling Problem

Example:

```text
Elevator 1

Floor 2

Moving UP
```

Request:

```text
Floor 3

UP
```

Better choice:

```text
Elevator 1
```

Reason:

Closer elevator.

---

## Scheduling Strategies

### First Come First Serve (FCFS)

Process requests sequentially.

Example:

```text
Floor 3

↓

Floor 8

↓

Floor 5
```

Problem:

Higher waiting time.

---

### Nearest Elevator Strategy

Assign closest elevator.

Benefits:

- Faster response
- Better efficiency

Most common interview approach.

---

## Concurrency Problem

Scenario:

```text
100 Users

↓

Request Elevator
```

Problems:

- Race condition
- Request collision

Solutions:

- Queue
- Locking
- Thread safe scheduling

---

## Design Patterns Used

### Singleton

Single controller instance.

---

### Strategy Pattern

Different scheduling algorithms.

Examples:

```text
FCFS
```

```text
Nearest Elevator
```

---

## Database Requirement

Usually elevator systems do not need heavy database interaction.

Optional:

Store:

- Usage logs
- Maintenance history

---

## Production Example

Office Building:

```text
Request Floor 8

↓

Nearest Elevator Found

↓

Move Elevator

↓

Open Door
```

---

## Interview Questions

### Q1. How elevator selected?

Scheduling algorithm.

---

### Q2. Which scheduling strategy preferred?

Nearest elevator strategy.

---

### Q3. Why Strategy Pattern used?

Scheduling algorithm can change easily.

---

### Q4. Biggest challenge?

Efficient elevator assignment.

---

## Quick Revision

- Elevator Controller manages requests
- Direction → UP DOWN IDLE
- Nearest elevator → Better efficiency
- Strategy Pattern → Scheduling logic
- Singleton → Controller management
- Queue handles concurrent requests