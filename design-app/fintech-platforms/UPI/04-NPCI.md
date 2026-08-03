

# National Payments Corporation of India (NPCI)

## Overview

The **National Payments Corporation of India (NPCI)** is the organization responsible for developing and operating India's retail payment infrastructure. It was established to provide secure, interoperable, and scalable payment systems for the country.

NPCI operates several payment platforms, including:

- UPI (Unified Payments Interface)
- IMPS (Immediate Payment Service)
- RuPay
- NACH
- FASTag
- Bharat BillPay (BBPS)
- AePS (Aadhaar Enabled Payment System)

Within the UPI ecosystem, NPCI acts as the **central payment switch**.

---

# Why Does NPCI Exist?

Imagine every bank had to connect directly with every other bank.

With 100 participating banks, thousands of individual integrations would be required, making the ecosystem difficult to maintain and scale.

NPCI simplifies this by acting as a central hub. Every participant integrates once with NPCI instead of integrating with every other bank.

```text
Without NPCI

Bank A ───── Bank B
   │            │
   ├────────────┤
   │            │
Bank C ───── Bank D

Many direct integrations
```

```text
With NPCI

Bank A
   │
Bank B
   │
Bank C
   │
Bank D
   │
   ▼
 NPCI
```

---

# Responsibilities

NPCI is responsible for:

- Receiving payment requests.
- Identifying the destination bank.
- Routing payment messages.
- Exchanging transaction responses.
- Supporting inter-bank settlement processes.
- Maintaining common UPI standards.
- Ensuring interoperability among participants.

NPCI does **not**:

- Store customer balances.
- Debit customer accounts.
- Credit customer accounts.
- Act as a commercial bank.

Those responsibilities remain with participating banks.

---

# High-Level Request Flow

```text
Customer
    │
UPI App
    │
PSP
    │
NPCI
   ├────────► Sender Bank
   │
   └────────► Receiver Bank
```

NPCI coordinates communication but does not own customer accounts.

---

# Engineering Characteristics

The UPI switch must provide:

- Extremely high availability.
- Low latency.
- Massive scalability.
- Fault tolerance.
- Secure message exchange.
- Reliable routing.

Because millions of transactions occur every day, the switching infrastructure is designed to minimize downtime while maintaining consistent transaction processing.

---

# Key Takeaways

- NPCI is the central payment infrastructure operator.
- NPCI enables interoperability across participating banks and payment applications.
- NPCI routes payment requests but does not hold customer money.
- Banks remain responsible for debits, credits, and account management.

---

# What's Next?

The next chapter explains the role of the Payment Service Provider (PSP), which connects UPI applications to the NPCI infrastructure.