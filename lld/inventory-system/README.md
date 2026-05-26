# Inventory System - Low Level Design (LLD)

## Problem Statement

Design an Inventory Management System for an E-Commerce platform.

System should support:

- Add Product
- Update Product Quantity
- Check Product Availability
- Reserve Inventory
- Release Inventory
- Product Search

Examples:

- Amazon Inventory
- Flipkart Inventory
- Blinkit Inventory

---

## Functional Requirements

System should support:

1. Add Product

2. Update Stock

3. Check Stock Availability

4. Reserve Product

5. Release Reserved Product

6. Product Search

---

## Non Functional Requirements

- High Availability
- Fast Lookup
- Scalability
- Data Consistency
- Low Latency

---

## Core Entities

## Product

```java
public class Product {

    private String productId;

    private String name;

    private String category;

    private double price;

    private int availableQuantity;

}
```

Responsibilities:

- Store product details
- Track available inventory

---

## Inventory

```java
public class Inventory {

    private Map<String, Product> products;

}
```

Responsibilities:

- Add product
- Remove product
- Search product
- Update stock

---

## Inventory Service

```java
public interface InventoryService {

    void addProduct(Product product);

    void updateStock(
        String productId,
        int quantity
    );

    boolean checkAvailability(
        String productId,
        int quantity
    );

    void reserveInventory(
        String productId,
        int quantity
    );

    void releaseInventory(
        String productId,
        int quantity
    );

}
```

---

## Class Diagram

```text
InventoryService
       |
       |
Inventory
       |
       |
Product
```

---

## Add Product Flow

```text
Admin

↓

Inventory Service

↓

Inventory

↓

Database
```

---

## Reserve Inventory Flow

Example:

User buys:

```text
Laptop

Quantity = 2
```

Flow:

```text
Checkout

↓

Check Inventory

↓

Reserve Product

↓

Reduce Available Quantity
```

---

## Inventory Reservation Example

Before:

```text
Laptop

Available = 10
```

User buys:

```text
2 Laptop
```

After:

```text
Available = 8
```

---

## Inventory Release Example

Payment failed.

Before:

```text
Available = 8
```

Release inventory:

```text
Available = 10
```

---

## Design Pattern Used

### Singleton

Inventory Service Instance.

### Factory Pattern

Product creation.

### Strategy Pattern

Inventory allocation strategy.

---

## Concurrency Problem

Scenario:

```text
2 Users

↓

Buy Last Product
```

Problem:

```text
Overselling
```

Solution:

- Database Lock
- Optimistic Locking
- Atomic Update

---

## Database Table

Product Table:

| ProductId | Name | Quantity | Price |
|------------|------|-----------|-------|
| P101 | Laptop | 100 | 50000 |

---

## Interview Questions

### Q1. How to avoid overselling?

Answer:

- Locking
- Atomic update
- Inventory reservation

---

### Q2. Why reservation needed?

Prevents multiple users purchasing same stock.

---

### Q3. Inventory consistency challenges?

- Concurrent update
- Duplicate reservation
- Stock mismatch

---

## Production Example

Amazon:

```text
Checkout

↓

Inventory Reservation

↓

Payment Success

↓

Stock Commit
```

Payment failure:

```text
Release Reserved Inventory
```

---

## Quick Revision

- Inventory = Product stock management
- Reservation prevents overselling
- Locking solves concurrency
- Atomic update improves consistency
- Inventory release handles payment failure
- Core entities → Product + Inventory + Service