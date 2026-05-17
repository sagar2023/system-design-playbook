# 🔩 Low Level Design (LLD)

This folder contains Low-Level Design documents for various system design problems.

Low-Level Design focuses on the internal structure of a system — class design, API contracts, database schemas, concurrency handling, and code-level architectural decisions.

---

## 🎯 Objective

- Strengthen object-oriented design and SOLID principles
- Practice class diagram and relationship modeling
- Prepare for LLD interview rounds
- Document design patterns and when to use them
- Build reusable component-level design references

---

## 🏗️ What LLD Covers

Each design typically includes:

### 1️⃣ Requirements
- Functional Requirements
- Non-Functional Requirements
- Assumptions & Constraints
- Out of Scope

### 2️⃣ Entities & Relationships
- Core entities and their attributes
- Entity relationships (1:1, 1:N, M:N)
- Class diagram

### 3️⃣ Class Design
- Classes, interfaces, abstract classes
- Inheritance hierarchy
- Composition vs aggregation decisions
- Design patterns applied (Strategy, Factory, Observer, etc.)

### 4️⃣ API Design (Detailed)
- Endpoint definitions
- Request/Response contracts
- Status codes & error handling
- Versioning approach
- Authentication & Authorization

### 5️⃣ Database Schema
- Table definitions with column types
- Primary keys, foreign keys, indexes
- Normalization decisions
- Enum types and constraints

### 6️⃣ Concurrency & Thread Safety
- Race conditions and critical sections
- Locking strategy (optimistic vs pessimistic)
- Distributed locking (Redis, DB-level)
- Idempotency handling

### 7️⃣ Caching Strategy
- What to cache and cache key design
- TTL and eviction policy
- Cache invalidation approach
- Cache-aside vs write-through decisions

### 8️⃣ Background Jobs & Async Processing
- Job definitions and triggers
- Queue strategy
- Retry and dead-letter handling
- Scheduling logic

### 9️⃣ Error Handling & Edge Cases
- Input validation
- Failure scenarios
- Graceful degradation
- Idempotency on retries

---

## 📂 Folder Structure

Each problem has its own directory:

```
LLD/
│
├── README.md                       ← This file
├── template.md                     ← Blank LLD problem template
│
├── parking-lot/
│   └── README.md
├── library-management/
│   └── README.md
├── ride-sharing/
│   └── README.md
├── hotel-booking/
│   └── README.md
├── movie-ticket-booking/
│   └── README.md
├── atm-system/
│   └── README.md
├── elevator-system/
│   └── README.md
└── splitwise/
    └── README.md
```

---

## 🧩 Design Patterns Reference

| Pattern | Category | Use When |
|---------|----------|----------|
| Strategy | Behavioral | Interchangeable algorithms (pricing, sorting) |
| Factory / Abstract Factory | Creational | Object creation without exposing logic |
| Singleton | Creational | Single shared instance (config, connection pool) |
| Observer | Behavioral | Event notifications (order status, alerts) |
| Decorator | Structural | Extending behavior without subclassing |
| Command | Behavioral | Undo/redo, job queues |
| State | Behavioral | Object behavior changes with state (booking, order lifecycle) |
| Template Method | Behavioral | Fixed skeleton with variable steps |
| Composite | Structural | Tree structures (file system, org chart) |
| Proxy | Structural | Access control, lazy loading, caching |

---

## ✅ SOLID Principles Checklist

| Principle | Check |
|-----------|-------|
| **S** — Single Responsibility: each class has one reason to change | |
| **O** — Open/Closed: open for extension, closed for modification | |
| **L** — Liskov Substitution: subtypes replaceable for base type | |
| **I** — Interface Segregation: no class forced to depend on unused methods | |
| **D** — Dependency Inversion: depend on abstractions, not concretions | |

---

## 🎯 Common LLD Interview Problems

| Problem | Key Patterns | Core Challenge |
|---------|-------------|----------------|
| Parking Lot | Strategy, Factory | Slot allocation, pricing |
| Library Management | Observer, State | Book reservation, late fines |
| Ride Sharing (Uber) | Strategy, Observer | Driver matching, surge pricing |
| Hotel Booking | State, Strategy | Room availability, concurrency |
| Movie Ticket Booking | State, Factory | Seat locking, payment flow |
| ATM System | State, Command | Transaction flow, cash dispensing |
| Elevator System | State, Strategy | Scheduling algorithm |
| Splitwise | Strategy | Debt simplification algorithm |
| Chess Game | Command, State | Move validation, game state |
| Snake & Ladder | State | Dice, position management |

---

## 🔑 LLD Interview Framework

When solving any LLD problem, follow this order:

```
1. Clarify requirements (functional + non-functional)
2. Identify core entities
3. Define relationships & cardinalities
4. Draw class diagram
5. Detail key methods per class
6. Apply design patterns
7. Handle concurrency & edge cases
8. Design APIs
9. Design DB schema
10. Discuss trade-offs
```
