

# Model Serving System Design

## Problem Statement

Design a model serving platform that deploys ML and AI models for real time and batch inference at scale.

Used in:

- Chatbot Systems
- Recommendation Systems
- Fraud Detection
- Image Classification
- Search Ranking
- RAG Systems

System should support:

- Model Deployment
- Online Inference
- Batch Inference
- Model Versioning
- Canary Deployment
- A/B Testing
- Autoscaling
- Monitoring

---

## Functional Requirements

### Core Features

- Deploy model
- Route inference request
- Model version control
- Batch prediction
- Real time prediction
- Traffic splitting
- Rollback deployment
- Monitoring

---

## Non Functional Requirements

### Scalability

- Millions of predictions/day

### Availability

- 99.99% uptime

### Reliability

- No prediction outage

### Latency

- P95 inference latency under 100 ms

---

## Why Model Serving Needed

Without serving layer:

```text
Model Training
↓
Manual Deployment
↓
Slow Updates
↓
Operational Complexity
```

Goal:

```text
Reliable Prediction
+
Fast Deployment
+
Scalable Inference
```

---

## Core Concepts

### Online Inference

Example:

```text
User Query
↓
Model Prediction
↓
Immediate Response
```

Examples:

- Recommendation
- Fraud Detection
- Chatbot

---

### Batch Inference

Example:

```text
Nightly Data Job
↓
Model Prediction
↓
Store Result
```

Examples:

- Analytics
- Risk scoring

---

### Model Versioning

Example:

```text
v1
v2
v3
```

Benefits:

- Rollback
- Safer deployment

---

### Canary Deployment

Example:

```text
90% Traffic → Model V1
10% Traffic → Model V2
```

Goal:

Reduce deployment risk.

---

### A/B Testing

Example:

```text
Group A → Model V1
Group B → Model V2
```

Measure:

- Accuracy
- CTR
- Conversion

---

## API Design

### Predict

```http
POST /predict
```

Request:

```json
{
 "userId":"123",
 "input":"recommend movie"
}
```

Response:

```json
{
 "prediction":"Interstellar"
}
```

---

## High Level Design

```text
Client
 |
API Gateway
 |
Inference Service
 |
Model Router
 |
Model Server
 |
Redis Cache
 |
Feature Store
 |
Monitoring
```

---

## Prediction Flow

```text
User Request
↓
Feature Fetch
↓
Model Selection
↓
Inference
↓
Prediction
↓
Metrics Collection
```

---

## Scaling Strategy

### Autoscaling

Scale model instances.

### Cache

Redis:

- Hot prediction cache

### GPU Pool

Benefits:

- Faster inference

---

## Monitoring

Track:

- Latency
- Error rate
- Throughput
- GPU utilization
- Model drift

---

## Reliability

Strategies:

- Retry mechanism
- Multi region deployment
- Health check
- Rollback deployment

---

## Tradeoffs

| Choice | Benefit | Drawback |
|----------|----------|-----------|
| GPU inference | Faster prediction | Higher cost |
| Batch inference | Lower compute | Higher latency |
| Canary deployment | Lower risk | More complexity |

---

## Interview Questions

1. Batch vs online inference?
2. Why model versioning needed?
3. Why canary deployment useful?
4. Why feature store needed?
5. How model serving scales?
6. How model drift detected?

---

## Quick Revision

- Model serving enables scalable inference
- Canary deployment reduces deployment risk
- Feature store improves prediction quality
- Autoscaling handles traffic spike
- Monitoring detects model drift
- Versioning improves rollback