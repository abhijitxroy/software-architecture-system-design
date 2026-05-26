

# Load Balancer System Design

## Problem Statement

Design a load balancer that distributes incoming traffic across multiple backend servers to improve scalability, reliability and availability.

Used in:

- Microservices
- Kubernetes Platforms
- Cloud Native Systems
- API Platforms
- AI Platforms
- Ecommerce Systems

Examples:

- NGINX
- HAProxy
- AWS ELB
- Envoy

System should support:

- Traffic Distribution
- Health Checks
- Failover
- SSL Termination
- Session Persistence
- Auto Scaling Integration
- Load Distribution Algorithms

---

## Functional Requirements

### Core Features

- Route traffic
- Health monitoring
- Backend failover
- SSL termination
- Sticky sessions
- Traffic balancing
- Retry support

---

## Non Functional Requirements

### Scalability

- Millions of requests/minute

### Availability

- 99.99% uptime

### Reliability

- No single point of failure

### Latency

- Routing latency under milliseconds

---

## Why Load Balancer Needed

Without load balancer:

```text
Client
↓
Single Server
↓
Overload
↓
Failure
```

Goal:

```text
Distribute Traffic
↓
Improve Availability
```

---

## Load Balancing Algorithms

### Round Robin

Flow:

```text
Request1 → Server1
Request2 → Server2
Request3 → Server3
```

Benefits:

- Simple
- Equal distribution

---

### Least Connections

Flow:

```text
Route Request
↓
Server With Lowest Connections
```

Benefits:

- Better uneven workload handling

---

### Weighted Round Robin

Example:

```text
Server1 Weight=5
Server2 Weight=2
```

Benefits:

- Handle server capacity differences

---

### IP Hash

Purpose:

```text
Same User
↓
Same Backend
```

Useful for:

- Sticky session

---

## Health Check

Purpose:

Detect unhealthy server.

Flow:

```text
Health Probe
↓
Backend Server
↓
Healthy ?
```

If failed:

```text
Remove Server
From Pool
```

---

## High Level Design

```text
Client
 |
DNS
 |
Load Balancer
 |
Server1
Server2
Server3
```

---

## Request Flow

```text
Client Request
↓
Load Balancer
↓
Algorithm Selection
↓
Healthy Backend
↓
Response
```

---

## Layer 4 vs Layer 7

| Feature | Layer 4 | Layer 7 |
|----------|----------|----------|
| Operates On | TCP/UDP | HTTP |
| Routing Logic | Network | Application |
| SSL Handling | Limited | Better |
| Performance | Faster | More Flexible |

---

## Scaling Strategy

### Horizontal Scaling

Add backend servers.

### Multi Region

Improve availability.

### Auto Scaling

Scale backend dynamically.

---

## Reliability

Strategies:

- Active passive failover
- Health checks
- Retry mechanism
- Redundant load balancers

---

## Tradeoffs

| Choice | Benefit | Drawback |
|----------|----------|-----------|
| Sticky session | Session consistency | Uneven traffic |
| Round robin | Simple | Ignore server load |
| Least connection | Better balancing | More tracking cost |

---

## Interview Questions

1. Layer 4 vs Layer 7?
2. Round robin vs least connection?
3. Why sticky session needed?
4. Why health check important?
5. Why load balancer prevents failure?
6. Why active passive failover useful?

---

## Quick Revision

- Load balancer distributes traffic
- Health check removes bad nodes
- Least connection handles uneven load
- Layer 7 supports smart routing
- Sticky session improves session handling
- Failover improves availability