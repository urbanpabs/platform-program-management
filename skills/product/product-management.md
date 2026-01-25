# Skill: Product Management

## Description
Comprehensive product management skill for platform engineering programs. Covers product strategy, feature prioritization, user story mapping, product metrics, and product discovery. Designed for Platform Product Managers driving internal developer platform adoption.

## Usage
```bash
/product-management --action "prioritize-features" --method "rice"
/product-management --action "create-okrs" --quarter "Q1 2026"
/product-management --action "user-story-map" --epic "self-service provisioning"
/product-management --action "product-metrics" --domain "developer-experience"
/product-management --action "discovery" --opportunity "cloud-development-environments"
```

## Parameters

### Required
- `--action` (string): Product management action to perform:
  - `prioritize-features` - Prioritize backlog using scoring frameworks
  - `create-okrs` - Define Objectives and Key Results
  - `user-story-map` - Create user story map for an epic
  - `product-metrics` - Define and track product metrics
  - `discovery` - Product discovery and opportunity assessment
  - `competitive-analysis` - Analyze competitive landscape
  - `roadmap-planning` - Product roadmap planning session

### Optional
- `--method` (string): Prioritization method: "rice", "wsjf", "moscow", "kano", "ice" (default: "rice")
- `--quarter` (string): Target quarter for OKRs (e.g., "Q1 2026")
- `--epic` (string): Epic name for user story mapping
- `--domain` (string): Product domain: "developer-experience", "platform-adoption", "self-service", "observability", "security"
- `--opportunity` (string): Opportunity to assess for discovery
- `--output` (string): Output format: "markdown", "html", "json" (default: "markdown")

---

## Core Capabilities

### 1. Feature Prioritization Frameworks

#### RICE Scoring (Reach, Impact, Confidence, Effort)

```markdown
# Feature Prioritization: RICE Analysis

## Scoring Criteria

### Reach (per quarter)
- How many developers will this feature impact?
- Measured in: developers/quarter

### Impact (scale 0.25 - 3)
- Massive (3x): Transforms developer experience
- High (2x): Significant improvement
- Medium (1x): Noticeable improvement
- Low (0.5x): Minor improvement
- Minimal (0.25x): Negligible improvement

### Confidence (%)
- High (100%): Validated with user research
- Medium (80%): Based on strong signals
- Low (50%): Educated guess
- Moonshot (20%): Speculative

### Effort (person-months)
- Development effort required

### RICE Score Formula
```
RICE Score = (Reach × Impact × Confidence) / Effort
```

## Feature Ranking

| Rank | Feature | Reach | Impact | Confidence | Effort | RICE Score |
|------|---------|-------|--------|------------|--------|------------|
| 1 | Self-service DB provisioning | 500 | 3 | 80% | 2 | 600 |
| 2 | GitHub Actions templates | 800 | 2 | 100% | 3 | 533 |
| 3 | One-click staging env | 300 | 3 | 80% | 2 | 360 |
| 4 | Automated security scans | 500 | 2 | 80% | 3 | 267 |
| 5 | Developer portal search | 800 | 1 | 100% | 4 | 200 |

## Recommendation
**Priority 1**: Self-service DB provisioning
- Highest RICE score (600)
- Addresses #1 developer pain point (3-5 day wait)
- Validated through developer surveys (80% confidence)
```

---

#### WSJF (Weighted Shortest Job First)

```markdown
# Feature Prioritization: WSJF Analysis

## Cost of Delay Components

### User-Business Value (1-10)
How much value does this deliver to users/business?

### Time Criticality (1-10)
How urgent is delivery? Are there deadlines or windows?

### Risk Reduction / Opportunity Enablement (1-10)
Does this reduce risk or enable future opportunities?

### Cost of Delay = User Value + Time Criticality + Risk Reduction

### Job Duration (relative sizing)
1 = Small (1-2 weeks)
2 = Medium (2-4 weeks)
3 = Large (4-8 weeks)
5 = XL (8+ weeks)

### WSJF Formula
```
WSJF = Cost of Delay / Job Duration
```

## Feature Ranking

| Feature | User Value | Time Crit. | Risk Red. | CoD | Duration | WSJF |
|---------|------------|------------|-----------|-----|----------|------|
| Kratix promises | 8 | 9 | 7 | 24 | 2 | 12.0 |
| Cortex scorecards | 7 | 8 | 6 | 21 | 2 | 10.5 |
| Harness integration | 9 | 6 | 5 | 20 | 2 | 10.0 |
| Coder CDE | 8 | 5 | 7 | 20 | 3 | 6.7 |
| Full observability | 7 | 4 | 8 | 19 | 5 | 3.8 |

## Recommendation
**Sequence**: Kratix → Cortex → Harness → Coder → Observability
```

---

### 2. OKR Framework

