# Failure Scenarios

## Overview

In a distributed payment system, failures are inevitable. Networks can become unavailable, banks may experience downtime, and communication between participants may be interrupted.

A well-designed payment system should handle failures gracefully while ensuring that customer money is never lost or duplicated.

---

# Why Failure Handling Matters

Payment systems deal with real money.

The system must guarantee:

- No money is created.
- No money is lost.
- No customer is charged twice.
- Every transaction reaches a final state.
- Every transaction can be audited.

These properties are more important than processing speed.

---

# Common Failure Scenarios

## 1. Incorrect UPI PIN

Authentication fails before the transaction reaches the sender bank.

Result:

- Transaction rejected.
- No debit.
- No credit.

---

## 2. Insufficient Balance

The sender bank verifies the balance and rejects the transaction.

Result:

- No debit.
- No credit.

---

## 3. Sender Bank Unavailable

The sender bank cannot process the request.

Result:

- Transaction fails or times out.
- Customer may retry later.

---

## 4. Receiver Bank Unavailable

The sender bank may have already debited the customer.

The receiver bank cannot accept the credit.

Possible outcomes:

- Retry
- Reversal
- Pending status

This is one of the most important production scenarios.

---

## 5. NPCI Timeout

NPCI does not receive a response from one of the participants.

Result:

- Transaction marked as pending.
- Status inquiry may be performed later.

---

## 6. Network Failure

Communication between participants is interrupted.

Possible outcomes:

- Retry
- Timeout
- Status reconciliation

---

## 7. Duplicate Request

The same request reaches the system multiple times because of retries.

The payment system must detect duplicates and avoid processing the transaction twice.

This is where **idempotency** becomes critical.

---

# Recovery Mechanisms

Production payment systems use several recovery mechanisms:

- Automatic retry
- Reconciliation
- Transaction status inquiry
- Reversal
- Manual investigation (rare cases)

These mechanisms ensure that every transaction eventually reaches a consistent final state.

---

# Engineering Considerations

Reliable payment systems should provide:

- Idempotent APIs
- Distributed tracing
- Audit logs
- Retry policies
- Dead-letter handling
- Monitoring and alerting
- Automated reconciliation
- Disaster recovery

---

# Common Interview Questions

- What happens if money is debited but not credited?
- Why is idempotency important?
- How do payment systems avoid duplicate transactions?
- What is reconciliation?
- How would you recover a partially completed payment?

---

# Key Takeaways

- Failures are expected in distributed systems.
- Every payment must eventually reach a consistent state.
- Idempotency prevents duplicate transactions.
- Reconciliation ensures financial correctness.
- Reliability is more important than raw performance in payment systems.

---

# What's Next?

The next chapter brings together everything you've learned and explains how to design a scalable, secure, and highly available UPI-like payment system from a software architecture perspective.
