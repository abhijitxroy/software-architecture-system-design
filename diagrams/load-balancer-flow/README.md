

# Load Balancer Flow Diagram

## Purpose

Load Balancer distributes traffic across multiple servers.

Goals:

- Improve availability
- Increase scalability
- Prevent overload
- Improve reliability
- Eliminate single server bottleneck

---

## High Level Flow

```text
Client Requests
      ↓
+----------------+
| Load Balancer  |
+----------------+

 ↓      ↓      ↓

Server A
Server B
Server C
```

Load Balancer distributes requests.

---

## Production Flow

```text
Client
 ↓
CDN
 ↓
Load Balancer
 ↓
Application Servers
 ↓
Database
```

---

## Why Load Balancer?

Without Load Balancer:

```text
Users
 ↓
Single Server
 ↓
Traffic Spike
 ↓
Server Failure
```

Problems:

- Single point of failure
- Lower scalability
- Higher downtime risk

With Load Balancer:

```text
Traffic Distribution
↓
Multiple Servers
↓
Better Availability
```

---

## Common Algorithms

### Round Robin

```text
Request 1 → Server A
Request 2 → Server B
Request 3 → Server C
```

Best For:

- Similar server capacity

---

### Least Connections

```text
New Request
↓
Server With Lowest Connections
```

Best For:

- Uneven workloads

---

### IP Hash

```text
Client IP
↓
Same Server Mapping
```

Best For:

- Session stickiness

---

## Production Examples

Load Balancer commonly used in:

- API platforms
- Microservices
- E Commerce systems
- Media platforms

---

## Interview Notes

Common discussion:

```text
Load Balancer vs API Gateway

L4 vs L7 Load Balancer

Sticky Session
```

---

## Quick Revision

```text
Load Balancer
→ Traffic Distribution

Round Robin
→ Equal Distribution

Least Connections
→ Dynamic Distribution

IP Hash
→ Session Affinity
```