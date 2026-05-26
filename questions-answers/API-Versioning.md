

# API Versioning

## Why API Versioning Matters?

API contracts change over time.

Production systems evolve because of:

- New features
- Schema updates
- Deprecation
- Security improvements
- Client compatibility requirements

Without versioning:

```text
Old Clients Break
↓
Production Issues
↓
Poor User Experience
```

Understanding API versioning is important for:

- System Design Interviews
- Backend Development
- Microservices
- Production Systems

---

## URL Versioning

Version included in URL.

Example:

```text
/v1/users
/v2/users
```

Flow:

```text
Client
 ↓
/v1/orders
 ↓
API Server
```

Pros:

- Simple
- Easy debugging
- Easy routing
- Widely adopted

Cons:

- Multiple endpoint maintenance

Best For:

- Public APIs
- External clients

Examples:

```text
api.company.com/v1/users
```

---

## Header Versioning

Version passed in request header.

Example:

```text
Accept: application/vnd.company.v2+json
```

Flow:

```text
Client
 ↓ Header
Version Information
 ↓
API Server
```

Pros:

- Cleaner URL
- Flexible evolution

Cons:

- Harder debugging
- Less visible

Best For:

- Enterprise APIs

---

## Query Parameter Versioning

Version passed in query parameter.

Example:

```text
/users?version=v2
```

Pros:

- Easy implementation

Cons:

- Less common
- URL inconsistency

Best For:

- Internal systems

---

## Content Negotiation Versioning

Server chooses response format.

Example:

```text
Accept: application/json;version=2
```

Pros:

- Flexible
- REST friendly

Cons:

- Operational complexity

Best For:

- Advanced API platforms

---

## Key Differences

| Strategy | URL Cleanliness | Client Visibility | Complexity | Production Usage |
|-----------|-----------------|-------------------|------------|------------------|
| URL Versioning | Lower | Best | Simple | Very Common |
| Header Versioning | Better | Lower | Medium | Common |
| Query Versioning | Moderate | Better | Simple | Lower |
| Content Negotiation | Better | Lower | Higher | Advanced Systems |

---

## Production Example

Public API:

```text
External Developers
Backward Compatibility
```

Choose:

```text
URL Versioning
```

Enterprise Platform:

```text
Cleaner API Contract
```

Choose:

```text
Header Versioning
```

---

## Version Migration Strategy

Recommended approach:

```text
Create v2
↓
Support v1 + v2
↓
Deprecation Notice
↓
Client Migration
↓
Remove v1
```

---

## Interview Shortcut

Remember:

```text
URL
→ Simplicity

Header
→ Cleaner API

Content Negotiation
→ Flexibility
```

---

## Interview Questions

1. API Versioning strategies?

2. URL vs Header versioning?

3. Why API versioning matters?

4. Backward compatibility strategy?

5. Public API versioning choice?

6. API deprecation handling?

---

## Quick Revision

- APIs evolve over time
- Versioning prevents client breakage
- URL versioning is most common
- Header versioning provides cleaner API design
- Backward compatibility matters
- API lifecycle management is common interview topic