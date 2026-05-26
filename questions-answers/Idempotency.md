# Idempotency

## Why Idempotency Matters?

- Retry handling
- Distributed systems reliability
- Payment systems safety
- Network failure recovery
- Duplicate request prevention

## What Is Idempotency?

Same operation executed multiple times
↓
Same final result

Examples:
- Idempotent API
- Non Idempotent API

## HTTP Methods

GET
PUT
DELETE
POST

Idempotent vs Non Idempotent behavior

## Payment System Example

Client
↓
Payment Request
↓ Timeout
Retry
↓
Duplicate Charge Risk

Solution:

Idempotency Key

payment_123456

Retry
↓
Same Result Returned

## Production Strategy

- Idempotency Key Store
- Redis
- Database Record
- Request Fingerprint
- Expiration Window

## Production Examples

Payment Platform
Order Platform
Notification Retry
Webhook Processing

## Interview Shortcut

Retry Safe
→ Idempotency

Duplicate Protection
→ Idempotency Key

## Interview Questions

1. What is idempotency?
2. PUT vs POST idempotency?
3. Why payment systems need idempotency?
4. Retry handling strategy?
5. Idempotency key storage?
6. Distributed systems retry protection?

## Quick Revision

- Prevent duplicate operations
- Important for retries
- Critical for payments
- Idempotency key prevents duplicate processing
- Distributed systems heavily use idempotency