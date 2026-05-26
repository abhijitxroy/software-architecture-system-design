# Consensus Protocols System Design

## Problem Statement

Consensus protocols help distributed systems agree on a single source of truth even during failures.

Used in:

- Kafka
- Kubernetes
- ZooKeeper
- etcd
- Distributed databases

System should support:

- Leader Election
- Log Replication
- Failure Recovery
- Majority Agreement
- Split Brain Prevention
- High Availability

---

## Why Consensus Needed

Distributed systems face problems:

- Node failure
- Network partition
- Duplicate request
- Inconsistent state

Goal:

```text
Multiple nodes
↓
Agree on same data
↓
Maintain consistency
```

---

## Core Concepts

### Leader Election

One node becomes:

```text
Leader
```

Leader responsibilities:

- Accept write request
- Replicate logs
- Coordinate cluster

Followers:

- Receive updates
- Participate in voting

---

### Quorum

Definition:

Minimum nodes required to agree.

Example:

```text
5 Nodes Cluster

Quorum = 3
```

Formula:

```text
(N / 2) + 1
```

Benefits:

- Prevent split brain
- Strong consistency

---

### Split Brain

Problem:

Two leaders exist simultaneously.

Example:

```text
Partition A
Leader A

Partition B
Leader B
```

Issue:

```text
Data inconsistency
```

Solution:

```text
Majority quorum
Leader lease
```

---

## Raft Protocol

Raft focuses on:

- Simplicity
- Understandability
- Strong consistency

States:

```text
Follower
Candidate
Leader
```

Election Flow:

```text
Follower Timeout
↓
Become Candidate
↓
Request Vote
↓
Majority Vote
↓
Become Leader
```

Leader Responsibilities:

- Accept write
- Replicate log
- Heartbeat follower

Log Replication:

```text
Client Write
↓
Leader
↓
Follower Replication
↓
Majority Ack
↓
Commit Entry
```

Advantages:

- Easier than Paxos
- Production friendly

Used In:

```text
etcd
Consul
Kubernetes
```

---

## Paxos Protocol

Goal:

Agree on value despite failures.

Roles:

### Proposer

Suggest value.

### Acceptor

Vote proposal.

### Learner

Learn final value.

Flow:

```text
Propose
↓
Accept
↓
Majority Vote
↓
Commit
```

Challenges:

- Complex implementation
- Hard interview explanation

Benefits:

- Strong consistency
- Fault tolerance

---

## Raft vs Paxos

| Feature | Raft | Paxos |
|----------|------|-------|
| Complexity | Lower | Higher |
| Learning Curve | Easier | Harder |
| Leader Model | Strong Leader | Distributed Proposal |
| Interview Friendly | Better | Harder |

---

## Log Replication

Purpose:

Keep nodes synchronized.

Flow:

```text
Leader
↓
Append Log
↓
Replicate
↓
Follower Ack
↓
Commit
```

Guarantee:

```text
All nodes converge eventually
```

---

## Failure Recovery

Scenario:

```text
Leader Crash
↓
Heartbeat Missing
↓
Election Triggered
↓
New Leader Selected
```

Recovery Goal:

- No data corruption
- Cluster availability

---

## High Level Architecture

```text
Client
 |
Leader Node
 |
+----------------+
| Follower Node |
| Follower Node |
| Follower Node |
+----------------+
 |
Replicated Logs
```

---

## Reliability Strategy

Techniques:

- Majority quorum
- Replication
- Heartbeat detection
- Leader election

---

## Bottlenecks

| Problem | Solution |
|----------|-----------|
| Leader overload | Scale cluster |
| Network partition | Quorum |
| Split brain | Majority voting |
| Slow replication | Log optimization |

---

## Interview Questions

1. Why quorum needed?
2. Raft vs Paxos?
3. How leader election works?
4. How split brain prevented?
5. Why heartbeat needed?
6. Why majority voting required?

---

## Quick Revision

- Consensus maintains consistency
- Quorum prevents split brain
- Raft easier than Paxos
- Leader handles writes
- Followers replicate logs
- Heartbeat detects failures