

# Payment Service Provider (PSP)

## Overview

A **Payment Service Provider (PSP)** connects UPI applications with the NPCI UPI infrastructure. It acts as the technical gateway that validates, processes, and forwards payment requests between the application and participating banks.

Every UPI transaction initiated from a mobile application passes through a PSP before reaching NPCI.

---

# Why is a PSP Needed?

A mobile application should not communicate directly with NPCI or every participating bank.

Instead, the PSP provides a standardized interface for:

- Processing payment requests
- Authenticating users
- Validating requests
- Communicating with NPCI
- Receiving transaction responses

This simplifies application development while ensuring compliance with UPI standards.

---

# High-Level Flow

```text
Customer
    │
    ▼
UPI App
    │
    ▼
PSP
    │
    ▼
NPCI
    │
    ▼
Banks
```

---

# Responsibilities

A PSP is responsible for:

- Receiving requests from the UPI application.
- Validating transaction data.
- Authenticating the customer where applicable.
- Forwarding requests to NPCI.
- Receiving responses from NPCI.
- Returning the final transaction status to the application.

A PSP does **not**:

- Hold customer balances.
- Debit or credit bank accounts.
- Perform inter-bank settlement.

---

# PSP vs UPI Application

These terms are often confused.

- **UPI Application (TPAP):** The customer-facing mobile app.
- **PSP:** The backend service that connects the application to the UPI ecosystem.

The application provides the user experience, while the PSP provides payment connectivity.

---

# Engineering Considerations

A production-grade PSP should provide:

- High availability
- Low latency
- Secure communication
- Request validation
- Retry handling
- Idempotency
- Monitoring and logging
- Fraud detection integration

---

# Common Interview Questions

- What is the role of a PSP?
- Why can't a UPI application directly connect to NPCI?
- Does a PSP store customer money?
- What happens if the PSP is unavailable?

---

# Key Takeaways

- A PSP is the technical bridge between UPI applications and NPCI.
- It validates and forwards payment requests.
- Banks remain responsible for account operations.
- A PSP focuses on reliable, secure, and scalable payment processing.

---

# What's Next?

The next chapter explains the role of participating banks and how they authenticate customers, maintain accounts, and perform debit and credit operations during a UPI transaction.
