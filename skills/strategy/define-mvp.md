# Skill: Define MVP

## Description
Define Minimum Viable Platform (MVP) scope with clear boundaries, prioritized capabilities, and acceptance criteria.

## Usage
```bash
/define-mvp --teams 50 --timeline 12-months --format detailed
```

## Parameters

### Required
- `--teams` (number): Number of development teams to support in MVP

### Optional
- `--timeline` (string): MVP delivery timeline (e.g., "6-months", "9-months", "12-months") (default: "12-months")
- `--current-state` (string): Brief description of current tooling (e.g., "jenkins,manual-deploys,ec2")
- `--priorities` (string): Top priorities: "speed", "security", "cost", "quality" (comma-separated, default: "speed,quality")
- `--constraints` (string): Known constraints (e.g., "budget:2M,staff:6-fte,regulatory:soc2")
- `--format` (string): Output format: "detailed", "summary", "user-stories", "acceptance-criteria" (default: "detailed")
- `--verticals` (string): Platform verticals to include (default: auto-selected based on priorities)

## Output Formats

### Summary Format
```
===========================================
MINIMUM VIABLE PLATFORM (MVP) DEFINITION
===========================================

Target Teams: 50 development teams
Timeline: 12 months (Q1 2026 - Q4 2026)
Investment: $2.5M CAPEX, $400K annual OPEX

────────────────────────────────────────
MVP SCOPE (What's IN)
────────────────────────────────────────

✓ Developer Portal
  - Service catalog (view existing services)
  - Documentation hub (searchable, versioned)
  - Getting started guides for 3 languages (Node, Python, Go)
  - Self-service account provisioning

✓ CI/CD Pipeline (GitHub Actions)
  - Standardized pipeline templates (build, test, deploy)
  - Automated PR validation
  - Push-to-deploy for non-prod environments
  - Manual approval gates for production

✓ Container Platform (EKS)
  - Managed Kubernetes cluster (2 environments: staging, prod)
  - Pre-configured namespaces with resource limits
  - Ingress controller and basic routing
  - Horizontal pod autoscaling

✓ Observability Basics
  - Centralized logging (CloudWatch)
  - APM integration (Datadog agents pre-configured)
  - Health check dashboards
  - Alert routing to Slack/PagerDuty

✓ Security Baseline
  - Secret management (Vault integration)
  - Container image scanning (Trivy)
  - RBAC for platform resources
  - Audit logging

────────────────────────────────────────
OUT OF SCOPE (Phase 2+)
────────────────────────────────────────

✗ Advanced service mesh (Istio)
✗ Multi-region deployment
✗ Custom operator development
✗ FinOps cost optimization dashboards
✗ Advanced ML platform capabilities
✗ Database-as-a-Service automation
✗ Chaos engineering tooling
✗ Full GitOps (ArgoCD) - Phase 2

────────────────────────────────────────
SUCCESS CRITERIA
────────────────────────────────────────

By Month 12:
✓ ≥50 teams onboarded and using platform
✓ ≥80% of new deployments via platform CI/CD
✓ Developer satisfaction score ≥7/10
✓ Time to first deployment ≤2 hours (baseline: 2 days)
✓ Platform uptime ≥99.5%
✓ Zero critical security vulnerabilities in platform
✓ ≥100 developers trained on platform

────────────────────────────────────────
ASSUMPTIONS
────────────────────────────────────────

• Teams are willing to adopt containerization
• GitHub Enterprise license already available
• AWS accounts and budgets provisioned
• Security team available for reviews
• Executive sponsorship secured
• 6 FTE platform team + 2 FTE product owner
```

### Detailed Format
Comprehensive document including:
- Executive Summary
- Business Context and Justification
- Detailed Capability Breakdown (IN scope)
- Explicit Exclusions (OUT of scope)
- User Personas and Use Cases
- Technical Architecture (high-level)
- Success Metrics and KPIs
- Risks and Mitigations
- Resource Requirements
- Roadmap Integration (how MVP feeds into Phase 2)

