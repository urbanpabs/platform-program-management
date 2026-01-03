# Skill: Create Roadmap

## Description
Generate a multi-year platform transformation roadmap with phased delivery milestones, dependencies, and success metrics.

## Usage
```bash
/create-roadmap --horizon 3-years --format timeline --include-metrics
```

## Parameters

### Required
- `--horizon` (string): Time horizon for the roadmap (e.g., "18-months", "2-years", "3-years", "5-years")

### Optional
- `--format` (string): Output format: "timeline", "gantt", "phases", "markdown" (default: "timeline")
- `--include-metrics` (boolean): Include success metrics and KPIs (default: true)
- `--include-dependencies` (boolean): Show cross-phase dependencies (default: true)
- `--mvp-only` (boolean): Focus on MVP phase only (default: false)
- `--verticals` (string): Comma-separated list of platform verticals to include (default: "all")
- `--risk-overlay` (boolean): Include risk indicators on timeline (default: false)
- `--resource-view` (boolean): Include resource allocation view (default: false)

## Output Formats

### Timeline Format
```
===========================================
PLATFORM TRANSFORMATION ROADMAP
===========================================
Horizon: 36 months (Q1 2026 - Q4 2028)
Strategy: Crawl → Walk → Run

────────────────────────────────────────
PHASE 1: FOUNDATION (MVP) - Months 0-12
────────────────────────────────────────
Objective: Establish core platform capabilities

Q1 2026 (Months 0-3):
├─ Developer Portal MVP
├─ CI/CD Standardization (GitHub Actions)
├─ Container Platform (EKS foundations)
└─ Initial Service Catalog (top 10 services)

Q2 2026 (Months 3-6):
├─ Self-Service Provisioning (Terraform modules)
├─ Observability Stack (Datadog integration)
├─ Secret Management (Vault deployment)
└─ Developer Onboarding Automation

Q3 2026 (Months 6-9):
├─ Platform API Gateway
├─ Internal Developer Documentation
├─ Golden Path Templates (3 languages)
└─ SRE Runbooks

Q4 2026 (Months 9-12):
├─ Initial Metrics Dashboard
├─ Developer Feedback Loop
├─ Security Scanning Integration
└─ MVP Retrospective & Phase 2 Planning

Success Metrics:
✓ 50% of teams onboarded
✓ 30% reduction in deployment time
✓ Developer satisfaction ≥ 7/10
✓ <2 hour time-to-first-deployment

────────────────────────────────────────
PHASE 2: SCALE - Months 12-24
────────────────────────────────────────
Objective: Scale adoption and optimize

[Similar structure for Phase 2...]

────────────────────────────────────────
PHASE 3: OPTIMIZE - Months 24-36
────────────────────────────────────────
Objective: Advanced capabilities and excellence

[Similar structure for Phase 3...]

────────────────────────────────────────
DEPENDENCIES
────────────────────────────────────────
Phase 1 → Phase 2: Container platform stability
Phase 2 → Phase 3: 80% team adoption
Cross-cutting: Security compliance throughout
```

### Gantt Chart Format
```
ASCII Gantt chart showing:
- Tasks as horizontal bars
- Dependencies as arrows
- Milestones as diamonds
- Critical path highlighted
```

### Phases Format
```markdown
## Phase 1: Foundation (MVP)
**Timeline**: Months 0-12
**Investment**: $2.5M CAPEX, $400K OPEX
**Teams**: 8 FTE platform team + 2 FTE product

### Goals
1. Establish core platform services
2. Onboard first 50% of development teams
3. Achieve baseline developer productivity gains

### Key Deliverables
- Developer Portal (Q2)
- CI/CD Standardization (Q1-Q2)
- Container Platform MVP (Q1-Q3)
- Golden Path Templates (Q3)

### Success Criteria
- 50% team adoption
- 30% deployment time reduction
- Developer NPS ≥ 30

### Risks
- Risk 1: Kubernetes expertise gap (Mitigation: Training + hire)
- Risk 2: Resistance from legacy teams (Mitigation: Incentives)

---

## Phase 2: Scale
[Similar structure...]
```

### Markdown Format
Complete markdown document with:
- Executive summary
- Vision and strategy
- Phase-by-phase breakdown
- Dependency maps
- Resource requirements
- Success metrics
- Risk management

## Roadmap Templates

### Crawl-Walk-Run Framework
```
CRAWL (Months 0-12): Foundation & MVP
→ Core infrastructure
→ Initial team onboarding
→ Prove value with early wins

WALK (Months 12-24): Scale & Adoption
→ Expand to majority of teams
→ Advanced capabilities
→ Optimize based on feedback

RUN (Months 24-36): Excellence & Innovation
→ Full organizational adoption
→ Advanced automation
→ Continuous improvement culture
```

### Platform Vertical Examples
```
Common Verticals:
- Developer Experience (Portal, Docs, Onboarding)
- CI/CD & Build Systems
- Container Orchestration (Kubernetes)
- Observability (Monitoring, Logging, Tracing)
- Security & Compliance
- Data Platform
- Service Mesh & Networking
- Infrastructure as Code
```

## Success Metrics by Phase

### Phase 1 (MVP) Metrics
```
Developer Productivity:
- Time to first deployment: <2 hours (baseline: 2 days)
- PR to production: <1 day (baseline: 5 days)
- Failed deployments: <5% (baseline: 15%)

Adoption:
- Teams onboarded: ≥50%
- Active platform users: ≥100 developers
- Self-service usage: ≥60% of provisions

Quality:
- Platform uptime: ≥99.5%
- Security scan coverage: 100%
- Incident resolution time: <30 min
```

