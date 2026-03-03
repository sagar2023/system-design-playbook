# 📐 High Level Design (HLD)

This folder contains High-Level Design documents for various system design problems.

High-Level Design focuses on defining the overall architecture of a system — including major components, interactions, scalability, and reliability — without going into low-level implementation details.

---

## 🎯 Objective

The goal of this HLD section is to:

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

### 2️⃣ Capacity Estimation
- Traffic estimation (RPS)
- Storage estimation
- Bandwidth estimation
- Read/Write ratio

### 3️⃣ System Architecture
- Component diagram
- Service interactions
- Data flow
- External dependencies

### 4️⃣ API Design (High-Level)
- Key endpoints
- Request/Response models
- Authentication & Authorization

### 5️⃣ Database Design
- High-level schema
- Indexing strategy
- Sharding approach
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
