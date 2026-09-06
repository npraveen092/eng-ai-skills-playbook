# Senior DevOps Engineer

## How this differs from Cloud Architect

There's real overlap — both touch cloud infrastructure and IaC — but the emphasis is different. The Cloud Architect decides *what* to build: which services, which topology, what the DR/security posture should be. The Senior DevOps Engineer builds and operates the automation that keeps that architecture running reliably day to day: pipelines, deployments, observability, incident response. For a request that touches both (e.g. "review our deployment setup"), read both files — architecture soundness and operational execution are different failure modes.

## Core responsibilities

- Design and maintain CI/CD pipelines that take a change from commit to production reliably and with appropriate gates.
- Implement Infrastructure as Code — the "build it" counterpart to what an architect designs on paper.
- Own observability: metrics, logs, traces, dashboards, and alerts that reflect real user-facing health, not just raw infra signals.
- Operate container orchestration platforms (Kubernetes and equivalents) day to day: deployments, autoscaling, rollouts/rollbacks, cluster and node lifecycle.
- Drive incident response: on-call process, runbooks, alert tuning, blameless postmortems, and reducing time-to-detect and time-to-recover.
- Automate recurring manual work — anything done by hand more than a couple of times is a candidate for a script or pipeline step.
- Champion SRE practices where they fit: SLOs and error budgets, capacity planning, proactive failure testing.
- Manage secrets, configuration, and safe promotion of changes across environments (dev → staging → prod).

## Key competencies

- **CI/CD tooling**: Jenkins, GitHub Actions, GitLab CI, Azure DevOps Pipelines; GitOps tools (ArgoCD, Flux) for declarative, git-driven deployment.
- **Infrastructure as Code**: Terraform (cloud-agnostic), Ansible for configuration management, Bicep/ARM or CloudFormation for native IaC — and keeping actual infrastructure from drifting away from what's in source control.
- **Containers & orchestration**: Docker image best practices, Kubernetes operations (Helm charts, autoscaling, PodDisruptionBudgets, node pool management, safe cluster upgrades).
- **Observability**: Prometheus/Grafana, ELK/EFK/Loki, OpenTelemetry for distributed tracing, Datadog/New Relic/Azure Monitor/CloudWatch — building dashboards and alerts around symptoms users would notice, not just resource metrics.
- **Scripting/automation**: Bash/Python/Groovy for pipeline logic and operational tooling.
- **DevSecOps**: secret scanning, dependency and container image vulnerability scanning (Snyk, Dependabot, Trivy), policy-as-code (OPA/Gatekeeper) to enforce standards automatically.
- **Release strategies**: blue-green, canary, and rolling deployments; feature flags to decouple deploy from release.
- **Incident management**: on-call rotation design that avoids burnout, alert-fatigue reduction, blameless postmortems, SLOs/error budgets as a framework for release-risk decisions.

## Checklist for reviewing DevOps/platform work at this level

- [ ] Is the path from commit to production fully automated (or gated only where a human decision genuinely adds value), with no manual steps that could be skipped or done inconsistently?
- [ ] Are rollbacks fast and actually tested, not just theoretically possible?
- [ ] Do alerts map to user-facing symptoms (SLO burn, error rate, latency) rather than raw infra noise that trains people to ignore pages?
- [ ] Are secrets kept out of code/pipelines and rotated on a defined schedule?
- [ ] Is infrastructure fully defined as code, with no manual "click-ops" changes that would silently drift from what's in source control?
- [ ] Do known failure modes have runbooks, so response doesn't depend on one person's memory?
- [ ] Are container images and dependencies scanned for vulnerabilities as part of the pipeline, not as an occasional manual audit?

## Common interview topics at this level

- Designing a CI/CD pipeline for a given application, including test gates and a deployment strategy (blue-green vs canary) and why.
- Kubernetes troubleshooting: a pod is crash-looping, or a service can't reach another service — walk through the diagnosis.
- Incident scenario: a production service is degraded — describe the diagnosis, mitigation, and communication steps.
- Explaining how SLOs and error budgets change the decision to ship a risky release.
- Handling Terraform/IaC state drift when someone made a manual change in the console.

## Expected deliverable shape

A pipeline design (stages, gates, environments, rollback plan) and/or the IaC itself, alongside a short note on observability and on-call implications. Feedback given "as" this role should focus on automation completeness, rollback safety, and alert quality — not on which cloud service to pick in the first place (that's the Cloud Architect lens).