### Phase 2 (Scale) Metrics
```
[Progressive improvement on Phase 1 metrics...]
```

## Examples

### Example 1: Basic 3-Year Roadmap
```bash
/create-roadmap --horizon 3-years
```

Output: Timeline format roadmap with 3 phases (Foundation, Scale, Optimize) covering 36 months

### Example 2: MVP-Focused Roadmap
```bash
/create-roadmap --horizon 12-months --mvp-only --include-metrics
```

Output: Detailed 12-month MVP roadmap with quarterly breakdown and success metrics

### Example 3: Specific Verticals
```bash
/create-roadmap --horizon 2-years --verticals "cicd,containers,observability" --format phases
```

Output: Phase-based roadmap focusing only on CI/CD, Container Platform, and Observability verticals

### Example 4: Executive Presentation
```bash
/create-roadmap --horizon 3-years --format markdown --risk-overlay --resource-view
```

Output: Comprehensive markdown document with risk indicators and resource allocation for executive review

## Dependencies

The roadmap automatically considers:

### Technical Dependencies
```
Container Platform → Service Mesh
CI/CD Platform → Security Scanning
Identity Management → All Services
Observability → Incident Response
```

### Organizational Dependencies
```
Training Programs → Tool Adoption
Executive Sponsorship → Budget Allocation
Security Sign-off → Production Deployment
```

### Sequencing Rules
```
1. Infrastructure before applications
2. Security baseline before scale
3. Monitoring before production workloads
4. Documentation before self-service
```

## Customization

### Custom Phases
You can specify custom phase definitions:

```bash
/create-roadmap --horizon 18-months --phases "prototype,pilot,scale"
```

### Custom Milestones
Add specific milestone requirements:

```bash
/create-roadmap --horizon 2-years --milestones "soc2-audit:M12,fedramp:M24"
```

## Integration with Agents

This skill is designed to work with multiple agents:

```bash
# Create roadmap via Strategy Agent
@strategy-agent "Create a 3-year platform transformation roadmap for 500-person engineering org"

# The agent will invoke:
/create-roadmap --horizon 3-years --include-metrics --resource-view

# Then optionally call financial agent for ROI:
@financial-agent "Calculate ROI for the roadmap phases"
```

## Best Practices

1. **Start with MVP**: Always define a clear 6-12 month MVP phase
2. **Quarterly Reviews**: Plan for roadmap adjustments every quarter
3. **Dependencies First**: Map dependencies before committing to timelines
4. **Resource Reality**: Ensure resource allocations are realistic
5. **Metrics-Driven**: Define measurable success criteria for each phase
6. **Stakeholder Alignment**: Review roadmap with all key stakeholders before committing

## Common Pitfalls

❌ **Too Ambitious**: Trying to deliver everything in Phase 1
❌ **No Metrics**: Roadmap without success criteria
❌ **Ignoring Dependencies**: Scheduling work without considering blockers
❌ **Fixed Timeline**: Not allowing for learning and iteration
❌ **No Risk Planning**: Optimistic timeline without contingency

## Anti-Patterns

### Big Bang Approach
```
❌ WRONG: Launch entire platform in month 18
✅ RIGHT: Incremental rollout with feedback loops
```

### Feature-Focused
```
❌ WRONG: List of tools/features to build
✅ RIGHT: Outcomes and capabilities to deliver
```

### Technology-First
```
❌ WRONG: "Deploy Kubernetes" as a milestone
✅ RIGHT: "Enable self-service container deployment" as a milestone
```

## Output Templates

### Executive Summary Template
```markdown
## Platform Transformation Roadmap - Executive Summary

**Vision**: [One sentence vision statement]
**Horizon**: [Time period]
**Investment**: [Total investment over period]
**Expected ROI**: [ROI percentage and payback period]

### Strategic Phases
1. **Phase 1 (Months 0-12)**: Foundation - Establish core capabilities
2. **Phase 2 (Months 12-24)**: Scale - Drive adoption and optimization
3. **Phase 3 (Months 24-36)**: Excellence - Advanced capabilities and innovation

### Key Milestones
- M6: Developer Portal MVP launch
- M12: 50% team adoption
- M18: Full CI/CD automation
- M24: 90% team adoption
- M36: Platform excellence state

### Success Metrics
- Developer productivity: +40% by M36
- Deployment frequency: 10x increase
- Lead time: 80% reduction
- Platform uptime: 99.9%
```

## Related Skills
- `/define-mvp` - Define detailed MVP scope
- `/calculate-roi` - Calculate financial returns per phase
- `/dependency-analysis` - Deep dive on dependencies
- `/risk-assessment` - Identify roadmap risks

## Related Agents
- `@strategy-agent` - Strategic roadmap guidance
- `@delivery-agent` - Execution planning
- `@financial-agent` - Budget and ROI alignment
- `@risk-agent` - Risk identification

## Implementation Notes

The roadmap generator uses:
- Industry best practices for platform engineering
- DORA metrics framework for success criteria
- Team Topologies organizational patterns
- Reference architectures from AWS, Azure, GCP

For custom roadmaps specific to your industry (e.g., FinTech, Healthcare), provide additional context when invoking the skill.
