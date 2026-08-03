

# Participating Banks

## Overview

Banks are the financial institutions that own customer accounts and ultimately move money during a UPI transaction. While UPI applications, PSPs, and NPCI coordinate the payment, only banks can debit and credit customer accounts.

Every successful UPI payment eventually results in a debit from one bank account and a credit to another.

---

# Why Are Banks Required?

Customer money is always held by banks, not by UPI applications or NPCIs.

Banks are responsible for:

- Maintaining customer accounts
- Managing account balances
- Performing debit operations
- Performing credit operations
- Recording transactions in their ledgers
- Enforcing banking regulations

---

# Bank Roles in UPI

## Sender (Remitter) Bank

The sender bank:

- Authenticates the customer.
- Verifies account status.
- Checks available balance.
- Debits the customer's account.
- Records the transaction.

---

## Receiver (Beneficiary) Bank

The receiver bank:

- Validates the destination account.
- Credits the beneficiary account.
- Updates its ledger.
- Confirms successful credit.

---

# High-Level Flow

```text
Customer
    │
UPI App
    │
PSP
    │
NPCI
   ├────────► Sender Bank (Debit)
   │
   └────────► Receiver Bank (Credit)
```

The banks are responsible for moving customer funds. NPCI coordinates the communication but does not transfer customer balances itself.

---

# Responsibilities

Participating banks are responsible for:

- Customer authentication support
- Account validation
- Balance verification
- Debit processing
- Credit processing
- Ledger management
- Transaction history
- Regulatory compliance

---

# Engineering Considerations

A production banking platform should provide:

- High availability
- Strong consistency for account balances
- Low transaction latency
- Secure APIs
- Audit logging
- Fraud detection integration
- Disaster recovery
- Regulatory compliance

---

# Common Interview Questions

- Why can only banks debit and credit customer accounts?
- What is the difference between the sender bank and receiver bank?
- Does NPCI maintain customer balances?
- What happens if the sender bank is unavailable?

---

# Key Takeaways

- Banks own customer accounts and money.
- Sender banks perform debits.
- Receiver banks perform credits.
- NPCI coordinates transactions but does not maintain customer balances.
- Correct ledger management is critical for financial consistency.

---

# What's Next?

The next chapter follows a complete UPI transaction from payment initiation to final confirmation, explaining every step in the end-to-end transaction flow.
