

# Security

## Overview

Security is one of the most critical aspects of the UPI ecosystem. Since every transaction involves the movement of real money, multiple layers of security are implemented to protect customers, banks, and payment service providers.

UPI security is based on the principle of **defense in depth**, where several independent security controls work together instead of relying on a single mechanism.

---

# Security Objectives

A secure payment system should provide:

- Authentication
- Authorization
- Confidentiality
- Integrity
- Non-repudiation
- Availability
- Fraud prevention

---

# Security Layers

```text
User
   │
Device Security
   │
UPI Application Security
   │
Secure Network Communication
   │
PSP Security
   │
NPCI Security
   │
Bank Security
```

Each layer contributes to protecting the transaction.

---

# Authentication

UPI verifies that the person initiating the transaction is the legitimate account holder.

Common authentication mechanisms include:

- UPI PIN
- Device binding
- Mobile number verification
- SIM association
- Biometrics (where supported)

---

# Authorization

After authentication, participating banks determine whether the transaction should be allowed.

Typical checks include:

- Account status
- Available balance
- Transaction limits
- Risk policies
- Fraud detection rules

---

# Secure Communication

Communication between participants is protected using secure network protocols and encryption to prevent interception or tampering.

---

# Fraud Prevention

Modern UPI systems continuously monitor transactions for suspicious activity.

Examples include:

- Velocity checks
- Unusual transaction patterns
- Device reputation
- Risk scoring
- Blacklisted accounts

---

# Engineering Considerations

Production payment systems should implement:

- Encryption of sensitive data
- Secure key management
- API authentication
- Audit logging
- Rate limiting
- Continuous monitoring
- Incident response procedures

---

# Common Interview Questions

- Why is a UPI PIN required?
- What is the difference between authentication and authorization?
- How does UPI prevent fraud?
- Why is encryption important in payment systems?

---

# Key Takeaways

- Security is implemented at multiple layers.
- Authentication verifies identity.
- Authorization determines whether a payment is permitted.
- Fraud detection and monitoring protect the ecosystem.
- Security is a shared responsibility across UPI applications, PSPs, NPCI, and banks.

---

# What's Next?

The next chapter explains settlement, including how banks reconcile transactions and how funds are settled after successful UPI payments.