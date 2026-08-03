# UPI Architecture

## Overview

UPI is a distributed payment ecosystem rather than a single application. Multiple organizations collaborate to process every transaction securely, reliably, and in real time.

At a high level, a UPI payment flows through four major layers:

```text
Customer
    │
    ▼
UPI Application (TPAP)
    │
    ▼
Payment Service Provider (PSP)
    │
    ▼
NPCI UPI Switch
    │
    ▼
Banks
```

Each layer has a clearly defined responsibility, allowing banks and payment applications to interoperate while following the same UPI standards.

---

# Major Components

## Customer

The person or business initiating or receiving a payment.

---

## UPI Application (TPAP)

The mobile application used by customers.

Examples:

- Google Pay
- PhonePe
- Paytm
- BHIM

Responsibilities:

- User interface
- Payment initiation
- Account management
- QR scanning
- Transaction history

---

## Payment Service Provider (PSP)

Acts as the bridge between the UPI application and NPCI.

Responsibilities:

- Validate requests
- Authenticate users
- Forward requests to NPCI
- Receive responses
- Notify the application

---

## NPCI UPI Switch

NPCI operates the central switching infrastructure.

Responsibilities:

- Route payment requests
- Identify destination banks
- Coordinate participating institutions
- Exchange payment messages
- Support settlement processes

NPCI does **not** hold customer money.

---

## Banks

Banks maintain customer accounts and are responsible for:

- Balance verification
- Debit operations
- Credit operations
- Account validation
- Ledger management

---

# End-to-End Architecture

```text
Sender
    │
    ▼
UPI App
    │
    ▼
PSP
    │
    ▼
NPCI UPI Switch
    │
    ▼
Sender Bank
    │
    ▼
Receiver Bank
    │
    ▼
Receiver
```

---

# Design Principles

The UPI ecosystem is built around several key principles:

- Standardized interfaces
- Interoperability
- Real-time processing
- High availability
- Security by design
- Horizontal scalability

---

# Why a Central Switch?

Without NPCI, every bank would need direct integrations with every other bank.

With NPCI acting as the central switch, each participant integrates once using common standards, significantly reducing complexity and improving interoperability.

---

# Key Takeaways

- UPI is a distributed payment ecosystem.
- Each participant has a well-defined responsibility.
- NPCI provides centralized routing, not banking services.
- Banks own customer accounts and perform debits and credits.
- Standardization enables interoperability across all participating banks and applications.

---

# What's Next?

The next chapter explores NPCI in detail, including its responsibilities, internal role in the UPI ecosystem, and why it is central to India's digital payment infrastructure.