```markdown
# Platform Product OKRs: Q1 2026

## Objective 1: Accelerate Developer Self-Service
**Why**: Developers wait 3-5 days for infrastructure. Eliminating this friction unlocks velocity.

### Key Results

| KR# | Key Result | Baseline | Target | Current | Status |
|-----|------------|----------|--------|---------|--------|
| 1.1 | Reduce infrastructure provisioning time from 5 days to <5 minutes | 5 days | 5 min | - | Not Started |
| 1.2 | Achieve 50% developer adoption of self-service portal | 0% | 50% | - | Not Started |
| 1.3 | Decrease tickets to platform team by 40% | 200/week | 120/week | - | Not Started |

### Initiatives
- Self-service database provisioning (CLI + Portal)
- Automated namespace provisioning via Kratix
- Developer portal catalog with one-click templates

---

## Objective 2: Establish Production Readiness Visibility
**Why**: Leadership lacks visibility into service health. Scorecards enable data-driven decisions.

### Key Results

| KR# | Key Result | Baseline | Target | Current | Status |
|-----|------------|----------|--------|---------|--------|
| 2.1 | 100% of production services registered in Cortex catalog | 40% | 100% | - | Not Started |
| 2.2 | All services have production readiness scorecard | 0% | 100% | - | Not Started |
| 2.3 | 70% of services at Bronze level or higher | 0% | 70% | - | Not Started |

### Initiatives
- Cortex.io deployment and integration
- Custom CQL scorecards for production readiness
- Engineering Intelligence dashboards for leadership

---

## Objective 3: Improve Platform Reliability & Trust
**Why**: Developer trust in platform directly impacts adoption. Reliability is the foundation.

### Key Results

| KR# | Key Result | Baseline | Target | Current | Status |
|-----|------------|----------|--------|---------|--------|
| 3.1 | Platform availability ≥99.9% | 99.5% | 99.9% | - | Not Started |
| 3.2 | Mean time to recover (MTTR) <15 minutes | 45 min | 15 min | - | Not Started |
| 3.3 | Zero P1 incidents caused by platform changes | 3/quarter | 0 | - | Not Started |

### Initiatives
- SLO/SLI framework implementation
- Automated rollback capabilities
- Chaos engineering program

---

## OKR Tracking Cadence

| Cadence | Activity | Participants |
|---------|----------|--------------|
| Weekly | KR progress check-in | Product Manager, Tech Lead |
| Bi-weekly | Sprint demo with OKR alignment | Full team + stakeholders |
| Monthly | OKR review with leadership | PM, EM, Director |
| Quarterly | OKR retrospective and planning | All stakeholders |
```

---

### 3. User Story Mapping

```markdown
# User Story Map: Self-Service Database Provisioning

## Backbone (User Journey)

```
[Discover] → [Request] → [Configure] → [Provision] → [Connect] → [Manage] → [Decommission]
```

## Walking Skeleton (MVP)

| Phase | User Activity | MVP Stories |
|-------|---------------|-------------|
| Discover | Find what databases are available | View available DB types in catalog |
| Request | Request a new database | Submit request via CLI/Portal |
| Configure | Specify database settings | Select type, size, environment |
| Provision | Database gets created | Automated provisioning in <5 min |
| Connect | Get connection credentials | Receive connection string |
| Manage | Monitor and maintain | View database status |
| Decommission | Delete when done | Delete database with safeguards |

---

## Story Slices (by priority)

### Release 1: CLI-First MVP
```
[Discover]     [Request]       [Configure]     [Provision]     [Connect]
    |              |               |               |              |
As a dev,      As a dev,       As a dev,       As a dev,      As a dev,
I can see      I can request   I can specify   I can wait     I can get
available DB   a DB via CLI    DB type and     <5 min for     connection
types in docs  command         size            provisioning   string
```

### Release 2: Portal Experience
```
[Discover]     [Request]       [Configure]     [Provision]     [Connect]
    |              |               |               |              |
As a dev,      As a dev,       As a dev,       As a dev,      As a dev,
I can browse   I can request   I can use       I can see      I can copy
DB catalog     DB via portal   form wizard     progress bar   conn string
in portal      UI              with defaults                  from portal
```

### Release 3: Advanced Management
```
[Manage]                               [Decommission]
    |                                       |
