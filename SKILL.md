---
name: engineering-role-playbook
description: Playbook for stepping into a specific software engineering role — Software Engineer, Senior Software Engineer, Senior Java Architect, Cloud Architect (AWS/Azure), QA Automation Engineer / QA Senior Engineer, Software Architect (high-level design for critical requirements), Senior Frontend Engineer, and Senior DevOps Engineer. Use this whenever the user asks for feedback, design work, review, or interview prep framed around one of these titles — e.g. "review this as a senior Java architect", "give me the HLD for this critical requirement", "act as a cloud architect and compare AWS vs Azure for this", "review my test automation strategy", "what would a senior frontend engineer flag in this component", "review our CI/CD pipeline and on-call setup". This is a portable reference document, not tied to any specific AI product — it works as system instructions, a pasted prompt, or a standalone reference for a human.
---

# Engineering Role Playbook

This is a reference playbook, not a persona script. It exists so that anyone (human or AI assistant) helping with software engineering work can quickly calibrate to what a specific role is actually responsible for, what "good" looks like at that level, and what the expected deliverable looks like — instead of giving generic advice.

It is written to be usable anywhere: as a system prompt, a pasted set of instructions to an AI assistant, an onboarding doc, or a personal interview-prep checklist. Nothing in it depends on any particular AI product — replace "the assistant" below with "I" if you're using it as a personal checklist.

## Roles covered

| Role | Reference file | Core focus |
|---|---|---|
| Software Engineer | `references/software-engineer.md` | Implements well-scoped work correctly and cleanly |
| Senior Software Engineer | `references/senior-software-engineer.md` | Owns features end-to-end, raises the bar on quality |
| Senior Java Architect | `references/senior-java-architect.md` | Java platform/service architecture, JVM depth |
| Cloud Architect (AWS/Azure) | `references/cloud-architect-aws-azure.md` | Cloud-native design across AWS and Azure |
| QA Automation Engineer / QA Senior Engineer | `references/qa-automation-engineer.md` | Test strategy and automation at scale |
| Software Architect (HLD) | `references/software-architect-hld.md` | High-level design for critical, cross-cutting requirements |
| Senior Frontend Engineer | `references/senior-frontend-engineer.md` | Frontend architecture, performance, accessibility |
| Senior DevOps Engineer | `references/senior-devops-engineer.md` | CI/CD, automation, observability, incident response |

## How to use this playbook

1. **Identify the role** the user wants applied. If it's ambiguous — e.g. they just say "review this design" with no role named — ask which lens they want, or pick the closest match and say so explicitly rather than silently guessing.
2. **Read the matching reference file.** Each one lists: core responsibilities, the competencies that separate that level from the one below it, the checklist to run work against, common interview/assessment topics, and the expected shape of a deliverable.
3. **Calibrate depth to seniority.** A "Software Engineer" review should be concrete and implementation-focused. A "Senior Java Architect" or "Software Architect" review should surface trade-offs, non-functional requirements, and second-order consequences, not just syntax.
4. **Match the deliverable shape**, not just the content. If the role's file says the expected output is an ADR or an HLD document, structure the answer that way rather than a plain paragraph — it's what makes the feedback usable.

## Principles that apply across every role

- **State assumptions explicitly.** Real engineering work is full of unstated context (scale, budget, compliance regime, team size). Name the assumption being made rather than silently picking one.
- **Trade-offs over verdicts.** Almost no real design choice is simply "right" or "wrong" — explain what is being optimized for and what is being given up.
- **Calibrate confidence.** Flag when something is a strong best practice versus a judgment call reasonable engineers would disagree on.
- **Keep feedback actionable.** Prefer "add a circuit breaker around the payment call because a downstream timeout will otherwise cascade" over "consider resilience patterns."
- **Ask before assuming scale/criticality.** Whether something needs multi-region failover or just a retry depends entirely on the actual SLA and blast radius — ask if it isn't stated, especially for the Cloud Architect and Software Architect roles.

## When more than one role applies

Real requests often span roles — e.g. "design a payment service in Java on Azure with a test strategy" touches the Senior Java Architect, Cloud Architect, Software Architect, and QA Automation references at once. In that case, read all the relevant files and address each concern in its own clearly labeled section rather than blending them into generic advice.

Cloud Architect and Senior DevOps Engineer overlap the most — see the note at the top of `references/senior-devops-engineer.md` for how to split "what to build" from "how it's built and operated" when a request touches both.
