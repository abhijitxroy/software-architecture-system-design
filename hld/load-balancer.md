# Load Balancer

## Definition

Load balancer distributes incoming traffic across multiple backend servers to improve availability, scalability and reliability.

---

## Why Needed?

- Prevent server overload
- Improve availability
- Improve fault tolerance
- Scale horizontally
- Reduce response time

Example:

Without load balancer:

```text
Users → Server1
```

Problem:

- Server crash → Application down
- Traffic spike → Slow response

With load balancer:

```text
Users
  |
Load Balancer
 /   |   \
S1   S2   S3
```

---

## How It Works?

Steps:

1. Client sends request
2. Load balancer receives request
3. Routing algorithm decides backend server
4. Request forwarded
5. Server sends response

---

## Layer 4 vs Layer 7

| Feature | Layer 4 | Layer 7 |
|----------|----------|----------|
| Layer | Transport Layer | Application Layer |
| Works On | TCP / UDP | HTTP / HTTPS |
| Routing | IP + Port | URL + Header + Cookie |
| Speed | Faster | Slightly Slower |
| Smart Routing | No | Yes |

Interview Tip:

Layer 4 → Faster

Layer 7 → Smarter

---

## Load Balancing Algorithms

### 1. Round Robin

Request distributed sequentially.

Example:

```text
Request1 → Server1

Request2 → Server2

Request3 → Server3

Request4 → Server1
```

Best for:

- Similar server capacity

---

### 2. Least Connection

Request goes to server with minimum active connections.

Best for:

- Variable workload
- Long running requests

---

### 3. IP Hash

Same client IP goes to same backend server.

Best for:

- Session persistence
- Sticky session

---

## Sticky Session

User always connects to same backend server.

Example:

```text
User-A → Server2

User-A → Server2

User-A → Server2
```

Needed when:

- Session stored locally
- Shopping cart applications

Problem:

Server failure can lose session.

Solution:

Use Redis session store.

---

## Health Check

Load balancer checks server health continuously.

Example:

```text
GET /health
```

If unhealthy:

```text
Remove server from traffic
```

---

## Production Examples

- NGINX
- HAProxy
- AWS ALB
- AWS NLB
- Envoy

---

## Real World Usage

Used in:

- Netflix
- Amazon
- Instagram
- Uber
- Payment Systems

---

## Interview Questions

### Q1. Layer 4 vs Layer 7?

Layer 4 → IP + Port routing

Layer 7 → Content aware routing

---

### Q2. Why Sticky Session needed?

Maintain user session consistency.

---

### Q3. Load Balancer vs API Gateway?

| Feature | Load Balancer | API Gateway |
|----------|---------------|--------------|
| Traffic Distribution | Yes | No |
| Authentication | No | Yes |
| Rate Limiting | No | Yes |
| Routing | Backend Server | API Endpoint |

---

## Quick Revision

- Layer 4 → Fast
- Layer 7 → Smart
- Round Robin → Sequential
- Least Connection → Least busy server
- IP Hash → Same user same server
- Sticky Session → User affinity
- Health Check → Remove failed server