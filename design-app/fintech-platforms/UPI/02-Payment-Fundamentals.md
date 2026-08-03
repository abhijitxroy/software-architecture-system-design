

# Payment Fundamentals

## Why Learn Payment Fundamentals?

Before understanding UPI, it is important to understand how digital payment systems work in general. Nearly every modern payment system—UPI, IMPS, NEFT, RTGS, Visa, Mastercard, Pix, FedNow, or SEPA Instant—follows the same high-level principles.

Learning these fundamentals makes it easier to understand any payment architecture.

---

# Evolution of Payments

```text
Cash
    ↓
Cheque
    ↓
NEFT
    ↓
RTGS
    ↓
IMPS
    ↓
UPI
```

Each generation improved one or more aspects of the previous system, such as speed, convenience, availability, interoperability, security, or user experience.

---

# Generic Payment Ecosystem

Every payment system consists of a few common participants.

```text
Customer
    │
    ▼
Payment Application
    │
    ▼
Payment Service Provider
    │
    ▼
Payment Network / Switch
    │
    ▼
Banks
    │
    ▼
Settlement System
```

Although implementation details differ, these building blocks are present in almost every modern payment network.

---

# Core Concepts

## Authentication

Verifies **who** is initiating the payment.

Examples:

- UPI PIN
- Password
- Biometrics
- OTP

---

## Authorization

Determines whether the requested payment is allowed.

Examples:

- Sufficient balance
- Daily transaction limit
- Fraud checks
- Account status

---

## Clearing

The process of exchanging payment instructions between participating financial institutions.

---

## Settlement

The actual transfer of funds between financial institutions after payment instructions have been accepted.

---

# Push vs Pull Payments

## Push Payment

The payer initiates the transaction.

Examples:

- UPI Pay
- IMPS
- NEFT

## Pull Payment

The payee requests money from the payer.

Examples:

- UPI Collect
- Auto-debit mandates
- Some card payment scenarios

---

# Real-Time vs Deferred Settlement

Real-time payment confirmation does not necessarily mean banks settle funds immediately.

Many payment systems provide instant confirmation while settlement between banks occurs later according to predefined settlement cycles.

---

# Key Takeaways

- Every payment system follows similar architectural principles.
- Authentication and authorization serve different purposes.
- Clearing and settlement are separate processes.
- Push and pull payments solve different business problems.
- Understanding these concepts is essential before studying UPI.

---

# What's Next?

The next chapter introduces the overall UPI architecture and explains how all major participants work together to process real-time payments.