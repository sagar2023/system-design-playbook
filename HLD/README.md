# 📐 High Level Design (HLD)

This folder contains High-Level Design documents for various system design problems.

High-Level Design focuses on defining the overall architecture of a system — including major components, interactions, scalability, and reliability — without going into low-level implementation details.

---

## 🎯 Objective

- Strengthen distributed systems fundamentals
- Practice structured system design thinking
- Prepare for system design interviews
- Document scalable architecture patterns
- Build reusable architectural references

---

## 🏗️ What HLD Covers

Each design typically includes:

### 1️⃣ Requirements
- Functional Requirements
- Non-Functional Requirements
- Assumptions & Constraints
- Out of Scope

### 2️⃣ Capacity Estimation
- Traffic estimation (RPS, DAU/MAU)
- Storage estimation
- Bandwidth estimation
- Read/Write ratio

### 3️⃣ System Architecture
- Component diagram
- Service interactions
- Data flow (end-to-end)
- External dependencies

### 4️⃣ API Design (High-Level)
- Key endpoints
- Request/Response models
- Authentication & Authorization

### 5️⃣ Database Design
- High-level schema
- SQL vs NoSQL decision
- Indexing strategy
- Sharding & partitioning approach
- Replication strategy

### 6️⃣ Scalability Strategy
- Horizontal scaling
- Load balancing
- Auto-scaling
- CDN usage

### 7️⃣ Performance Optimization
- Caching strategy (Redis / CDN)
- Read replicas
- Asynchronous processing
- Queue-based architecture

### 8️⃣ Reliability & Fault Tolerance
- Retry mechanisms
- Circuit breakers
- Graceful degradation
- Backup & disaster recovery

### 9️⃣ Trade-offs
- CAP theorem decisions
- Consistency vs Availability
- SQL vs NoSQL decisions
- Cost vs Performance trade-offs

---

## 📂 Folder Structure

Each problem has its own directory:

```
HLD/
│
├── README.md                       ← This file
├── template.md                     ← Blank HLD problem template
│
├── url-shortener/
│   └── README.md
├── notification-system/
│   └── README.md
├── payment-system/
│   └── README.md
├── rate-limiting-service/
│   └── README.md
├── distributed-logging/
│   └── README.md
├── inventory-management/
│   └── README.md
├── search-autocomplete/
│   └── README.md
├── newsfeed-system/
│   └── README.md
└── ride-sharing/
    └── README.md
```

---

## 🧩 Architecture Patterns Reference

| Pattern | Use When |
|---------|----------|
| Load Balancer | Distribute traffic across multiple instances |
| API Gateway | Single entry point, routing, auth, rate limiting |
| Message Queue (Kafka / RabbitMQ) | Async processing, decoupling producers & consumers |
| Cache Aside (Redis) | Reduce DB load for read-heavy workloads |
| Write-Through Cache | Ensure cache & DB consistency on writes |
| Read Replicas | Scale read traffic independently from writes |
| Database Sharding | Horizontally partition data across DB nodes |
| CDN | Serve static assets closer to users |
| Circuit Breaker | Prevent cascading failures between services |
| Saga Pattern | Manage distributed transactions across services |
| Event Sourcing | Audit log, replay-able state changes |
| CQRS | Separate read and write models for scale |

---

## ⚡ Capacity Estimation Cheat Sheet

| Metric | Rule of Thumb |
|--------|--------------|
| 1 million requests/day | ~12 RPS |
| 10 million requests/day | ~115 RPS |
| 100 million requests/day | ~1,200 RPS |
| 1 KB per record × 1B records | ~1 TB storage |
| 1 MB per record × 1M records | ~1 TB storage |
| Read-heavy system | Read:Write = 100:1 |
| Write-heavy system | Read:Write = 1:10 |

---

## 🎯 Common HLD Interview Problems

| Problem | Core Challenge | Key Components |
|---------|---------------|----------------|
| URL Shortener | Unique ID generation, redirects | Hashing, Redis, CDN |
| Notification System | Fan-out at scale, delivery guarantees | Kafka, push/pull, templates |
| Payment System | Consistency, idempotency, fraud | DB transactions, Saga, audit log |
| Rate Limiting Service | Per-user throttling at scale | Redis sliding window / token bucket |
| Distributed Logging | Ingestion at scale, querying | Kafka, Elasticsearch, S3 |
| Search Autocomplete | Low-latency prefix search | Trie, Redis, CDN |
| Newsfeed / Timeline | Fan-out on write vs read | Kafka, Redis, hybrid approach |
| Ride Sharing | Real-time matching, geo queries | WebSockets, geospatial index |
| Inventory Management | Stock consistency, oversell prevention | Distributed locks, events |
| Chat System | Real-time messaging, presence | WebSockets, message ordering |

---

## 🔑 HLD Interview Framework

When solving any HLD problem, follow this order:

```
1.  Clarify requirements (functional + non-functional)
2.  Define scope — what's in, what's out
3.  Capacity estimation — DAU, RPS, storage, bandwidth
4.  High-level architecture diagram
5.  Deep dive — critical components
6.  API design (key endpoints)
7.  Database design — schema, SQL vs NoSQL
8.  Scalability — sharding, replication, load balancing
9.  Caching — what, where, eviction
10. Reliability — retries, circuit breakers, failure handling
11. Trade-offs — explain decisions made
```
