

# Service Discovery

## What is Service Discovery?

Service Discovery is a mechanism that helps services dynamically find and communicate with other services in distributed systems without hardcoding IP addresses or hostnames.

Instead of storing service locations manually, services register themselves into a registry and clients discover them dynamically.

---

## Why Service Discovery?

Problems without service discovery:

- Dynamic IP changes
- Container scaling changes instances frequently
- Hardcoded endpoints break deployments
- Manual configuration becomes difficult
- Multi-region systems increase complexity

Service discovery improves:

- Scalability
- Reliability
- Service availability
- Infrastructure automation
- Fault tolerance

---

## High Level Architecture

```text
+----------------+
| Service A       |
+--------+--------+
         |
         | Query
         v
+----------------------+
| Service Registry     |
| (Consul / Eureka)    |
+-----------+----------+
            |
            | Returns Instance
            v
+----------------------+
| Service B            |
| Multiple Instances   |
+----------------------+
```

---

## Core Components

### Service Registry

Stores available service instances.

Examples:

- Consul
- Eureka
- ZooKeeper
- Kubernetes DNS
- etcd

---

### Service Registration

Services register themselves during startup.

Example:

```text
Payment Service
10.0.0.12:8080
Region=us-east
Status=Healthy
```

---

### Health Check

Registry continuously verifies service health.

Health checks:

- HTTP endpoint
- TCP probe
- Heartbeat mechanism
- Kubernetes liveness probe

Unhealthy services are removed automatically.

---

### Service Lookup

Clients request service location dynamically.

Example:

```text
Get Inventory Service
→ inventory-service
→ 10.0.0.15:8080
```

---

## Discovery Models

### Client Side Discovery

Client directly queries registry.

Flow:

```text
Client
 ↓
Service Registry
 ↓
Target Service
```

Examples:

- Netflix Eureka
- Consul

Advantages:

- Lower latency
- Better routing control

Disadvantages:

- Client complexity increases

---

### Server Side Discovery

Load balancer queries registry.

Flow:

```text
Client
 ↓
Load Balancer
 ↓
Registry
 ↓
Service
```

Examples:

- Kubernetes Service
- AWS ELB
- Service Mesh

Advantages:

- Simpler clients
- Centralized routing

Disadvantages:

- Additional infrastructure layer

---

## Service Discovery in Kubernetes

Kubernetes provides built-in discovery.

Example:

```text
payment-service.default.svc.cluster.local
```

Components:

- CoreDNS
- Service abstraction
- Endpoint objects

---

## Production Challenges

Common issues:

- Registry failure
- Stale instance data
- Network partition
- Slow health checks
- DNS propagation delay

Solutions:

- Registry replication
- TTL expiration
- Retry logic
- Circuit breaker
- Multi-region registry deployment

---

## Production Examples

Examples:

- Kubernetes platform
- Microservices platform
- Service Mesh architecture
- Cloud native systems
- Enterprise distributed systems

---

## Interview Questions

1. What is service discovery?

2. Why do microservices need service discovery?

3. Client-side vs server-side discovery?

4. How does Kubernetes service discovery work?

5. How are unhealthy instances removed?

6. What happens if registry becomes unavailable?

---

## Quick Revision

- Service discovery removes hardcoded endpoints
- Registry stores service locations
- Health checks remove failed instances
- Client-side discovery gives routing control
- Server-side discovery simplifies clients
- Kubernetes provides built-in discovery
- Service discovery improves scalability and reliability