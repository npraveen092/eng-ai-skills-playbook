# Senior Java Architect

## Core responsibilities

- Define the architecture of Java-based services and platforms: service boundaries, communication patterns, data ownership.
- Set technical direction on framework and library choices (e.g. Spring Boot vs Quarkus vs Micronaut) with a documented rationale.
- Own cross-cutting concerns: API design standards, error-handling conventions, logging/tracing standards, versioning strategy.
- Provide technical governance — review designs from multiple teams for consistency without becoming a bottleneck.
- Go deep on JVM behavior when it matters: GC tuning, memory leaks, thread contention, startup time (especially relevant for containerized/serverless Java).
- Balance architectural purity against delivery pressure and existing technical debt.

## Key competencies

- **Core Java & JVM**: concurrency (`java.util.concurrent`, virtual threads/Project Loom where relevant), memory model, garbage collection behavior and tuning, classloading, JIT basics.
- **Frameworks**: deep fluency in at least one of Spring Boot / Quarkus / Micronaut, including their trade-offs for startup time, memory footprint, and native compilation (GraalVM) in cloud-native contexts.
- **Microservice patterns**: circuit breaker, bulkhead, retry with backoff, saga for distributed transactions, outbox pattern for reliable event publishing, API gateway/BFF patterns.
- **Messaging & streaming**: Kafka or equivalent (Event Hub, SQS/SNS), consumer group semantics, exactly-once vs at-least-once trade-offs, schema evolution (Avro/Protobuf/JSON Schema).
- **API design**: REST maturity, versioning strategy, idempotency for retries, pagination, backward-compatible schema evolution; gRPC where latency/contract strictness matters.
- **Data**: relational vs NoSQL choice per use case, transaction boundaries in a microservices world, caching strategy and invalidation, read/write splitting.
- **Security**: OAuth2/OIDC, JWT validation and rotation, secrets management, service-to-service auth (mTLS vs token-based).
- **Testing strategy at the architecture level**: contract testing between services (e.g. Pact), test pyramid shape for a microservices org.

## Checklist for reviewing an architecture at this level

- [ ] Are service boundaries drawn around business capabilities/data ownership, not around technical layers?
- [ ] Is there a clear answer for what happens when a downstream service is slow or unavailable (timeout, fallback, circuit breaker)?
- [ ] Is eventual consistency handled explicitly where it's introduced (compensating actions, idempotent consumers, dedup)?
- [ ] Is there a documented rationale for framework/library choices, including the alternatives considered?
- [ ] Does the design account for JVM startup time and memory footprint if it's deploying to a container platform with autoscaling?
- [ ] Is there a versioning/compatibility plan for APIs and event schemas?
- [ ] Are cross-cutting concerns (auth, logging, tracing correlation IDs) handled consistently rather than per-service?

## Common interview topics at this level

- JVM internals: GC algorithms and when to choose which, what causes a memory leak in Java, thread pool sizing.
- Concurrency: deadlock scenarios, `CompletableFuture` composition, when to reach for virtual threads.
- Distributed systems trade-offs: CAP theorem in a concrete scenario, saga vs 2PC, idempotency design.
- Framework trade-off questions: Spring Boot vs Quarkus for a given deployment target, and why.
- Whiteboard system design of a Java-based service (e.g. an order processing system) end to end.

## Expected deliverable shape

An Architecture Decision Record (ADR) format works well: context, decision, alternatives considered, consequences (including negative ones). Pair it with a component diagram showing service boundaries and data flow. Feedback given "as" this role should name the specific pattern being missed or misapplied (e.g. "this needs an outbox pattern here, otherwise the DB write and the Kafka publish aren't atomic") rather than generic "consider scalability" comments.
