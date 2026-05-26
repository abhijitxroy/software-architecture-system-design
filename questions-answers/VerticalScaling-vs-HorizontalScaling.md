# Vertical Scaling vs Horizontal Scaling

## Why This Comparison Matters?

Scaling is a core system design concept.

System design interviews frequently ask scaling approaches because production systems must handle:

- User growth
- Traffic spikes
- Data growth
- Performance bottlenecks
- Availability requirements

Choosing the wrong scaling strategy can create:

- Infrastructure limitations
- Downtime risk
- Higher operational cost
- Scalability bottlenecks

Understanding scaling approaches is important for:

- System Design Interviews
- Distributed Systems
- Cloud Architecture
- Production Systems

---

## Vertical Scaling

Vertical Scaling means increasing resources of an existing machine.

Example:

```text
Before
CPU = 4 Core
RAM = 16 GB

Upgrade
↓

CPU = 32 Core
RAM = 128 GB
```

Goal:

```text
More Power
Single Machine
```

Best For:

- Small systems
- Early stage products
- Database servers

Pros:

- Easier implementation
- Lower operational complexity
- No distributed system complexity

Cons:

- Hardware limit exists
- Single point of failure
- Expensive upgrades

---

## Horizontal Scaling

Horizontal Scaling means adding more machines.

Example:

```text
Client
  ↓
Load Balancer
 ↓   ↓   ↓
S1  S2  S3
```

Goal:

```text
More Machines
More Capacity
```

Best For:

- Large scale systems
- Distributed applications
- High traffic platforms

Pros:

- Better scalability
- Better fault tolerance
- Higher availability

Cons:

- Distributed system complexity
- Load balancing needed
- Data consistency challenges

---

## Key Differences

| Feature | Vertical Scaling | Horizontal Scaling |
|----------|------------------|--------------------|
| Approach | Bigger Machine | More Machines |
| Scalability Limit | Hardware Limit | Higher Limit |
| Complexity | Lower | Higher |
| Availability | Lower | Better |
| Infrastructure | Simpler | Distributed |
| Cost Growth | Hardware Upgrade | Infrastructure Growth |
| Failure Impact | Higher | Lower |

---

## Production Example

Startup Product:

```text
10K Users
```

Choose:

```text
Vertical Scaling
```

Social Platform:

```text
100 Million Users
```

Choose:

```text
Horizontal Scaling
```

---

## Production Reality

Large systems commonly combine both.

Example:

```text
Bigger Database Machine
↓
Vertical Scaling

More Application Servers
↓
Horizontal Scaling
```

---

## Interview Shortcut

Remember:

```text
Vertical Scaling
→ Scale Up

Horizontal Scaling
→ Scale Out
```

---

## Interview Questions

1. Vertical Scaling vs Horizontal Scaling?

2. Why horizontal scaling improves availability?

3. Why vertical scaling becomes expensive?

4. Database scaling choice?

5. Startup scaling approach?

6. Why large systems prefer horizontal scaling?

---

## Quick Revision

- Vertical scaling means bigger machine
- Horizontal scaling means more machines
- Horizontal scaling improves availability
- Vertical scaling is simpler
- Distributed systems commonly scale horizontally
- Large systems combine both approaches
- Scaling strategy is common interview topic