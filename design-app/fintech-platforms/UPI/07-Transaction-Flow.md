

# UPI Transaction Flow

## Overview

A UPI transaction involves multiple participants working together to securely transfer money from the sender's bank account to the receiver's bank account.

Although the payment appears instantaneous to the user, several validation, routing, authorization, and accounting steps occur behind the scenes.

---

# High-Level Transaction Flow

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
   ├────────► Sender Bank
   │              │
   │         Debit Account
   │              │
   └────────► Receiver Bank
                  │
             Credit Account
                  │
                  ▼
              Receiver
```

---

# Step-by-Step Flow

## Step 1 – Payment Initiation

The sender enters the amount, selects the recipient, and initiates the payment using a UPI application.

---

## Step 2 – Authentication

The customer authenticates the transaction using the UPI PIN.

The application securely sends the payment request to the PSP.

---

## Step 3 – Request Validation

The PSP validates the request format, verifies required information, and forwards the request to NPCI.

---

## Step 4 – Request Routing

NPCI identifies the sender and receiver banks and routes the payment request to the appropriate institutions.

---

## Step 5 – Debit Processing

The sender bank:

- Verifies account status.
- Checks available balance.
- Performs fraud and risk checks.
- Debits the customer's account.

---

## Step 6 – Credit Processing

The receiver bank validates the beneficiary account and credits the amount.

---

## Step 7 – Response

The receiver bank sends the transaction result back through NPCI.

NPCI forwards the response to the PSP, which notifies the UPI application.

Both sender and receiver receive confirmation of the completed transaction.

---

# What Happens Behind the Scenes?

During a successful payment, multiple internal operations occur:

- Customer authentication
- Request validation
- Risk and fraud checks
- Balance verification
- Debit processing
- Credit processing
- Ledger updates
- Audit logging
- Notification delivery

These operations are completed within a few seconds under normal conditions.

---

# Failure Scenarios

A transaction may fail due to:

- Incorrect UPI PIN
- Insufficient balance
- Bank downtime
- Network timeout
- Invalid beneficiary account
- Technical issues

Modern payment systems include retry, reconciliation, and recovery mechanisms to maintain transaction consistency.

---

# Key Takeaways

- A UPI payment involves multiple independent participants.
- NPCI coordinates routing between participating banks.
- Banks perform the actual debit and credit operations.
- Validation, security, and ledger updates occur before a transaction is confirmed.

---

# What's Next?

The next chapter explains how UPI protects transactions using authentication, encryption, secure communication, and fraud prevention mechanisms.
