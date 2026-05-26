

# Low Level Design (LLD)

## Definition

Low Level Design (LLD) explains internal system implementation.

LLD focuses on:

- Classes
- Objects
- Methods
- Relationships
- Design Patterns
- Data Models

Interview Goal:

Design maintainable and scalable components.

---

## Why LLD Needed?

Without LLD:

```text
Complex Code

↓

Tight Coupling

↓

Difficult Maintenance
```

Problems:

- Poor code maintainability
- Difficult testing
- Higher bug risk
- Difficult scalability

Benefits:

- Better code organization
- Better maintainability
- Easier testing
- Cleaner implementation

---

## HLD vs LLD

| Feature | HLD | LLD |
|----------|-----|-----|
| Focus | System Architecture | Component Design |
| Level | Big Picture | Internal Implementation |
| Covers | Database Cache Queue API | Classes Methods Objects |
| Audience | Architects | Developers |

Interview Tip:

HLD → System level

LLD → Code level

---

## LLD Building Blocks

### Class

Blueprint for objects.

Example:

```java
User

Order

Payment
```

---

### Object

Runtime instance of class.

Example:

```text
User user1
```

---

### Interface

Defines contract.

Example:

```java
NotificationService
```

---

### Design Pattern

Reusable design solution.

Common Patterns:

- Singleton
- Factory
- Strategy
- Observer

---

## LLD Design Principles

Common principles:

- SOLID
- Low Coupling
- High Cohesion
- Composition Over Inheritance

---

## Common LLD Interview Problems

- Parking Lot
- Elevator System
- Inventory System
- Notification System
- ATM Design
- BookMyShow
- Splitwise

---

## Interview Approach

Step 1:

Understand requirements.

Step 2:

Identify entities.

Step 3:

Identify relationships.

Step 4:

Create class diagram.

Step 5:

Apply design patterns.

Step 6:

Discuss scalability.

---

## Interview Questions

### Q1. HLD vs LLD?

HLD focuses architecture.

LLD focuses implementation.

---

### Q2. Why design patterns used?

Improve maintainability.

---

### Q3. Why interfaces used?

Reduce coupling.

---

## Quick Revision

- HLD → Architecture
- LLD → Implementation
- Class → Blueprint
- Object → Instance
- Interface → Contract
- Singleton → One instance
- Factory → Object creation
- Strategy → Flexible behavior
# Low Level Design (LLD)

## Purpose

Low Level Design (LLD) explains component implementation and internal system behavior.

LLD focuses on:

- Classes
- Objects
- Methods
- Relationships
- Design Patterns
- Data Models
- Code Maintainability
- Extensibility

Interview Goal:

```text
Requirements
↓
Entities
↓
Relationships
↓
Class Design
↓
Design Patterns
↓
Scalability
↓
Tradeoffs
```

---

## Why LLD Matters?

Without LLD:

```text
Complex Code
↓
Tight Coupling
↓
Difficult Maintenance
```

Problems:

- Poor maintainability
- Difficult testing
- Higher bug risk
- Difficult scalability

Benefits:

- Better organization
- Easier testing
- Cleaner implementation
- Better extensibility

---

## HLD vs LLD

| Feature | HLD | LLD |
|----------|-----|-----|
| Focus | System Architecture | Component Design |
| Level | Big Picture | Internal Implementation |
| Covers | Database Cache Queue API | Classes Objects Methods |
| Audience | Architects | Developers |
|
Interview Focus | Scalability | Maintainability |

Interview Tip:

```text
HLD
→ System Level

LLD
→ Component Level
```

---

## LLD Building Blocks

### Class

Blueprint for objects.

Examples:

```java
User
Order
Payment
```

---

### Object

Runtime instance of class.

Example:

```java
User user1
```

---

### Interface

Defines contract.

Example:

```java
NotificationService
```

---

### Design Pattern

Reusable design solution.

Common Patterns:

- Singleton
- Factory
- Strategy
- Observer
- Builder

---

## LLD Design Principles

Common principles:

- SOLID
- Low Coupling
- High Cohesion
- Composition Over Inheritance
- Separation Of Concerns

---

## Repository Coverage

Current systems:

- Elevator System
- Inventory System
- Notification System

Focus Areas:

- Entity Modeling
- Object Interaction
- Class Design
- Extensible Components

---

## Common LLD Interview Problems

- Parking Lot
- Elevator System
- Inventory System
- Notification System
- ATM Design
- BookMyShow
- Splitwise
- Hotel Management
- Library Management

---

## Interview Approach

Step 1:

Understand requirements.

Step 2:

Identify entities.

Step 3:

Identify relationships.

Step 4:

Create class diagram.

Step 5:

Apply design patterns.

Step 6:

Discuss scalability.

Step 7:

Discuss tradeoffs.

---

## Interview Questions

### Q1. HLD vs LLD?

HLD focuses architecture.

LLD focuses implementation.

---

### Q2. Why design patterns used?

Improve maintainability.

---

### Q3. Why interfaces used?

Reduce coupling.

---

### Q4. Why SOLID matters?

Improve maintainability and extensibility.

---

## Quick Revision

- HLD → Architecture
- LLD → Implementation
- Class → Blueprint
- Object → Instance
- Interface → Contract
- Singleton → One instance
- Factory → Object creation
- Strategy → Flexible behavior
- SOLID → Better maintainability
- Low Coupling → Easier changes