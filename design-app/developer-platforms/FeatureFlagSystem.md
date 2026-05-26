

# Feature Flag System Design

## Problem Statement

Design a feature flag system that enables teams to enable or disable features dynamically without redeploying applications.

Used in:

- Canary Deployment
- A/B Testing
- Gradual Rollout
- Experimentation Platform
- Emergency Kill Switch
- Premium Feature Access

System should support:

- Feature Toggle
- User Targeting
- Percentage Rollout
- Kill Switch
- Environment Specific Config
- Real Time Update
- Audit History

---

## Functional Requirements

### Core Features

- Create feature flag
- Update feature flag
- Delete feature flag
- Enable feature dynamically
- User targeting
- Percentage rollout
- SDK integration
- Audit tracking

---

## Non Functional Requirements

### Scalability

- Millions of flag evaluations/sec
- Thousands of applications

### Availability

- 99.99% uptime

### Reliability

- No configuration loss

### Latency

- Feature evaluation under 10 ms

---

## Why Feature Flags Needed

Without feature flags:

```text
Code Change
↓
Build
↓
Deploy
↓
Release
```

Problem:

```text
Slow rollout
Risky deployment
Hard rollback
```

With feature flags:

```text
Deploy Code
↓
Enable Feature Later
```

---

## Core Concepts

### Boolean Flag

Example:

```text
new_checkout=true
```

Behavior:

```text
Enabled
→ New Experience

Disabled
→ Old Experience
```

---

### Percentage Rollout

Example:

```text
5%
↓
20%
↓
50%
↓
100%
```

Benefits:

- Safer rollout
- Lower production risk

---

### Canary Release

Example:

```text
Internal Users
↓
5% Users
↓
20% Users
↓
Global Rollout
```

Goal:

Reduce blast radius.

---

### Kill Switch

Purpose:

```text
Disable feature immediately
```

Example:

```text
Payment Failure Spike
↓
Disable New Checkout
```

---

### User Targeting

Example:

```text
Country = India
Tier = Premium
AppVersion >= 2.5
```

Benefits:

- Controlled release
- Personalization

---

## API Design

### Create Flag

```http
POST /flags
```

### Get Flag

```http
GET /flags/{flagName}
```

Response:

```json
{
 "flag":"new_checkout",
 "enabled":true
}
```

---

## High Level Design

```text
Application SDK
 |
Feature Flag SDK
 |
Config Service
 |
Redis Cache
 |
Database
 |
Audit Pipeline
```

---

## Evaluation Flow

```text
Request
↓
SDK Check Cache
↓
Flag Evaluation
↓
Target Rules
↓
Return Decision
```

---

## Scaling Strategy

### Redis

Responsibilities:

- Hot flag cache
- Low latency lookup

### SDK Cache

Benefits:

- Lower latency
- Fewer backend calls

### Database

Store:

- Rules
- Audit history
- Rollout configuration

---

## Reliability

Strategies:

- Cache fallback
- Replication
- Version history
- Multi region deployment

---

## Tradeoffs

| Choice | Benefit | Drawback |
|----------|----------|-----------|
| SDK cache | Faster evaluation | Stale config |
| Dynamic config | Safer rollout | More complexity |
| Percentage rollout | Lower risk | Extra evaluation logic |

---

## Interview Questions

1. Why feature flags needed?
2. Canary release vs A/B testing?
3. Why SDK cache needed?
4. How percentage rollout works?
5. Why kill switch useful?
6. How stale configuration handled?

---

## Quick Revision

- Feature flag decouples deployment from release
- Canary reduces rollout risk
- Kill switch improves reliability
- Redis improves lookup latency
- SDK cache improves performance
- Percentage rollout improves safety