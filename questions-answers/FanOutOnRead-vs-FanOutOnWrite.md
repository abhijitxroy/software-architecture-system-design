

# Fan Out On Read vs Fan Out On Write

## Why This Comparison Matters?

Fan Out strategies are common feed generation approaches used in large scale social systems.

System design interviews frequently ask this topic for:

- Twitter Design
- News Feed Design
- Social Platform Design
- Feed Generation Systems

Choosing the wrong approach can create:

- High latency
- Database bottlenecks
- Scalability problems
- Celebrity user problems

Understanding feed generation is important for:

- System Design Interviews
- Distributed Systems
- Scalability Design
- Production Architecture

---

## Fan Out On Write

Generate feed when content is created.

Flow:

```text
User Creates Post
       ↓
Push Post To Followers
       ↓
Follower Timeline Updated
```

Example:

```text
User A
 ↓
Creates Tweet
 ↓
Followers Feed Updated
```

Best For:

- Normal users
- Read heavy systems
- Faster timeline loading

Pros:

- Fast feed read
- Lower read latency
- Better user experience

Cons:

- Higher write cost
- Celebrity user problem
- More storage needed

---

## Fan Out On Read

Generate feed when user opens timeline.

Flow:

```text
Open Timeline
      ↓
Fetch Posts
      ↓
Build Feed
      ↓
Return Timeline
```

Example:

```text
User Opens Feed
      ↓
System Generates Timeline
```

Best For:

- Celebrity users
- Large follower systems
- Lower write pressure

Pros:

- Lower write cost
- Less storage usage
- Better celebrity handling

Cons:

- Higher read latency
- Slower feed generation

---

## Celebrity Problem

Example:

```text
Celebrity User
100 Million Followers
```

Fan Out On Write:

```text
Need 100 Million Feed Updates
```

Expensive operation.

Production systems commonly avoid this.

---

## Hybrid Model

Large production systems commonly combine both.

Example:

```text
Normal User
→ Fan Out On Write

Celebrity User
→ Fan Out On Read
```

Examples:

- Twitter/X Feed
- Social Platforms

---

## Key Differences

| Feature | Fan Out On Read | Fan Out On Write |
|----------|-----------------|------------------|
| Feed Generation | Read Time | Write Time |
| Read Latency | Higher | Lower |
| Write Cost | Lower | Higher |
| Storage Usage | Lower | Higher |
| Celebrity Support | Better | Harder |
| User Experience | Moderate | Better |

---

## Interview Shortcut

Remember:

```text
Fan Out On Read
→ Save Write Cost

Fan Out On Write
→ Faster Feed Read
```

---

## Interview Questions

1. Fan Out On Read vs Fan Out On Write?

2. Celebrity user problem?

3. Why social systems use hybrid approach?

4. Why Fan Out On Write improves latency?

5. Feed generation scaling approach?

6. Twitter feed generation design?

---

## Quick Revision

- Fan Out On Write improves read performance
- Fan Out On Read reduces write cost
- Celebrity users create scaling problems
- Hybrid approach is common in production
- Feed generation is common interview topic
- Twitter commonly uses hybrid feed generation