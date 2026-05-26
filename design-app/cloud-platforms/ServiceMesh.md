

# Service Mesh

## What is Service Mesh?

Service Mesh is an infrastructure layer that manages service-to-service communication inside distributed systems and microservices environments.

It provides networking capabilities without adding communication logic inside application code.

A service mesh handles:

- Traffic management
- Service discovery
- Security
- Observability
- Load balancing
- Retry policies
- Circuit breaking

Instead of developers implementing these capabilities inside every service, service mesh moves them into infrastructure.

---

## Why Service Mesh?

Problems without service mesh:

- Complex service communication
- Duplicate networking logic
- Difficult observability
- Security inconsistencies
- Manual retry handling
- Hard traffic routing

Service mesh improves:

- Reliability
- Security
- Visibility
- Operational simplicity
- Traffic control

---

## High Level Architecture

```text
+-------------+      +-------------+
| Service A   | ---> | Service B   |
| Sidecar     |      | Sidecar     |
+------+------+      +------+------+
       |                    |
       +--------+-----------+
                |
                v
      +-------------------+
      | Control Plane     |
      | Istio / Linkerd   |
      +-------------------+
```

---

## Core Components

### Data Plane

Handles actual traffic between services.

Responsibilities:

- Routing
- Load balancing
- Retry logic
- Encryption
- Metrics collection

Usually implemented using sidecar proxies.

Examples:

- Envoy Proxy
- Linkerd Proxy

---

### Control Plane

Manages configuration and policies.

Responsibilities:

- Traffic rules
- Certificate management
- Policy enforcement
- Service discovery integration

Examples:

- Istio Control Plane
- Linkerd Control Plane

---

### Sidecar Proxy

A proxy container deployed alongside application containers.

Flow:

```text
Application
    ↓
Sidecar Proxy
    ↓
Network
    ↓
Remote Sidecar
    ↓
Target Service
```

Benefits:

- No application code changes
- Unified traffic handling
- Consistent security policies

---

## Traffic Management

Service mesh supports:

- Load balancing
- Retry mechanism
- Timeout policies
- Circuit breaker
- Traffic mirroring
- Canary deployment
- Blue Green deployment

Example:

```text
90% → Service V1
10% → Service V2
```

Useful for controlled production rollout.

---

## Security Features

Capabilities:

- Mutual TLS (mTLS)
- Identity verification
- Encryption in transit
- Authorization policies
- Zero trust networking

Example:

```text
Service A <TLS> Service B
```

---

## Observability

Service mesh provides visibility automatically.

Metrics:

- Request latency
- Error rate
- Throughput
- Traffic volume
- Dependency graph

Tools:

- Prometheus
- Grafana
- Jaeger
- Kiali

---

## Popular Service Mesh Solutions

### Istio

Features:

- Envoy proxy
- Traffic management
- Security policies
- Advanced observability

Best for:

- Large Kubernetes platforms

---

### Linkerd

Features:

- Lightweight deployment
- Simpler operations
- Lower resource usage

Best for:

- Small to medium clusters

---

### Consul Connect

Features:

- Service networking
- Multi-platform support
- Service discovery integration

---

## Production Challenges

Common issues:

- Sidecar overhead
- Increased latency
- Operational complexity
- Resource consumption
- Certificate rotation challenges

Solutions:

- Proxy optimization
- Monitoring
- Resource tuning
- Automation pipelines

---

## Production Examples

Examples:

- Kubernetes platform
- Enterprise microservices
- Cloud native systems
- Multi-cluster deployments
- AI platform infrastructure

---

## Interview Questions

1. What is service mesh?

2. Why use service mesh in microservices?

3. Data plane vs control plane?

4. What is sidecar proxy?

5. How does mTLS work?

6. Istio vs Linkerd?

7. Service discovery vs service mesh?

---

## Quick Revision

- Service mesh manages service communication
- Sidecar proxies handle networking logic
- Control plane manages policies
- Data plane handles traffic
- mTLS improves service security
- Traffic routing supports canary deployment
- Service mesh improves observability and reliability