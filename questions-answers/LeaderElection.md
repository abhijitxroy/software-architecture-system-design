

# Leader Election

## Why Leader Election Matters?

Distributed systems commonly run multiple servers.

Without coordination:

```text
Multiple Nodes
↓
Conflicting Updates
↓
Data Problems
↓
System Instability
```

Leader election helps distributed systems choose one node to coordinate operations.

Understanding leader election is important for:

- System Design Interviews
- Distributed Systems
- Database Systems
- Production Systems

---

## What Is Leader Election?

Leader election is the process of selecting one node as leader.

Example:

```text
Node A
Node B
Node C

↓

Leader = Node B
```

Leader responsibilities:

- Coordinate writes
- Manage metadata
- Handle ownership
- Coordinate replicas

Followers:

```text
Receive Updates
Follow Leader
```

---

## Why Systems Need Leader Election?

Problems without leader election:

```text
Multiple Leaders
↓
Split Brain
↓
Inconsistent Data
```

Goal:

```text
Single Coordination Point
```

---

## Leader Failure Scenario

Example:

```text
Leader Node
↓
Crash

Followers Detect Failure
↓
Election Process
↓
New Leader Selected
```

System continues operating.

---

## Election Algorithms

### Bully Algorithm

Higher priority node becomes leader.

Example:

```text
Node 1
Node 2
Node 5

Leader → Node 5
```

Pros:

- Simple

Cons:

- Higher message overhead

---

### Raft

Distributed consensus algorithm.

States:

```text
Leader
Follower
Candidate
```

Flow:

```text
Leader Failure
↓
Candidate Requests Vote
↓
Majority Vote
↓
Leader Selected
```

Best For:

- Distributed databases
- Consensus systems

---

## Production Examples

Database Cluster:

```text
Primary Node
↓
Leader
```

Distributed Scheduler:

```text
One Active Scheduler
```

Examples:

- Kubernetes Control Plane
- Distributed Databases
- Scheduler Systems

---

## Production Tradeoff

Benefits:

- Better coordination
- Consistency
- Reduced conflicts

Problems:

- Election overhead
- Recovery delay

---

## Interview Shortcut

Remember:

```text
Leader Election
→ Coordination

Leader Failure
→ Re Election
```

---

## Interview Questions

1. Why leader election matters?

2. Split brain problem?

3. Leader election after failure?

4. Raft states?

5. Why distributed systems need leader election?

6. Bully vs Raft?

---

## Quick Revision

- Leader election selects coordinator node
- Prevents conflicting updates
- Helps distributed coordination
- Failure triggers re election
- Raft commonly used in distributed systems
- Leader election is common interview topic