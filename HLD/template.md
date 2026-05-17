# HLD: <System Name>

Example: URL Shortener / Notification System / Payment System / Rate Limiter

---

## 1. Requirements

### Functional Requirements
- 
- 
- 

### Non-Functional Requirements
- High availability: 99.99% uptime
- Low latency: p99 < ___ ms
- Eventual / Strong consistency (choose one)
- Durability: no data loss

### Assumptions & Constraints
- 

### Out of Scope
- 

---

## 2. Capacity Estimation

### Traffic
| Metric | Value |
|--------|-------|
| Daily Active Users (DAU) | ___ M |
| Requests per day | ___ M |
| Requests per second (avg) | ___ RPS |
| Requests per second (peak) | ___ RPS (3x avg) |
| Read : Write ratio | ___ : 1 |

### Storage
| Metric | Value |
|--------|-------|
| Record size | ___ KB |
| Records per day | ___ M |
| Storage per day | ___ GB |
| Storage for 5 years | ___ TB |

### Bandwidth
| Metric | Value |
|--------|-------|
| Ingress (writes) | ___ MB/s |
| Egress (reads) | ___ MB/s |

---

## 3. High-Level Architecture

```
Client
  │
  ▼
[ CDN / Load Balancer ]
  │
  ▼
[ API Gateway ]  ── Auth, Rate Limit, Routing
  │
  ├──► [ Service A ]
  │         │
  │         ▼
  │    [ Database ]  ←─ [ Cache (Redis) ]
  │
  └──► [ Service B ]
            │
            ▼
       [ Message Queue (Kafka) ]
            │
            ▼
       [ Consumer Service ]
```

**Key Components:**
- **API Gateway:** 
- **Service A:** 
- **Service B:** 
- **Database:** 
- **Cache:** 
- **Queue:** 

---

## 4. Data Flow

### Write Path
```
1. Client sends request → API Gateway
2. Gateway authenticates → routes to Service
3. Service validates input
4. Service writes to DB
5. Service publishes event to Kafka
6. Consumer processes event
7. Response returned to client
```

### Read Path
```
1. Client sends request → API Gateway
2. Gateway routes to Service
3. Service checks Cache (Redis)
4. Cache HIT → return cached data
5. Cache MISS → query DB → populate cache → return data
```

---

## 5. API Design

### Endpoint 1 — Description

```
POST /api/v1/<resource>
Authorization: Bearer <token>

Request:
{
  "field": "value"
}

Response 201:
{
  "id": "uuid",
  "field": "value",
  "created_at": "ISO8601"
}

Response 400: { "error": "validation message" }
Response 429: { "error": "rate limit exceeded" }
```

### Endpoint 2 — Description

```
GET /api/v1/<resource>/{id}

Response 200:
{
  "id": "uuid",
  "field": "value"
}

Response 404: { "error": "not found" }
```

---

## 6. Database Design

### SQL vs NoSQL Decision

| Factor | SQL | NoSQL |
|--------|-----|-------|
| Schema flexibility | Fixed | Flexible |
| ACID transactions | Yes | Limited |
| Horizontal scaling | Hard | Easy |
| Query complexity | High | Low |

**Decision:** _SQL / NoSQL — because ___

### Schema (High-Level)

**Table: table_name**

| Column | Type | Notes |
|--------|------|-------|
| id | UUID / BIGINT | Primary Key |
| | | |
| created_at | TIMESTAMP | |
| updated_at | TIMESTAMP | |

### Indexing Strategy
- Index on `<column>` — for ___ query pattern
- Composite index on `(<col1>, <col2>)` — for ___

### Sharding Strategy
- Shard key: `<column>`
- Sharding method: Hash / Range / Directory-based
- Number of shards: ___

### Replication
- Primary-Replica setup
- Async replication for reads
- Sync replication for critical writes (if needed)

---

## 7. Scalability Strategy

### Load Balancing
- Algorithm: Round Robin / Least Connections / IP Hash
- Layer: L4 (TCP) / L7 (HTTP)