As a dev, I can:                       As a dev, I can:
- View DB metrics                      - Request deletion
- See storage usage                    - Confirm with safeguard
- Check connection count               - Auto-backup before delete
- View cost attribution
```

---

## Acceptance Criteria (MVP)

### Story: Submit request via CLI
```gherkin
Given I have platform CLI installed
And I am authenticated
When I run `platform db create --type postgres --size medium`
Then I should see a cost estimate
And be prompted to confirm
And receive a request confirmation ID
```

### Story: Automated provisioning in <5 min
```gherkin
Given I have submitted a DB request
When the request is confirmed
Then the database should be provisioned within 5 minutes
And I should receive a notification when complete
And the database should be accessible
```

### Story: Receive connection string
```gherkin
Given my database has been provisioned
When I run `platform db info <db-name> --show-credentials`
Then I should see the connection string
And the credentials should be stored in my local credential store
```

---

## Dependencies

| Story | Depends On | Blocks |
|-------|------------|--------|
| CLI provisioning | Kratix promises, Harness pipeline | Portal UI |
| Cost estimation | Finance API integration | CLI provisioning |
| Credential storage | Secrets management (Vault) | Connection retrieval |
| Portal UI | CLI backend API | - |
```

---

### 4. Product Metrics Framework

```markdown
# Platform Product Metrics: Developer Experience

## North Star Metric
**Developer Velocity Index (DVI)**
Composite metric measuring how fast developers can ship value.

Formula:
```
DVI = (Deployment Frequency × Change Success Rate) / Lead Time
```

Target: 10x improvement over baseline

---

## Metric Hierarchy

### Level 1: Business Outcomes

| Metric | Definition | Target | Current |
|--------|------------|--------|---------|
| **Time to Market** | Idea to production | -40% | Baseline |
| **Developer Productivity** | Features shipped per developer | +30% | Baseline |
| **Platform ROI** | Value delivered / Platform cost | 5x | Measuring |

---

### Level 2: User Outcomes

| Metric | Definition | Target | Current |
|--------|------------|--------|---------|
| **Developer NPS** | Would recommend platform | >50 | Survey |
| **Self-Service Rate** | % tasks completed without ticket | >80% | 20% |
| **Platform Adoption** | % developers using platform | >90% | 40% |
| **Time Saved per Developer** | Hours saved per week | 5+ hours | Measuring |

---

### Level 3: DORA Metrics (via Cortex)

| Metric | Elite | High | Medium | Low | Current |
|--------|-------|------|--------|-----|---------|
| **Deployment Frequency** | On-demand | Daily-weekly | Weekly-monthly | Monthly+ | Weekly |
| **Lead Time for Changes** | <1 hour | <1 day | <1 week | >1 month | 3 days |
| **Change Failure Rate** | <5% | 5-10% | 10-15% | >15% | 12% |
| **MTTR** | <1 hour | <1 day | <1 week | >1 month | 4 hours |

---

### Level 4: Feature Metrics

| Feature | Metric | Target | Current |
|---------|--------|--------|---------|
| **Self-Service DB** | Provisioning time | <5 min | 5 days |
| **Self-Service DB** | Adoption rate | 70% | 0% |
| **Scorecards** | Services cataloged | 100% | 40% |
| **Scorecards** | Bronze+ compliance | 70% | 0% |
| **Developer Portal** | Weekly active users | 500 | 0 |
| **Developer Portal** | Search success rate | >90% | N/A |

---

## Measurement Plan

| Metric | Data Source | Collection | Dashboard |
|--------|-------------|------------|-----------|
| Deployment Frequency | Harness | Automatic | Cortex |
| Lead Time | GitHub + Harness | Automatic | Cortex |
| Developer NPS | Quarterly survey | Manual | Tableau |
| Self-Service Rate | ServiceNow tickets | Automatic | ServiceNow |
| Platform Adoption | Cortex catalog | Automatic | Cortex |
| Provisioning Time | Kratix logs | Automatic | Grafana |
```

---

### 5. Product Discovery

