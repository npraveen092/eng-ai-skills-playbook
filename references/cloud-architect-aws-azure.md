# Cloud Architect (AWS & Azure)

## Core responsibilities

- Design cloud-native architectures that meet stated availability, scalability, security, and cost targets — on AWS, Azure, or across both.
- Choose the right service for a given need rather than defaulting to the most familiar one (e.g. not every workload needs Kubernetes).
- Own network design: VPC/VNet topology, segmentation, connectivity between environments (VPN/ExpressRoute/Direct Connect, peering).
- Design for security and compliance from the start: identity, encryption at rest/in transit, least-privilege access, audit logging.
- Design disaster recovery and business continuity: RTO/RPO targets translated into concrete multi-AZ/multi-region strategies.
- Own or heavily influence cost: right-sizing, reserved/savings plans vs on-demand, autoscaling policies, storage tiering.
- Produce infrastructure as code (Terraform, Bicep, ARM, CloudFormation) rather than manually configured environments.

## Key competencies — service equivalents across AWS and Azure

| Need | AWS | Azure |
|---|---|---|
| Virtual machines | EC2 | Virtual Machines |
| Container orchestration | ECS / EKS | Container Apps / AKS |
| Serverless functions | Lambda | Azure Functions |
| Relational database | RDS / Aurora | Azure SQL Database / Database for PostgreSQL |
| NoSQL database | DynamoDB | Cosmos DB |
| Object storage | S3 | Blob Storage |
| Networking | VPC | Virtual Network (VNet) |
| Identity | IAM | Entra ID (Azure AD) |
| Messaging/eventing | SQS / SNS / EventBridge | Service Bus / Event Grid / Event Hub |
| Streaming | Kinesis | Event Hub |
| CDN | CloudFront | Azure CDN / Front Door |
| Secrets management | Secrets Manager | Key Vault |
| IaC | CloudFormation / CDK | Bicep / ARM templates |
| Monitoring | CloudWatch | Azure Monitor / Application Insights |

## Key competencies — frameworks and cross-cutting concerns

- **Well-Architected thinking**: both AWS Well-Architected and Azure Well-Architected Frameworks converge on the same pillars — reliability, security, cost optimization, operational excellence, performance efficiency (Azure adds sustainability). Use these as a structured checklist for any design.
- **High availability patterns**: multi-AZ for regional resilience, multi-region for DR, active-active vs active-passive trade-offs, health checks and automated failover.
- **Networking**: hub-and-spoke topology, private endpoints/PrivateLink to avoid public exposure of managed services, hybrid connectivity to on-prem.
- **Cost optimization**: right-sizing based on actual utilization, reserved instances/savings plans for steady-state load, spot/low-priority VMs for interruptible workloads, storage lifecycle policies.
- **Migration strategy**: the "6 Rs" (rehost, replatform, refactor, repurchase, retire, retain) as a framing for any migration conversation.
- **Multi-cloud/hybrid reality check**: multi-cloud adds real operational cost (skills, tooling, networking) — it should be a deliberate trade-off (e.g. avoiding vendor lock-in for a specific critical component, or an existing organizational split) rather than a default goal.

## Checklist for reviewing a cloud architecture

- [ ] Are RTO/RPO targets stated, and does the DR design (multi-AZ, multi-region, backup frequency) actually meet them?
- [ ] Is there a clear blast-radius boundary — does a failure in one component/region take down everything?
- [ ] Is least-privilege access enforced (scoped IAM roles/Azure RBAC, not broad admin access)?
- [ ] Are secrets kept out of code/config and pulled from Key Vault/Secrets Manager at runtime?
- [ ] Is autoscaling tied to a meaningful metric (not just CPU, if the actual bottleneck is queue depth or memory)?
- [ ] Is the design portable enough to avoid unnecessary lock-in, or is lock-in an accepted, justified trade-off?
- [ ] Is cost estimated and does it account for data egress, which is often the hidden cost in cross-region/cross-cloud designs?

## Common interview topics at this level

- Designing a highly available, cost-efficient architecture for a given scenario (e.g. an e-commerce checkout system) on AWS, Azure, or both.
- Explaining trade-offs between serverless and container-based compute for a given workload.
- Disaster recovery scenario: given an RTO/RPO, propose a concrete architecture.
- Security scenario: how to expose an internal API to a partner securely.
- Cost optimization scenario: a workload's cloud bill is too high — where do you look first?

## Expected deliverable shape

An architecture diagram (logical, showing services and data flow — not just a service logo collage) plus a short narrative covering: availability strategy, security posture, cost drivers, and the top 2-3 trade-offs made and why. Feedback given "as" this role should name the specific service or pattern that better fits the stated requirement, and say what's being traded off (cost, complexity, lock-in) by choosing it.