### Horizontal Scaling
- Stateless services — scale by adding instances
- Session state stored in Redis, not in-memory

### Auto-Scaling
- Scale up trigger: CPU > 70% for 3 min
- Scale down trigger: CPU < 30% for 10 min
- Min instances: ___   Max instances: ___

### CDN
- Cache static assets: images, JS, CSS
- Cache API responses at edge: TTL = ___
- Invalidation strategy: ___

---

## 8. Caching Strategy

| What | Cache Key | TTL | Eviction | Invalidation |
|------|-----------|-----|----------|--------------|
| | | | LRU | On write |
| | | | LFU | TTL expiry |

**Cache Pattern:** Cache-Aside / Write-Through / Write-Behind

**Cache size estimation:**
- ___ records × ___ KB = ___ GB

---

## 9. Async Processing & Queues

| Event | Producer | Queue / Topic | Consumer | Processing |
|-------|----------|--------------|----------|------------|
| | | | | |

**Message delivery guarantee:** At-least-once / At-most-once / Exactly-once

**Consumer group strategy:**
- Partition key: `<field>` (ensures ordering per entity)
- Number of partitions: ___
- Retry policy: ___ retries with exponential backoff
- Dead letter queue (DLQ): Yes / No

---

## 10. Reliability & Fault Tolerance

### Retry Strategy
- Max retries: ___
- Backoff: Exponential with jitter
- Idempotency key: `<describe>`

### Circuit Breaker
- Threshold: ___ failures in ___ seconds → open circuit
- Half-open probe: after ___ seconds
- Fallback: ___ (cached response / default value / error)

### Graceful Degradation
| Failure | Degraded Behavior |
|---------|-------------------|
| Cache down | Serve from DB directly |
| DB replica down | Fall back to primary |
| Downstream service down | Return cached / default response |

### Disaster Recovery
- RPO (Recovery Point Objective): ___
- RTO (Recovery Time Objective): ___
- Backup frequency: ___
- Multi-region: Active-Active / Active-Passive

---

## 11. Observability

### Metrics to Monitor
- Request rate (RPS)
- Error rate (4xx, 5xx)
- p50 / p95 / p99 latency
- Cache hit rate
- Queue lag (consumer offset)
- DB connection pool usage

### Alerts
| Alert | Threshold | Action |
|-------|-----------|--------|
| Error rate | > 1% for 5 min | Page on-call |
| p99 latency | > 500ms | Investigate |
| Queue lag | > 10K messages | Scale consumers |

### Logging
- Structured JSON logs
- Correlation ID on every request
- Log levels: ERROR for failures, INFO for key events

---

## 12. Security Considerations

- **Authentication:** JWT / OAuth 2.0 / API Key
- **Authorization:** RBAC / ABAC
- **Rate Limiting:** Per user / per IP — ___ req/min
- **Encryption:** TLS in transit, AES-256 at rest
- **Input Validation:** Reject at API Gateway
- **Audit Log:** All write operations logged with actor + timestamp

---

## 13. Trade-offs

| Decision | Chosen Approach | Alternative | Reason |
|----------|----------------|-------------|--------|
| DB choice | | | |
| Consistency model | | | |
| Cache strategy | | | |
| Fan-out approach | | | |

---

## 14. Bottlenecks & Mitigations

| Bottleneck | Why It Occurs | Mitigation |
|------------|--------------|------------|
| DB write throughput | Single primary node | Sharding, write batching |
| Hot keys in cache | Uneven distribution | Key hashing, local cache |
| Message queue lag | Slow consumers | Scale consumer instances |
| | | |

---

## 15. Interview Explanation Flow

```
Problem statement
→ Requirements clarification
→ Capacity estimation (numbers matter)
→ High-level architecture diagram
→ Deep dive on critical path
→ Database design + SQL vs NoSQL
→ Caching strategy
→ Scalability approach
→ Reliability & failure handling
→ Trade-offs
```

---

## 16. Summary

2–3 line summary of the key architectural decisions and why they were made.
