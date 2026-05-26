

# Artifact Repository

## What is Artifact Repository?

Artifact Repository is a centralized platform used to store, manage, version and distribute build artifacts generated during software development.

Artifacts are deployable outputs created by build systems and CI/CD pipelines.

Examples:

- JAR files
- Docker images
- NPM packages
- Python packages
- Binary files
- Helm charts
- Build dependencies

Artifact repositories improve software delivery consistency and dependency management.

---

## Why Artifact Repository?

Problems without artifact repository:

- Dependency duplication
- Difficult version tracking
- Manual package distribution
- Poor build reproducibility
- Security risks from uncontrolled dependencies

Artifact repository improves:

- Dependency management
- Build consistency
- Security control
- Faster CI/CD
- Version management

---

## High Level Architecture

```text
Developer
    |
    v
CI/CD Pipeline
    |
    v
+----------------------+
| Artifact Repository  |
| Nexus / Artifactory  |
+----------+-----------+
           |
   +-------+-------+
   |               |
   v               v
Deployment      Build System
Platform        Dependency Pull
```

---

## Core Components

### Artifact Storage

Stores generated artifacts.

Examples:

- Maven packages
- Docker images
- Binary releases
- Helm packages

Requirements:

- Durability
- Availability
- Version tracking

---

### Metadata Management

Tracks artifact information.

Metadata examples:

- Version
- Build timestamp
- Checksum
- Repository path
- Owner

Example:

```text
application-service
Version: 2.1.0
Build: 450
Checksum: SHA256
```

---

### Repository Types

#### Local Repository

Stores internally published artifacts.

Example:

```text
company-internal-release
```

---

#### Remote Repository

Caches external packages.

Examples:

- Maven Central
- Docker Hub
- PyPI

Benefits:

- Faster downloads
- Reduced external dependency failures

---

#### Virtual Repository

Combines multiple repositories under one endpoint.

Example:

```text
virtual-repository
 ├── internal-release
 ├── docker-cache
 └── maven-central
```

---

## Artifact Lifecycle

Flow:

```text
Code Commit
   ↓
CI Build
   ↓
Artifact Generation
   ↓
Artifact Repository
   ↓
Deployment Pipeline
   ↓
Production
```

---

## Popular Artifact Repository Platforms

### JFrog Artifactory

Features:

- Universal package support
- Security scanning
- Repository federation

---

### Sonatype Nexus

Features:

- Dependency management
- Repository proxy
- Package lifecycle management

---

### Harbor

Features:

- Container registry
- Vulnerability scanning
- Image signing

---

## Security Concepts

Security capabilities:

- Access control
- RBAC
- Checksum validation
- Vulnerability scanning
- Artifact signing

Example:

```text
Developer → Upload Permission
Deployment → Read Permission
```

---

## Production Challenges

Common issues:

- Storage growth
- Dependency sprawl
- Artifact cleanup
- Security vulnerabilities
- Repository replication complexity

Solutions:

- Retention policies
- Cleanup automation
- Vulnerability scanning
- Multi-region replication

---

## Production Examples

Examples:

- Enterprise CI/CD platform
- Kubernetes deployment platform
- Internal package management system
- Microservices platform
- Developer platform engineering

---

## Interview Questions

1. What is Artifact Repository?

2. Why use artifact repositories?

3. Local vs remote vs virtual repository?

4. Artifact repository vs source repository?

5. Why checksum validation matters?

6. Nexus vs Artifactory?

---

## Quick Revision

- Artifact repository stores deployable software packages
- CI/CD pipelines publish build outputs
- Versioning improves reproducibility
- Remote repositories cache dependencies
- Virtual repositories simplify package access
- Security scanning improves software supply chain security
- Artifact repositories improve delivery reliability