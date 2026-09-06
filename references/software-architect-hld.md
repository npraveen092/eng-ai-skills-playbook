# Software Architect (High-Level Design for Critical Requirements)

## Core responsibilities

- Translate a business or critical technical requirement into a High-Level Design (HLD) that the engineering org can implement from.
- Ensure non-functional requirements (NFRs) — scalability, availability, security, performance, disaster recovery, compliance — are addressed explicitly, not left implicit.
- Lead and document architecture decisions (ADRs) with enough context that someone reading them a year later understands *why*, not just *what*.
- Identify cross-cutting risks early: single points of failure, data consistency issues, integration risk with third parties or legacy systems.
- Align stakeholders — engineering, product, security, operations — on the design before implementation starts, surfacing trade-offs rather than hiding them.
- Own the design through delivery: review implementation against the HLD, and update the HLD when reality forces a deviation.

## When a requirement counts as "critical"

Treat a requirement as critical — and therefore deserving a full HLD pass, not a lightweight design note — if any of these are true:
- Failure would cause direct financial loss, safety impact, regulatory exposure, or significant reputational damage.
- It has a hard SLA/SLO (e.g. 99.99% availability, sub-200ms latency, defined RTO/RPO).
- It touches sensitive data (financial, health, personal/PII) or is in scope for a compliance regime (PCI-DSS, HIPAA, GDPR, SOC 2, etc.).
- It's a shared/foundational component that many other systems will depend on, so a design flaw propagates widely.
- It involves a hard-to-reverse decision (data model, core API contract, choice of managed service with lock-in).

## HLD template for a critical requirement

Use this structure as the default shape for any HLD document:

1. **Requirement summary** — the business problem in plain language, and the specific critical NFRs in numbers: target SLA/uptime, RTO (recovery time objective), RPO (recovery point objective), expected throughput/QPS, latency budget (e.g. p95/p99), data volume and growth rate.
2. **Context and scope** — a context diagram showing this system's boundaries: what's in scope, what's an external dependency, who the consumers are. State explicitly what is *out* of scope.
3. **Component breakdown** — the major building blocks and how they interact (synchronous call, async event, batch job), at a level someone unfamiliar with the system can follow.
4. **Data design** — what data is owned where, the consistency model (strong vs eventual, and where each applies), and the reasoning for the storage choice(s).
5. **Scalability approach** — how the design handles growth: horizontal vs vertical scaling, statelessness of compute, caching strategy, partitioning/sharding if relevant, and where the design's ceiling is (the point past which it needs to be rethought, stated honestly).
6. **Availability and disaster recovery** — how the stated RTO/RPO is actually met: redundancy (multi-AZ/multi-region), failover mechanism and how it's triggered (automatic vs manual), backup strategy and restore testing cadence.
7. **Security and compliance** — authN/authZ approach, encryption in transit/at rest, data residency if relevant, and how the design satisfies any named compliance regime.
8. **Trade-offs and alternatives considered** — at least one alternative approach that was seriously considered, and the concrete reason it was rejected (not just "we chose X instead").
9. **Risks and mitigations** — the top risks to this design working as intended, and what's being done about each (not just naming the risk).
10. **Rollout and migration plan** — how this gets deployed safely: phased rollout, feature flags, backward compatibility with existing consumers during transition, and a rollback plan.

## Checklist for reviewing an HLD

- [ ] Are the critical NFRs stated as numbers (SLA %, RTO/RPO, latency, throughput), not adjectives like "highly available" or "fast"?
- [ ] Does the availability/DR design map directly to the stated RTO/RPO, rather than being a generic "we use multi-AZ" statement?
- [ ] Is there a named single point of failure, and if so, is that an accepted, justified risk or an oversight?
- [ ] Is the consistency model explicit for every piece of shared/critical data, especially across service boundaries?
- [ ] Does the design account for what happens during partial failure (a dependency is degraded, not fully down)?
- [ ] Is there at least one real alternative considered and rejected with a stated reason — a design with no alternatives considered is a red flag?
- [ ] Is there a rollback plan, and is backward compatibility handled for consumers during rollout?
- [ ] Are security/compliance requirements addressed as first-class sections, not an afterthought at the end?

## Common interview topics at this level

- End-to-end HLD for a critical system (e.g. a payment processing pipeline, an inventory system that must never oversell, a real-time bidding system) with a stated SLA.
- "Design X to survive a full region outage" — forces an explicit DR conversation.
- Trade-off defense: justify a specific architectural choice against a plausible alternative an interviewer proposes.
- Handling a conflicting requirement (e.g. strong consistency requested alongside a very low latency target) — how the design resolves or explicitly accepts the tension.

## Expected deliverable shape

The 10-section HLD document above, with diagrams for the context view and component view at minimum. Feedback given "as" this role should push on whether NFRs are quantified and whether the DR/availability design actually satisfies them — vague qualitative claims ("this is scalable," "this is secure") should be treated as incomplete until backed by a specific mechanism and number.
