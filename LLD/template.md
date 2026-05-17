# LLD: <System Name>

Example: Parking Lot / Library Management / Ride Sharing / Hotel Booking

---

## 1. Requirements

### Functional Requirements
- 
- 
- 

### Non-Functional Requirements
- 
- 
- 

### Assumptions & Constraints
- 

### Out of Scope
- 

---

## 2. Core Entities

List the main entities (nouns) in the system.

| Entity | Description |
|--------|-------------|
| | |
| | |

---

## 3. Entity Relationships

Describe cardinalities between entities.

```
EntityA (1) ──── (N) EntityB
EntityB (M) ──── (N) EntityC
```

---

## 4. Class Diagram

```
┌─────────────────────┐
│     ClassName       │
├─────────────────────┤
│ - field: Type       │
│ - field: Type       │
├─────────────────────┤
│ + method(): Return  │
│ + method(): Return  │
└─────────────────────┘
```

Key classes:
- **Interfaces:**
- **Abstract Classes:**
- **Concrete Classes:**
- **Enums:**

---

## 5. Design Patterns Applied

| Pattern | Where Applied | Why |
|---------|--------------|-----|
| | | |
| | | |

---

## 6. Key Class Definitions

```java
// Example — replace with actual language / pseudocode

interface PricingStrategy {
    double calculate(Duration duration, VehicleType type);
}

class HourlyPricing implements PricingStrategy {
    public double calculate(Duration duration, VehicleType type) { ... }
}
```

---

## 7. API Design

### Endpoint 1 — Description

```
POST /api/v1/<resource>
Authorization: Bearer <token>

Request:
{
  "field": "value"
}

Response 200:
{
  "id": "uuid",
  "field": "value"
}

Response 4xx:
{
  "error": "message"
}
```

### Endpoint 2 — Description

```
GET /api/v1/<resource>/{id}

Response 200:
{
  "id": "uuid"
}
```

---

## 8. Database Schema

### Table: table_name

| Column | Type | Constraints | Description |
|--------|------|-------------|-------------|
| id | UUID | PK | |
| created_at | TIMESTAMP | NOT NULL | |
| updated_at | TIMESTAMP | NOT NULL | |

### Indexes

```sql
CREATE INDEX idx_<table>_<column> ON <table>(<column>);
```

### Enums

```sql
CREATE TYPE status_enum AS ENUM ('PENDING', 'ACTIVE', 'COMPLETED', 'CANCELLED');
```

---

## 9. Concurrency Handling

**Race Condition:** _Describe the scenario_

**Solution:**

```
Option A: Optimistic Locking
  - Add version column to table
  - Check version on update, reject if stale

Option B: Pessimistic Locking (DB-level)
  SELECT ... FOR UPDATE

Option C: Distributed Lock (Redis)
  SET lock_key value NX EX 30
```

**Idempotency:**
- Idempotency key: `<describe key>`
- Stored in: `<table/cache>`
- TTL: `<duration>`

---

## 10. Caching Strategy

| What to Cache | Cache Key | TTL | Invalidation Trigger |
|--------------|-----------|-----|----------------------|
| | | | |

**Cache Pattern:** Cache-Aside / Write-Through / Write-Behind

---

## 11. Background Jobs

| Job | Trigger | Queue | Retry Policy |
|-----|---------|-------|--------------|
| | | | |

---

## 12. Error Handling & Edge Cases

| Scenario | Handling |
|----------|----------|
| | |
| | |
| Duplicate request | Idempotency key check |
| Partial failure | Compensating transaction / rollback |

---

## 13. Trade-offs

| Decision | Chosen Approach | Alternative | Why |
|----------|----------------|-------------|-----|
| | | | |
| | | | |

---

## 14. SOLID Principles Applied

| Principle | How Applied |
|-----------|-------------|
| Single Responsibility | |
| Open/Closed | |
| Liskov Substitution | |
| Interface Segregation | |
| Dependency Inversion | |

---

## 15. Interview Explanation Flow

```
Problem statement
→ Requirements clarification
→ Core entities
→ Class diagram walkthrough
→ Design patterns explained
→ API design
→ DB schema
→ Concurrency handling
→ Trade-offs
```

---

## 16. Summary

2–3 line summary of the key design decisions made and why.
