# Notification System - Low Level Design (LLD)

## Problem Statement

Design a Notification System for a large scale application.

System should support:

- Email Notification
- SMS Notification
- Push Notification
- In-App Notification

Examples:

- Amazon Order Updates
- Flipkart Delivery Notifications
- OTP Messages
- Instagram Push Notification

---

## Functional Requirements

System should support:

1. Send Email Notification

2. Send SMS Notification

3. Send Push Notification

4. Retry Failed Notification

5. Notification History

6. User Notification Preference

---

## Non Functional Requirements

- High Availability
- Scalability
- Retry Mechanism
- Low Latency
- Fault Tolerance

---

## Core Entities

## User

```java
public class User {

    private String userId;

    private String name;

    private String email;

    private String phone;

}
```

---

## Notification

```java
public class Notification {

    private String notificationId;

    private String message;

    private NotificationType type;

    private NotificationStatus status;

}
```

---

## Notification Type

```java
public enum NotificationType {

    EMAIL,

    SMS,

    PUSH

}
```

---

## Notification Service

```java
public interface NotificationService {

    void send(
        Notification notification
    );

}
```

---

## Email Service

```java
public class EmailService
implements NotificationService {

}
```

---

## SMS Service

```java
public class SMSService
implements NotificationService {

}
```

---

## Push Service

```java
public class PushService
implements NotificationService {

}
```

---

## Class Diagram

```text
NotificationService
      |
-----------------------
|         |           |
Email   SMS        Push
Service Service    Service
```

---

## Send Notification Flow

```text
Order Created

↓

Notification Service

↓

Message Queue

↓

Notification Worker

↓

Email / SMS / Push
```

---

## Why Queue Needed?

Without Queue:

```text
Order Created

↓

Email Service Slow

↓

Application Slow
```

With Queue:

```text
Order Created

↓

Kafka / RabbitMQ

↓

Worker

↓

Notification
```

Benefits:

- Async processing
- Better scalability
- Better reliability

---

## Retry Mechanism

Example:

```text
Email Failed
```

Retry:

```text
Attempt 1

↓

Attempt 2

↓

Attempt 3
```

Still failed:

```text
Dead Letter Queue
```

---

## User Preference Example

User Settings:

```text
Email = Enabled

SMS = Disabled

Push = Enabled
```

Notification service checks preference before sending.

---

## Design Patterns Used

### Factory Pattern

Create notification provider.

Example:

```text
EMAIL

↓

Email Service
```

---

### Strategy Pattern

Different notification delivery strategies.

Example:

```text
SMS Strategy

Email Strategy

Push Strategy
```

---

## Database Table

Notification Table:

| NotificationId | UserId | Type | Status |
|---------------|--------|------|--------|
| N1001 | U101 | EMAIL | SENT |

---

## Scaling Problem

Scenario:

```text
Big Billion Sale
```

Traffic:

```text
10 Million Notifications
```

Solution:

- Kafka
- Worker Scaling
- Retry Queue

---

## Interview Questions

### Q1. Why Queue needed?

Prevent slow notification processing.

---

### Q2. How retry mechanism works?

Retry failed notification multiple times.

---

### Q3. How system scales?

Queue + Worker scaling.

---

### Q4. Why Dead Letter Queue needed?

Store failed notifications.

---

## Production Examples

Amazon:

```text
Order Confirmed

↓

Queue

↓

Email Notification
```

Instagram:

```text
Like Received

↓

Push Notification
```

---

## Quick Revision

- Queue improves scalability
- Retry improves reliability
- DLQ stores failed messages
- Factory creates notification provider
- Strategy changes delivery method
- Kafka handles async processing