```markdown
# Product Discovery: Cloud Development Environments

## Opportunity Assessment

### Opportunity Statement
Developers spend 2+ hours setting up local development environments, leading to inconsistent setups, "works on my machine" issues, and delayed onboarding.

### Opportunity Size
- **Developers affected**: 800
- **Time wasted per developer**: 2 hours/week
- **Annual cost**: 800 × 2 × 52 × $75/hr = **$6.24M**

### Confidence Level
- **Problem confidence**: 90% (survey data, support tickets)
- **Solution confidence**: 60% (need to validate approach)

---

## Discovery Activities

### 1. User Research

#### Interview Insights (15 developers)
| Theme | Frequency | Quote |
|-------|-----------|-------|
| Setup time | 13/15 | "I spent my first 3 days just getting things running" |
| Inconsistency | 11/15 | "It works on my machine but fails in CI" |
| Onboarding | 10/15 | "New hires are blocked for a week" |
| Resource limits | 8/15 | "My laptop can't run the full stack" |
| Remote work | 7/15 | "VPN + local dev is painfully slow" |

#### Persona: Backend Developer (Sam)
- **Context**: Works on Java microservices, needs multiple services running locally
- **Pain**: Spends Monday mornings fixing broken local setup
- **Goal**: Start coding immediately without environment issues
- **Quote**: "I just want to open my laptop and code"

---

### 2. Solution Exploration

#### Option A: Cloud Development Environment (Coder)
**Description**: Browser-based IDE with pre-configured environments

**Pros**:
- Instant environment spin-up
- Consistent across all developers
- No local resource constraints
- Built-in collaboration features

**Cons**:
- Requires always-on internet
- Learning curve for new workflow
- Monthly per-seat cost ($30-50/user)

**Estimated Cost**: $30/user × 800 = $24,000/month

---

#### Option B: Dev Containers (VS Code)
**Description**: Containerized local development with shared configs

**Pros**:
- Works offline
- Familiar local workflow
- Lower cost (infrastructure only)
- Already have container expertise

**Cons**:
- Still uses local resources
- Docker Desktop licensing
- Setup still required per project

**Estimated Cost**: Docker licensing + infra = ~$10,000/month

---

#### Option C: Hybrid Approach
**Description**: Dev containers for simple projects, cloud IDE for complex stacks

**Pros**:
- Best of both worlds
- Cost-optimized by use case
- Gradual migration path

**Cons**:
- Two systems to maintain
- Complexity in tooling

**Estimated Cost**: ~$15,000/month

---

### 3. Validation Plan

#### Prototype Test (2 weeks)
- Deploy Coder pilot for 20 developers
- Measure: setup time, satisfaction, adoption
- Success criteria: 80% prefer cloud IDE

#### Metrics to Track
| Metric | Baseline | Target | Method |
|--------|----------|--------|--------|
| Environment setup time | 2 hours | 5 minutes | Logging |
| "Works on my machine" incidents | 15/week | <5/week | Jira |
| Developer satisfaction | 3.2/5 | 4.5/5 | Survey |
| Onboarding time | 5 days | 1 day | HR tracking |

---

### 4. Recommendation

**Proceed with Option A (Coder Cloud IDE)**

**Rationale**:
- Highest ROI: $6.24M problem / $288K annual cost = 21x return
- Aligns with remote-first strategy
- Integrates with Cortex for visibility
- Reduces platform team support burden

**Next Steps**:
1. Secure budget approval for pilot ($5,000)
2. Configure Coder templates for top 5 project types
3. Run 20-developer pilot for 2 weeks
4. Present results to stakeholders

**Decision Deadline**: End of month
```

---

## Output Structure

```
product-management/
├── prioritization/
│   ├── rice-analysis.md
│   ├── wsjf-analysis.md
│   └── backlog-ranking.md
├── okrs/
│   ├── Q1-2026-okrs.md
│   └── okr-tracking.md
├── story-maps/
│   ├── self-service-provisioning.md
│   ├── developer-portal.md
│   └── observability-platform.md
├── metrics/
│   ├── north-star-metrics.md
│   ├── dora-metrics.md
│   └── feature-metrics.md
├── discovery/
│   ├── opportunity-assessments/
│   │   ├── cloud-dev-environments.md
│   │   └── api-gateway.md
│   ├── user-research/
│   │   └── interview-synthesis.md
│   └── experiments/
│       └── coder-pilot-results.md
└── competitive/
    └── idp-landscape-analysis.md
```

---

## Integration with Agents

```bash
# Use with Product Prototyping Agent
@product-prototyping-agent "Prioritize our feature backlog using RICE"

# Combine with Strategy Agent
@strategy-agent "Align our OKRs with the platform roadmap"

# Work with Stakeholder Agent
@stakeholder-agent "Present OKR progress to leadership"

# Coordinate with Delivery Agent
@delivery-agent "Map story dependencies for sprint planning"
```

---

## Related Skills

- `/prototype-generator` - Create prototypes for validated opportunities
- `/create-roadmap` - Align product priorities to roadmap
- `/value-narrative` - Communicate product value to stakeholders
- `/stakeholder-map` - Identify product stakeholders
- `/platform-analytics` - Track product metrics

---

## Related Agents

- `@product-prototyping-agent` - Rapid prototype generation
- `@strategy-agent` - Strategic alignment
- `@financial-agent` - ROI calculations for features
- `@stakeholder-agent` - Stakeholder engagement
- `@delivery-agent` - Execution planning

---

## Best Practices

### 1. Ruthless Prioritization
Don't try to do everything. Use frameworks to make hard tradeoffs.

### 2. Outcome Over Output
Measure results (developer velocity), not just features shipped.

### 3. Continuous Discovery
Always have discovery running in parallel with delivery.

### 4. Data-Informed, Not Data-Driven
Use data to inform decisions, not replace judgment.

### 5. Build for Adoption
A feature not adopted is a feature not delivered.

---

**Skill Owner**: Platform Program Management Repository
**Last Updated**: January 2026
**Version**: 1.0