### User Stories Format
```markdown
## MVP User Stories

### Developer Portal

**Story 1: Service Discovery**
As a: New developer
I want to: Browse all available services in a searchable catalog
So that: I can understand what services exist and how to use them
Acceptance Criteria:
- [ ] Service catalog with search and filtering
- [ ] Each service has description, owner, API docs link
- [ ] Response time <500ms for search queries

**Story 2: Self-Service Onboarding**
As a: Team lead
I want to: Provision a new service environment with one click
So that: My team can start developing without waiting for ops
Acceptance Criteria:
- [ ] Web form for new service creation
- [ ] Automated GitHub repo creation
- [ ] CI/CD pipeline auto-configured
- [ ] Staging environment ready in <10 minutes

[20+ more user stories...]

### CI/CD Pipeline

**Story 3: Standardized Build**
As a: Developer
I want to: Use a standard CI/CD template for my language
So that: I don't have to learn YAML or configure pipelines
[...]

[Continues for all MVP capabilities...]
```

### Acceptance Criteria Format
```markdown
## MVP Acceptance Criteria

### Developer Portal
- [ ] Portal accessible at https://developer.company.com
- [ ] SSO authentication (SAML/OIDC)
- [ ] Service catalog with ≥100 services indexed
- [ ] Search results return in <500ms
- [ ] Mobile-responsive design
- [ ] Uptime ≥99.9%

### CI/CD Platform
- [ ] GitHub Actions templates for Node.js, Python, Go
- [ ] Automated build on every PR
- [ ] Test results visible in PR comments
- [ ] Staging deploys automatic on merge to main
- [ ] Production deploys require approval
- [ ] Pipeline execution time <10 minutes (p95)

### Container Platform
- [ ] EKS cluster running Kubernetes 1.28+
- [ ] Staging and production environments isolated
- [ ] Namespace provisioning automated
- [ ] Resource quotas enforced (CPU, memory, pods)
- [ ] Ingress controller with TLS termination
- [ ] Pod autoscaling based on CPU/memory

[Continues for all capabilities...]

### Cross-Cutting Requirements
- [ ] All services instrumented with logging
- [ ] All secrets stored in Vault (not environment variables)
- [ ] All platform APIs have ≥95% uptime SLA
- [ ] Platform team responds to issues in <30 minutes (business hours)
- [ ] Documentation exists for all self-service capabilities
```

## MVP Scoping Framework

### The 80/20 Rule
```
MVP should deliver:
✓ 80% of developer value
✓ With 20% of the effort of a "complete" platform

Focus on:
- High-frequency use cases (daily developer workflows)
- High-impact pain points (deployment friction, environment access)
- Reusable foundations (that enable Phase 2+ capabilities)
```

### Capability Prioritization Matrix

```
         │ High Value │ Low Value
─────────┼────────────┼───────────
High     │ MVP        │ Consider
Effort   │ (Do First) │ (Quick Wins)
─────────┼────────────┼───────────
Low      │ Phase 2+   │ Never
Effort   │ (Defer)    │ (Skip)
```

### Must-Have vs Nice-to-Have

**Must-Have (MVP Core)**:
- Basic service deployment (containers)
- Automated build and test
- Production-ready infrastructure
- Security baseline
- Developer documentation

**Nice-to-Have (Phase 2)**:
- Advanced automation
- Multi-region
- Service mesh
- Cost optimization
- Advanced observability

## Examples

### Example 1: Startup MVP (Small Scale)
```bash
/define-mvp --teams 10 --timeline 6-months --priorities "speed,cost"
```

Output:
```
MVP for 10 teams in 6 months (lean approach)
- Minimal developer portal (static docs)
- GitHub Actions with 2 templates
- EKS single environment
- Basic CloudWatch logging
- Total investment: $500K
```

### Example 2: Enterprise MVP (Large Scale)
```bash
/define-mvp --teams 200 --timeline 12-months --priorities "security,quality" --constraints "regulatory:soc2,budget:5M"
```

Output:
```
Enterprise MVP for 200 teams with SOC 2 compliance
- Full developer portal with SSO
- Advanced CI/CD with security gates
- Multi-environment EKS (dev, staging, prod)
- Comprehensive observability (Datadog)
- SOC 2 compliance controls
- Total investment: $4.8M
```

