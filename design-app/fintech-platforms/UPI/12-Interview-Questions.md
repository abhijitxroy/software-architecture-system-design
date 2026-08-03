# Interview Questions

## Overview

This chapter contains commonly asked UPI interview questions organized by difficulty. The goal is not only to memorize answers, but also to understand the underlying engineering concepts.

---

# Beginner Level

### 1. What is UPI?

**Answer**

UPI (Unified Payments Interface) is a real-time payment system developed by NPCI that enables instant bank-to-bank money transfers using mobile applications.

---

### 2. Who developed UPI?

**Answer**

The National Payments Corporation of India (NPCI).

---

### 3. What is NPCI?

**Answer**

NPCI is the organization that operates India's retail payment infrastructure, including UPI, IMPS, RuPay, NACH, BBPS, and FASTag.

---

### 4. Is Google Pay a bank?

**Answer**

No.

Google Pay is a Third-Party Application Provider (TPAP). It provides the user interface and works with participating banks to access the UPI infrastructure.

---

### 5. Can UPI work without a bank?

**Answer**

No.

Customer money is held by banks. Banks perform debit and credit operations.

---

# Intermediate Level

### 6. Explain a complete UPI transaction.

**Expected Topics**

- Customer
- UPI App
- PSP
- NPCI
- Sender Bank
- Receiver Bank
- Debit
- Credit
- Response

---

### 7. What is the role of a PSP?

**Answer**

A PSP validates payment requests, communicates with NPCI, and returns transaction responses to the UPI application.

---

### 8. Why is NPCI needed?

**Answer**

NPCI acts as a central payment switch, allowing every participant to integrate once instead of connecting directly with every other bank.

---

### 9. What is the difference between Authentication and Authorization?

**Answer**

Authentication verifies **who** is initiating the payment.

Authorization determines **whether** the payment is allowed.

---

### 10. What is the difference between Clearing and Settlement?

**Answer**

Clearing exchanges payment instructions and calculates obligations.

Settlement transfers funds between financial institutions.

---

# Senior Engineer Level

### 11. Design a UPI-like payment system.

Discuss:

- Architecture
- APIs
- Scalability
- Security
- Failure handling
- Observability

---

### 12. How would you prevent duplicate payments?

Expected discussion:

- Idempotency
- Unique transaction IDs
- Retry handling
- Transaction state management

---

### 13. What happens if the sender bank debits money but the receiver bank never credits it?

Expected discussion:

- Retry
- Timeout
- Reconciliation
- Reversal
- Customer notification

---

### 14. How would you scale UPI?

Expected discussion:

- Stateless services
- Horizontal scaling
- Load balancing
- Caching
- Message queues
- Database partitioning
- Monitoring

---

### 15. How would you monitor production health?

Expected discussion:

- Metrics
- Logging
- Distributed tracing
- Alerts
- Dashboards
- SLA monitoring

---

# Principal Engineer Level

### 16. How would you redesign the NPCI switch?

Topics:

- High Availability
- Multi-region deployment
- Active-Active architecture
- Fault tolerance
- Disaster recovery

---

### 17. What are the biggest engineering challenges in payment systems?

Examples:

- Financial consistency
- Security
- Fraud prevention
- Scalability
- Reliability
- Regulatory compliance

---

### 18. What trade-offs exist in payment system design?

Examples:

- Consistency vs Availability
- Performance vs Security
- Synchronous vs Asynchronous processing
- Retry vs Duplicate execution

---

# Rapid Revision

Remember these key points:

- NPCI routes transactions.
- Banks own customer accounts.
- PSP connects applications with NPCI.
- Authentication and Authorization are different.
- Clearing and Settlement are different.
- UPI is a distributed payment ecosystem.
- Idempotency prevents duplicate payments.
- Reconciliation ensures financial correctness.
- Reliability is more important than raw speed.

---

# Final Takeaway

A strong UPI interview answer should explain not only **what** happens, but also **why** the architecture is designed that way, what can fail, how failures are handled, and what trade-offs are involved in building a production-scale payment system.
