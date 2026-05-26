

# CDN Flow Diagram

## Purpose

CDN improves content delivery performance.

Goals:

- Lower latency
- Faster content delivery
- Reduce origin server load
- Improve scalability
- Better global performance

---

## High Level Flow

```text
User
 ↓
DNS Lookup
 ↓
Nearest CDN Edge
 ↓ Cache Hit
Content Response

OR

Cache Miss
 ↓
Origin Server
 ↓
CDN Cache Update
 ↓
User Response
```

---

## Production Flow

```text
Client
 ↓
DNS
 ↓
CDN Edge Location
 ↓
Load Balancer
 ↓
Application Service
 ↓
Database
```

---

## Cache Hit Flow

```text
User Request
 ↓
CDN Edge
 ↓ Cache Hit
Response
```

Benefits:

- Lower latency
- Lower infrastructure load
- Better user experience

---

## Cache Miss Flow

```text
User Request
 ↓
CDN Edge
 ↓ Miss
Origin Server
 ↓
CDN Store Content
 ↓
Response
```

Problems:

- Higher latency
- Origin server dependency

---

## Why CDN?

Without CDN:

```text
Global User
 ↓
Single Region Server
 ↓
Higher Latency
```

With CDN:

```text
Global User
 ↓
Nearest Edge Location
 ↓
Faster Delivery
```

---

## Interview Notes

CDN helps:

- Images
- Videos
- CSS
- JavaScript
- Static assets

Common discussion:

```text
CDN vs Cache
Cache Hit Ratio
CDN Invalidation
```

---

## Quick Revision

```text
CDN
→ Faster Delivery

Cache Hit
→ Faster Response

Cache Miss
→ Origin Fetch

Edge Location
→ Lower Latency
```