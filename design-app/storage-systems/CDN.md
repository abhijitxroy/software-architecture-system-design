# CDN (Content Delivery Network)

## What is CDN?

Content Delivery Network (CDN) is a distributed infrastructure used to deliver static and dynamic content closer to users through geographically distributed edge servers.

CDN reduces latency, improves performance and reduces load on origin servers.

CDN platforms are widely used in:

- Video streaming systems
- Social media platforms
- E commerce systems
- Gaming infrastructure
- API acceleration
- Large scale web applications

---

## Why CDN?

Problems without CDN:

- High latency
- Slow page load
- Origin server overload
- Poor global performance
- Traffic spike issues

CDN improves:

- Lower latency
- Faster content delivery
- Better scalability
- Higher availability
- Reduced origin load

---

## High Level Architecture

```text
User Request
      |
      v
+----------------+
| DNS Routing    |
+--------+-------+
         |
         v
+----------------+
| Edge Server    |
| CDN Cache      |
+--------+-------+
         |
Cache Hit? 
  |      |
 Yes     No
  |      |
  v      v
Serve   Origin Server
Content     |
             v
        Cache Response
```

---

## Core Components

### Edge Server

Distributed servers located near users.

Responsibilities:

- Content caching
- Request handling
- Traffic distribution

Benefits:

- Lower latency
- Better user experience

---

### Origin Server

Primary source of application content.

Examples:

- Web server
- Object storage
- Media storage

Responsibilities:

- Content generation
- Data persistence

---

### Cache Layer

Stores frequently requested content.

Examples:

```text
Images
CSS
JavaScript
Videos
API Responses
```

Benefits:

- Faster retrieval
- Lower backend traffic

---

### DNS Routing

Routes users to nearest CDN edge.

Routing strategies:

- Geo routing
- Latency based routing
- Weighted routing

---

## CDN Cache Flow

Example:

```text
Request Image
      ↓
Edge Cache Check
      ↓
Cache Miss
      ↓
Fetch Origin
      ↓
Store Cache
      ↓
Serve User
```

Repeated request:

```text
Request
   ↓
Cache Hit
   ↓
Serve Directly
```

---

## Cache Eviction Strategies

### TTL Expiration

Content removed after expiration.

Example:

```text
TTL = 1 Hour
```

---

### LRU

Least recently used content removed first.

Benefits:

- Better cache utilization

---

## CDN Content Types

### Static Content

Examples:

- Images
- CSS
- JavaScript
- Video assets

---

### Dynamic Content

Examples:

- API responses
- Personalized content

Optimization:

- Edge compute
- Smart caching

---

## Production Challenges

Common issues:

- Cache invalidation
- Hot content problem
- Regional failures
- Origin overload
- Cache consistency

Solutions:

- Cache purge strategy
- Multi region deployment
- Edge scaling
- Cache warming
- Monitoring

---

## Production Examples

Examples:

- Netflix streaming platform
- Global e commerce platform
- Social media platform
- Gaming infrastructure
- Enterprise API acceleration

---

## Interview Questions

1. What is CDN?

2. Cache hit vs cache miss?

3. Why CDN improves latency?

4. LRU vs TTL?

5. CDN production challenges?

6. Why edge servers improve performance?

---

## Quick Revision

- CDN reduces latency using edge servers
- Cache hit improves response time
- Origin server stores source content
- DNS routing improves content delivery
- Cache invalidation impacts consistency
- Edge servers reduce backend load
- CDN improves scalability and availability