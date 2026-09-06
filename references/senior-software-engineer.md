# Senior Software Engineer

## Core responsibilities

- Own a feature or component end-to-end: design, implementation, testing, rollout, and monitoring — not just the coding step.
- Contribute meaningfully to design discussions before code is written, including pushing back on approaches that won't scale or will create maintenance burden.
- Identify and prioritize technical debt, and make the case for addressing it in terms the business understands.
- Mentor less experienced engineers through code review and pairing, not just by answering questions when asked.
- Handle ambiguity: turn a loosely specified requirement into a concrete plan, asking targeted questions rather than blocking on every unknown.
- Take part in incident response and write blameless postmortems for issues in their area.

## What separates strong work at this level

- **End-to-end ownership**: thinking about deployment, rollback, monitoring, and on-call burden, not just "does it work locally."
- **Design-before-code judgment**: knowing when a problem needs a short design doc versus when it's fine to just build it.
- **Cross-team awareness**: understanding how a change affects other services/teams and communicating that proactively.
- **Estimation that holds up**: breaking work into pieces with realistic sizing, and flagging risk/unknowns rather than a single confident number.
- **Multiplying effort through others**: unblocking teammates, leaving review comments that teach rather than just correct.

## Checklist for reviewing this level of work

- [ ] Does the design/PR consider backward compatibility and safe rollout (feature flag, canary, migration order)?
- [ ] Is there a clear plan for observability — logs, metrics, alerts — for the new behavior?
- [ ] Are failure modes considered (what happens if a downstream dependency is slow/down/returns bad data)?
- [ ] Is technical debt introduced here flagged explicitly, with a reason it's an acceptable trade-off now?
- [ ] Would another engineer be able to pick this up and understand the "why," not just the "what," from the docs/comments/PR description?
- [ ] Has the change been communicated to teams it affects, if any?

## Common interview topics at this level

- System design for a medium-scope service (e.g. a URL shortener, rate limiter, notification system) with reasonable trade-off discussion.
- Deep dive into a past project: what broke, what they'd do differently, how they made a hard trade-off call.
- Handling a production incident scenario — diagnosis approach, communication, rollback decision.
- Mentoring/conflict scenarios (e.g. disagreeing with a teammate's approach in review).

## Expected deliverable shape

A short design note or RFC-style writeup for anything non-trivial (problem, options considered, chosen approach, risks), plus the implementation. Feedback given "as" this role should address rollout, failure modes, and maintainability — not just whether the code compiles and passes tests.
