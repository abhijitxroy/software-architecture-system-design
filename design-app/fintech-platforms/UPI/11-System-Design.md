# UPI System Design

## Overview

Designing a UPI-like payment system requires much more than transferring money between two bank accounts. The platform must process millions of transactions every day while maintaining security, consistency, high availability, and regulatory compliance.

This chapter explains how to design a scalable, reliable, and production-ready UPI ecosystem from a software architecture perspective.

---

# System Requirements

## Functional Requirements

- Register users
- Link bank accounts
- Send money
- Receive money
- Scan & Pay (QR)
- Collect Request
- Transaction History
- Balance Check
- Refunds
- Notifications

---

## Non-Functional Requirements

- High Availability
- Low Latency
- Horizontal Scalability
- Strong Security
- Fault Tolerance
- Reliability
- Auditability
- Regulatory Compliance

---

# High-Level Architecture

```text
                    Customer
                        │
                        ▼
                  UPI Mobile App
                        │
                        ▼
                  API Gateway
                        │
        ┌───────────────┼────────────────┐
        ▼               ▼                ▼
Authentication     Payment Service   Notification Service
        │               │                │
        └───────────────┼────────────────┘
                        ▼
                   PSP Backend
                        │
                        ▼
                  NPCI UPI Switch
                ┌────────┴────────┐
                ▼                 ▼
          Sender Bank       Receiver Bank
                │                 │
                ▼                 ▼
            Core Banking      Core Banking
```

---

# Major Components

## API Gateway

Responsible for:

- Authentication
- Request validation
- Rate limiting
- Routing
- Logging

---

## Authentication Service

Responsible for:

- User authentication
- Device verification
- Token validation
- Session management

---

## Payment Service

Responsible for:

- Payment orchestration
- Transaction lifecycle
- Request validation
- Status tracking

---

## Notification Service

Responsible for:

- Push notifications
- SMS
- Email
- Webhooks

---

## NPCI Switch

Responsible for:

- Request routing
- Bank identification
- Message exchange
- Settlement coordination

---

## Banks

Responsible for:

- Debit
- Credit
- Ledger updates
- Balance validation
- Account management

---

# Database Design

Typical entities include:

- Customer
- Device
- Bank Account
- VPA
- Transaction
- Ledger
- Settlement
- Audit Log

---

# Scalability

A production system should support:

- Horizontal scaling
- Stateless services
- Load balancing
- Caching
- Asynchronous processing
- Queue-based communication

---

# Reliability

Key reliability techniques include:

- Retry
- Idempotency
- Circuit Breaker
- Timeout
- Health Checks
- Distributed Tracing

---

# Observability

Every payment system should implement:

- Metrics
- Logging
- Tracing
- Alerting
- Dashboards

---

# Security

Security should include:

- TLS
- Encryption
- Secure APIs
- Device binding
- Fraud detection
- Audit logging

---

# Engineering Trade-offs

Typical design decisions include:

- Consistency vs Availability
- Latency vs Reliability
- Synchronous vs Asynchronous communication
- Retry vs Duplicate Processing
- Performance vs Security

---

# Common Interview Questions

- Design UPI from scratch.
- How would you scale UPI to millions of TPS?
- How would you prevent duplicate transactions?
- How would you handle debit success but credit failure?
- How would you monitor production health?
- How would you improve availability without compromising correctness?

---

# Key Takeaways

- UPI is a distributed payment system.
- High availability alone is not sufficient—financial correctness is equally important.
- Idempotency, observability, security, and reconciliation are essential for production systems.
- A successful architecture balances scalability, reliability, security, and operational simplicity.

---

# What's Next?

The final chapter summarizes the most important UPI interview questions and provides concise, interview-ready answers for different experience levels.
