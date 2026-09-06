# eng-role-playbook

> Role-calibrated engineering playbook — practical checklists, competencies, and interview prep for 8 dev roles, from IC to architect. Portable: works with any AI assistant or as a standalone human reference.

## What this is

Generic engineering feedback ("consider scalability," "looks good to me") isn't very useful because *good* means something different depending on who's looking and what they're accountable for. A Software Engineer reviewing a PR should catch a missing null check. A Cloud Architect looking at the same system should be asking about RTO/RPO and blast radius.

This repo is a set of role-specific reference files — one per engineering role — each describing:

- **Core responsibilities** at that level
- **Key competencies** that separate it from adjacent roles/levels
- **A review checklist** you can hold real work up against
- **Common interview topics** for that title
- **The expected shape of a deliverable** (PR, ADR, HLD doc, pipeline design, etc.)

It's written as plain Markdown with no product-specific mechanics baked in, so it works equally well as:
- A system prompt / custom instructions for an AI assistant
- A knowledge file attached to a project/GPT/assistant
- A personal checklist for self-review or interview prep
- An onboarding doc for engineers stepping into a new role

## Roles covered

| Role | File | Core focus |
|---|---|---|
| Software Engineer | `references/software-engineer.md` | Implements well-scoped work correctly and cleanly |
| Senior Software Engineer | `references/senior-software-engineer.md` | Owns features end-to-end, raises the bar on quality |
| Senior Java Architect | `references/senior-java-architect.md` | Java platform/service architecture, JVM depth |
| Cloud Architect (AWS/Azure) | `references/cloud-architect-aws-azure.md` | Cloud-native design across AWS and Azure |
| QA Automation Engineer / QA Senior Engineer | `references/qa-automation-engineer.md` | Test strategy and automation at scale |
| Software Architect (HLD) | `references/software-architect-hld.md` | High-level design for critical, cross-cutting requirements |
| Senior Frontend Engineer | `references/senior-frontend-engineer.md` | Frontend architecture, performance, accessibility |
| Senior DevOps Engineer | `references/senior-devops-engineer.md` | CI/CD, automation, observability, incident response |

`SKILL.md` is the entry point — it explains how to pick the right file(s) and the principles that apply across every role (state assumptions, trade-offs over verdicts, calibrate confidence, match the deliverable shape).

## Repo structure

```
eng-role-playbook/
├── README.md
├── SKILL.md              ← start here
└── references/
    ├── software-engineer.md
    ├── senior-software-engineer.md
    ├── senior-java-architect.md
    ├── cloud-architect-aws-azure.md
    ├── qa-automation-engineer.md
    ├── software-architect-hld.md
    ├── senior-frontend-engineer.md
    └── senior-devops-engineer.md
```

## How to use it

**With an AI assistant, generally:** paste the contents of `SKILL.md` plus the relevant role file(s) into a system prompt, project/custom instructions, or the start of a chat, then ask for the review/design/interview-prep you want. Example:

```
[paste SKILL.md + references/software-architect-hld.md]

Here's our design for a payment retry system. Review it as a Software
Architect and call out anything missing for a critical requirement.
```

**Per-platform notes:**
- **Claude** — add the files to a Project's knowledge, or paste into custom instructions.
- **ChatGPT** — attach the relevant `.md` files as knowledge to a Custom GPT, or paste into custom instructions.
- **Cursor / other AI coding tools** — drop the relevant reference file(s) into your rules/context config (e.g. `.cursor/rules/`) so reviews are calibrated automatically.
- **As a human** — just read the relevant file before a design review or before an interview for that role; the checklists are meant to be skimmable in a couple of minutes.

**Multi-role requests:** real work often spans roles (e.g. a Java service on Azure with a test plan touches four files at once). Read `SKILL.md`'s "When more than one role applies" section — the short version is: read every relevant file and answer each concern in its own section rather than blending them into generic advice.

## Contributing

To add a new role, follow the existing template so it stays consistent:

1. Core responsibilities
2. Key competencies (what separates this role from adjacent ones)
3. A review checklist (concrete, checkable items — not vague qualities)
4. Common interview topics
5. Expected deliverable shape

Add the new file under `references/`, then add a row to the table in this README and in `SKILL.md`, and update `SKILL.md`'s frontmatter `description` so the new role is discoverable by AI assistants that trigger on it.

Pull requests that tighten an existing checklist, fix a stale tool/service reference, or add a role are welcome.

## License

Not yet licensed — add a `LICENSE` file before treating this as open source. MIT is a reasonable default for a content/reference repo like this if you want others to freely reuse and adapt it; say the word and I'll add one.
