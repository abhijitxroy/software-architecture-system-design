# Horizontal Scaling vs Vertical Scaling

## Definition

Scaling means increasing system capacity to handle growing traffic and workload.

Two common scaling approaches:

1. Vertical Scaling (Scale Up)
2. Horizontal Scaling (Scale Out)

---

## Vertical Scaling (Scale Up)

Increase resources of existing machine.

Example:

Before:

```text
Server

4 CPU

16 GB RAM
```

After Upgrade:

```text
Server

16 CPU

64 GB RAM
```

Architecture:

```text
Users

↓

Application Server

(Bigger Machine)
```

Benefits:

- Simple implementation
- No architecture change
- Easy maintenance

Problems:

- Hardware limit exists
- Expensive upgrades
- Single point of failure

Examples:

- Upgrade EC2 instance
- Increase RAM
- Faster SSD
- More CPU

---

## Horizontal Scaling (Scale Out)

Add more machines instead of increasing server size.

Example:

Before:

```text
Users

↓

Server 1
```

After:

```text
Users

↓

Load Balancer

↓

Server1 Server2 Server3
```

Benefits:

- Better scalability
- Better fault tolerance
- High availability
- Traffic distribution

Problems:

- Complex architecture
- Distributed system challenges
- Data consistency issues

Examples:

- Kubernetes Pods
- Microservices scaling
- Database sharding

---

## Vertical vs Horizontal

| Feature | Vertical Scaling | Horizontal Scaling |
|----------|------------------|--------------------|
| Approach | Bigger Machine | More Machines |
| Cost | Expensive Hardware | Better Long Term |
| Availability | Lower | Higher |
| Single Point Failure | Yes | Reduced |
| Complexity | Lower | Higher |
| Scalability Limit | Hardware Limit | Better Scaling |
| Downtime | Possible | Lower |

Interview Tip:

Vertical → Bigger server

Horizontal → More servers

---

## Real World Example

Small Startup:

```text
1000 Users

↓

Vertical Scaling
```

Large Company:

```text
10 Million Users

↓

Horizontal Scaling
```

Examples:

Netflix:

```text
Horizontal Scaling
```

Instagram:

```text
Horizontal Scaling
```

---

## When To Use?

Use Vertical Scaling:

- Small systems
- Initial growth stage
- Lower traffic

Use Horizontal Scaling:

- Large scale systems
- High traffic
- Global applications

---

## Interview Questions

### Q1. Horizontal vs Vertical Scaling?

Vertical:

Increase server resources.

Horizontal:

Increase server count.

---

### Q2. Which scaling provides better availability?

Horizontal Scaling.

---

### Q3. Biggest limitation of Vertical Scaling?

Hardware limitation.

---

## Quick Revision

- Vertical → Bigger server
- Horizontal → More servers
- Vertical → Simpler
- Horizontal → Better scalability
- Vertical → Hardware limit
- Horizontal → Distributed system
- Startup → Vertical initially
- Large scale → Horizontal