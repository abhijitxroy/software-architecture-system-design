# Parking Lot System Design

## Problem Statement

Design a parking lot management system.

Features:

- Vehicle Entry
- Vehicle Exit
- Parking Spot Allocation
- Parking Ticket Generation
- Payment Processing
- Available Slot Tracking

Examples:

- Mall Parking
- Airport Parking
- Office Parking

---

## Clarifying Questions

Interview starts here.

Questions:

1. Single floor or multiple floors?

2. Vehicle types?

- Car
- Bike
- Truck

3. Multiple entry and exit gates?

4. Payment types?

- Cash
- Card
- UPI

5. Reservation needed?

---

## Functional Requirements

System should support:

1. Vehicle Entry

2. Vehicle Exit

3. Parking Spot Assignment

4. Payment

5. Display Available Spots

6. Parking Ticket Generation

---

## Non Functional Requirements

- Scalability
- Reliability
- Low Latency
- Fault Tolerance

---

## Core Classes

ParkingLot

Responsibilities:

- Manage floors
- Manage slots

ParkingFloor

Responsibilities:

- Floor level parking spots

ParkingSpot

Responsibilities:

- Slot allocation
- Availability status

Vehicle

Types:

- Car
- Bike
- Truck

ParkingTicket

Responsibilities:

- Entry Time
- Exit Time
- Price

Payment

Responsibilities:

- Fee calculation
- Payment status

---

## High Level Design

```text
Vehicle Entry
↓
Entry Panel
↓
Parking Service
↓
Parking Spot Allocation
↓
Database
```

Exit Flow:

```text
Vehicle Exit

↓

Ticket Validation

↓

Payment

↓

Gate Open
```

---

## Database Design

Vehicle Table:

| VehicleId | Type |
|------------|------|
| V101 | Car |

ParkingSpot Table:

| SpotId | Floor | Status |
|---------|-------|--------|
| P101 | 1 | Free |

Ticket Table:

| TicketId | Vehicle | EntryTime |
|-----------|----------|------------|
| T101 | V101 | 10:00 |

---

## Parking Spot Allocation

Interview Focus Topic.

Flow:

```text
Vehicle Arrives

↓

Find Free Slot

↓

Assign Spot
```

Optimization:

```text
Nearest Available Slot
```

---

## Display Board

Example:

```text
Floor 1

Car : 10 Free

Bike : 5 Free
```

Goal:

Fast parking allocation.

---

## Payment Flow

```text
Vehicle Exit

↓

Calculate Duration

↓

Calculate Fee

↓

Payment Success
```

---

## Scaling Strategy

Application:

- Horizontal Scaling

Database:

- Read Replica

Cache:

- Redis

---

## Bottleneck

Problems:

- Entry traffic spike
- Payment bottleneck
- Spot synchronization issue

Solutions:

- Redis
- Queue Processing
- Database Locking

---

## Interview Questions

### Q1. Important entities?

ParkingLot.

ParkingFloor.

ParkingSpot.

Vehicle.

Ticket.

---

### Q2. Prevent same slot allocation?

Locking.

---

### Q3. Major parking challenge?

Spot allocation.

---

## Quick Revision

- ParkingLot → Core manager
- Spot Allocation → Main problem
- Ticket → Entry + Exit tracking
- Redis → Fast lookup
- Locking → Prevent duplicate allocation


<!-- ### OLD Data -->
<!-- #parking lot
Ask clarifying questions

Is this a multiple floor parking garage or a single level parking lot?
How many entry and exit points will be needed, and for what types of vehicles?
Are there monetary goals for this parking lot?
Design high-level

Possible use cases: customers parking and paying for their spot, admin managing the system, parking attendants maintaining the lot and helping customers, etc.
Possible classes of the system: ParkingLot, ParkingFloor, Account, ParkingTicket, Vehicle, etc.
Drill down on your design

How will you diagram specific activities? (e.g. customers paying for parking tickets, display panels showing available spots, etc.)
What are the required enums, data types, and constants of the eventual code for the parking lot system?
Bring it all together

Will this system meet the requirements you’ve laid out with the interviewer in the beginning of the session?

Tutorial: https://www.youtube.com/watch?v=tVRyb4HaHgw&t=3s -->