### Example 3: Migration MVP
```bash
/define-mvp --teams 75 --timeline 9-months --current-state "jenkins,ec2,manual" --format user-stories
```

Output: User story format focused on migrating from Jenkins/EC2 to modern platform

### Example 4: Minimal MVP (Proof of Value)
```bash
/define-mvp --teams 5 --timeline 3-months --format acceptance-criteria
```

Output: Acceptance criteria for a minimal pilot with 5 early adopter teams

## Capability Categories

### Tier 1 (Always in MVP)
```
✓ Service Deployment (containerization or equivalent)
✓ CI/CD Automation (at minimum: build + test)
✓ Developer Documentation
✓ Security Baseline (secrets, RBAC, scanning)
✓ Basic Observability (logging, monitoring)
```

### Tier 2 (Usually in MVP)
```
✓ Developer Portal (may be static docs initially)
✓ Self-Service Provisioning (may be semi-automated)
✓ Multiple environments (staging + production)
✓ Incident Management Integration
```

### Tier 3 (Phase 2)
```
✗ Service Mesh
✗ Advanced FinOps
✗ Multi-Region
✗ Chaos Engineering
✗ ML/AI Platform
```

## Resource Estimation

The skill automatically estimates resources based on team count:

```
Small MVP (≤25 teams):
- 3-4 platform engineers
- 1 product owner
- Budget: $1M-$2M

Medium MVP (25-100 teams):
- 6-8 platform engineers
- 2 product owners
- 1 technical writer
- Budget: $2M-$4M

Large MVP (100+ teams):
- 10-15 platform engineers
- 3 product owners
- 2 technical writers
- 1 program manager
- Budget: $4M-$8M
```

## Integration with Agents

```bash
# Define MVP via Strategy Agent
@strategy-agent "Define an MVP platform for 50 teams with 12-month timeline"

# Agent invokes:
/define-mvp --teams 50 --timeline 12-months --format detailed

# Then can call financial agent:
@financial-agent "Calculate ROI for this MVP"
```

## Best Practices

1. **Start Smaller**: When in doubt, reduce scope for MVP
2. **Vertical Slice**: MVP should deliver end-to-end value, not horizontal layers
3. **User-Centric**: Define MVP based on developer use cases, not technology features
4. **Measurable**: Include concrete success metrics
5. **Expandable**: MVP should be foundation for Phase 2, not throwaway
6. **Time-Boxed**: Fix timeline, flex scope if needed

## Common Pitfalls

❌ **Scope Creep**: Adding "just one more thing" to MVP
❌ **Perfectionism**: Polishing features beyond MVP necessity
❌ **Technology-First**: Choosing cool tech over developer needs
❌ **No Boundaries**: Not clearly defining what's OUT of scope
❌ **Unrealistic Timeline**: 12 months of work squeezed into 6 months

## MVP Validation Checklist

Before finalizing MVP definition:

```
[ ] Can be delivered in timeline with available resources
[ ] Delivers measurable value to developers
[ ] Has clear success criteria
[ ] Builds foundation for Phase 2
[ ] Has executive sponsorship
[ ] Has security/compliance approval
[ ] Has realistic budget
[ ] Teams willing to adopt (validated with 3+ pilot teams)
[ ] Technical feasibility proven (spike/POC completed)
[ ] Out-of-scope items explicitly listed
```

## Related Skills
- `/create-roadmap` - Place MVP in multi-year roadmap
- `/calculate-roi` - Calculate MVP investment return
- `/risk-assessment` - Identify MVP delivery risks
- `/stakeholder-map` - Identify MVP stakeholders

## Related Agents
- `@strategy-agent` - Strategic MVP guidance
- `@delivery-agent` - MVP execution planning
- `@stakeholder-agent` - MVP stakeholder alignment
- `@risk-agent` - MVP risk management

## Implementation Notes

This skill uses:
- Industry benchmarks for team-to-platform-engineer ratios
- Reference architectures from major cloud providers
- Team Topologies patterns for platform team sizing
- DORA metrics for success criteria

MVP definitions are opinionated based on best practices but can be customized based on your organization's specific context.
