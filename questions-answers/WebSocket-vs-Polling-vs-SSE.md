# WebSocket vs Polling vs SSE

## Why This Comparison Matters?

WebSocket, Polling and SSE (Server Sent Events) solve real time communication problems.

System design interviews frequently ask communication approach selection because choosing the wrong model can create:

- Higher latency
- Increased server load
- Poor user experience
- Scalability bottlenecks
- Infrastructure inefficiency

Understanding communication models is important for:

- System Design Interviews
- Distributed Systems
- Backend Development
- Real Time Systems

---

## Polling

Client repeatedly asks server for updates.

Flow:

```text
Client
 ↓ Request
Server
 ↓ Response

Wait 5 Seconds

Client
 ↓ Request
Server
 ↓ Response
```

Example:

```text
Order Status Tracking
```

Best For:

- Small systems
- Simple applications
- Low frequency updates

Pros:

- Easy implementation
- Wide browser support
- Simple debugging

Cons:

- Higher server load
- Unnecessary requests
- Higher latency

---

## SSE (Server Sent Events)

Server pushes updates to client.

Connection remains open.

Flow:

```text
Client
 ↓
Server
 ↓
Update 1
Update 2
Update 3
```

Example:

```text
Stock Price Dashboard
News Feed Update
```

Best For:

- Notification systems
- Dashboard updates
- Live feeds

Pros:

- Lower overhead than polling
- Automatic reconnect
- Simpler than WebSocket

Cons:

- One way communication
- Browser limitations possible

---

## WebSocket

WebSocket creates persistent two way communication.

Flow:

```text
Client
 ↕
WebSocket Connection
 ↕
Server
```

Example:

```text
Chat Application
Gaming Platform
Trading Platform
```

Best For:

- Chat Systems
- Multiplayer Games
- Collaborative Editing
- Real Time Trading

Pros:

- Very low latency
- Two way communication
- Efficient real time updates

Cons:

- Higher operational complexity
- Connection management required

---

## Key Differences

| Feature | Polling | SSE | WebSocket |
|----------|----------|-----|------------|
| Communication | Request Response | One Way | Two Way |
| Real Time | Weak | Better | Best |
| Server Load | Higher | Lower | Lower |
| Complexity | Simple | Medium | Higher |
| Connection | Multiple Requests | Persistent | Persistent |
| Best For | Simple Updates | Dashboard | Chat |

---

## Production Example

Live Cricket Score:

```text
Server Updates Only
```

Choose:

```text
SSE
```

Chat Platform:

```text
Two Way Communication
```

Choose:

```text
WebSocket
```

Simple Status Page:

```text
Few Updates Needed
```

Choose:

```text
Polling
```

---

## Production Reality

Large systems choose communication model based on workload.

Example:

```text
Chat
↓
WebSocket

Monitoring Dashboard
↓
SSE

Simple Status System
↓
Polling
```

---

## Interview Shortcut

Remember:

```text
Polling
→ Ask Again

SSE
→ Server Push

WebSocket
→ Two Way Real Time
```

---

## Interview Questions

1. WebSocket vs Polling vs SSE?

2. Why WebSocket improves chat systems?

3. SSE vs WebSocket?

4. Polling limitation?

5. Dashboard communication choice?

6. Real time architecture choice?

---

## Quick Revision

- Polling repeatedly asks server
- SSE supports server push
- WebSocket supports two way communication
- WebSocket works best for chat systems
- SSE works well for dashboards
- Communication choice depends on workload
- Real time communication is common interview topic