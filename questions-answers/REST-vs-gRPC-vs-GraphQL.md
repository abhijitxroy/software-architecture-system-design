

# REST vs gRPC vs GraphQL

## Why This Comparison Matters?

REST, gRPC and GraphQL are common API communication approaches.

System design interviews frequently ask when to choose one over another.

Choosing the wrong API approach can create:

- Higher latency
- Overfetching data
- Underfetching data
- Scalability issues
- Development complexity

Understanding API design is important for:

- System Design Interviews
- Backend Development
- Microservices Design
- Production Architecture

---

## REST

REST uses HTTP endpoints.

Flow:

```text
Client
  ↓
GET /users/123
  ↓
Server
  ↓
JSON Response
```

Example:

```text
GET /users
GET /orders
POST /payments
```

Best For:

- Public APIs
- Web Applications
- CRUD Systems

Pros:

- Simple implementation
- Easy debugging
- Wide ecosystem support
- Human readable

Cons:

- Overfetching possible
- Underfetching possible
- Multiple API calls needed

---

## gRPC

gRPC uses Protocol Buffers and HTTP/2.

Flow:

```text
Service A
   ↓
gRPC Call
   ↓
Service B
```

Example:

```text
User Service
↓
gRPC
↓
Payment Service
```

Best For:

- Microservices
- Internal Services
- High Performance Systems

Pros:

- Faster communication
- Strong contract definition
- Streaming support
- Lower payload size

Cons:

- Browser support limited
- Harder debugging
- Learning curve higher

---

## GraphQL

GraphQL allows client to request only required fields.

Flow:

```text
Client
 ↓
GraphQL Query
 ↓
Server
 ↓
Required Data Only
```

Example:

```text
User {
 name
 orders
}
```

Best For:

- Mobile Applications
- Complex UI Systems
- Multi Data Source Systems

Pros:

- Prevents overfetching
- Flexible queries
- Single endpoint

Cons:

- Caching harder
- Query complexity
- Operational complexity

---

## Key Differences

| Feature | REST | gRPC | GraphQL |
|----------|------|------|----------|
| Protocol | HTTP | HTTP/2 | HTTP |
| Data Format | JSON | Protocol Buffer | JSON |
| Performance | Moderate | Fastest | Moderate |
| Browser Support | Strong | Limited | Strong |
| Streaming | Limited | Yes | Limited |
| Flexibility | Moderate | Lower | Highest |
| Best For | Public API | Internal Services | Complex UI |

---

## Production Example

Public API:

```text
External Developer Access
```

Choose:

```text
REST
```

Microservices Platform:

```text
Low Latency
High Throughput
```

Choose:

```text
gRPC
```

Mobile Application:

```text
Need Specific Fields Only
```

Choose:

```text
GraphQL
```

---

## Interview Shortcut

Remember:

```text
REST
→ Simplicity

gRPC
→ Performance

GraphQL
→ Flexibility
```

---

## Interview Questions

1. REST vs gRPC vs GraphQL?

2. Why gRPC is faster?

3. GraphQL overfetching problem solution?

4. Why REST is common for public APIs?

5. Microservices API communication choice?

6. Mobile application API choice?

---

## Quick Revision

- REST focuses on simplicity
- gRPC focuses on performance
- GraphQL focuses on query flexibility
- gRPC commonly powers internal services
- REST commonly powers public APIs
- GraphQL prevents overfetching
- API choice depends on workload