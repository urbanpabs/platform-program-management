# Skill: Dependency Analysis

## Description
Analyze cross-team and cross-vertical dependencies with critical path identification, bottleneck detection, and resolution strategies.

## Usage
```bash
/dependency-analysis --initiative "platform-transformation" --teams 50 --format network-graph
```

## Parameters

### Required
- `--initiative` (string): Initiative or program name

### Optional
- `--teams` (number): Number of teams involved (default: 10)
- `--verticals` (string): Platform verticals to analyze: "cicd,containers,observability,security" (comma-separated, default: "all")
- `--format` (string): Output format: "network-graph", "matrix", "critical-path", "timeline" (default: "network-graph")
- `--phase` (string): Program phase: "planning", "execution", "scaling" (default: "execution")
- `--include-external` (boolean): Include external dependencies (vendors, third parties) (default: true)
- `--time-horizon` (string): Analysis timeframe: "current-sprint", "current-quarter", "full-program" (default: "current-quarter")

## Output Formats

### Network Graph Format
```
═══════════════════════════════════════════════════════════
DEPENDENCY NETWORK: PLATFORM TRANSFORMATION
═══════════════════════════════════════════════════════════
Initiative: Platform Transformation MVP
Teams: 50 development teams + 1 platform team
Phase: Execution (Q1-Q2 FY2026)
Timeframe: Current Quarter (Q1)

───────────────────────────────────────────────────────────
DEPENDENCY GRAPH
───────────────────────────────────────────────────────────

Legend:
  [Component]           = Work item or deliverable
  ──────────>           = "Depends on" relationship
  ═════════>            = Critical path dependency
  - - - - ->            = Optional/soft dependency
  (TEAM)                = Responsible team

───────────────────────────────────────────────────────────

                    [Platform Foundation]
                    ═════════════════════>
                            │
                ┌───────────┼───────────┐
                │           │           │
                ▼           ▼           ▼
        [Container      [CI/CD       [Security
         Platform]      Platform]     Baseline]
        (Platform)     (Platform)    (Security)
                │           │           │
                │           │           │
    ┌───────────┼───────────┼───────────┼───────────┐
    │           │           │           │           │
    ▼           ▼           ▼           ▼           ▼
[Developer  [Observ-   [Service    [Secret      [RBAC &
 Portal]    ability]   Catalog]    Mgmt]        AuthN]
(Platform) (Platform)  (Platform)  (Security)   (Security)
    │           │           │           │           │
    │           │           │           │           │
    └───────────┴───────────┴───────────┴───────────┘
                            │
                ┌───────────┼───────────┐
                │           │           │
                ▼           ▼           ▼
        [Team A        [Team B      [Team C
      Onboarding]    Onboarding]  Onboarding]
      (Product)      (Product)    (Product)
                            │
                            ▼
                    [MVP Complete]

───────────────────────────────────────────────────────────

CRITICAL PATH (highlighted with ═════> ):
Platform Foundation → Container Platform → Service Catalog
→ Team Onboarding → MVP Complete

Estimated Duration: 12 weeks
Critical Path Float: 1 week (low buffer, high risk)

───────────────────────────────────────────────────────────
DEPENDENCY TYPES
───────────────────────────────────────────────────────────

Technical Dependencies (8):
├─ Container Platform → CI/CD Platform
│  Description: CI/CD needs container registry and orchestration
│  Type: HARD (blocking)
│  Owner: Platform Team
│  Status: 🟢 Complete

├─ Security Baseline → All Services
│  Description: Security scanning, RBAC, secrets must be ready
│  Type: HARD (blocking)
│  Owner: Security Team
│  Status: 🟢 Complete

├─ Observability → Team Onboarding
│  Description: Teams need logging/monitoring before production
│  Type: HARD (blocking)
│  Owner: Platform Team
│  Status: 🟡 In Progress (60% complete)

[... continues for all 8 technical dependencies ...]

Process Dependencies (5):
├─ Security Review → Production Deployment
│  Description: CISO sign-off required before prod
│  Type: HARD (blocking)
│  Owner: CISO
│  Status: 🟢 Process defined

├─ Budget Approval → Vendor Procurement
│  Description: CFO approval needed for tooling purchases
│  Type: HARD (blocking)
│  Owner: CFO
│  Status: 🟢 FY2026 budget approved

[... continues for all process dependencies ...]

Resource Dependencies (6):
├─ Platform Team Bandwidth → Multiple Verticals
│  Description: Platform team stretched across CI/CD, containers, portal
│  Type: SOFT (capacity constraint)
│  Owner: VP Engineering
│  Status: 🟡 Adding 2 engineers in Q2

├─ Security Team Reviews → All Team Onboardings
│  Description: Security review required per team (bottleneck)
│  Type: SOFT (capacity constraint)
│  Owner: CISO
│  Status: 🔴 Bottleneck identified

[... continues for all resource dependencies ...]

Knowledge Dependencies (4):
├─ Kubernetes Training → Platform Team
│  Description: Team needs K8s expertise before production
│  Type: HARD (skill requirement)
│  Owner: Platform Team Lead
│  Status: 🟢 Training 80% complete

├─ Developer Documentation → Team Onboarding
│  Description: Teams need self-service docs before onboarding
│  Type: HARD (enablement requirement)
│  Owner: Technical Writer
│  Status: 🟡 Docs 70% complete

[... continues for all knowledge dependencies ...]

External Dependencies (3):
├─ AWS EKS Cluster Provisioning → Container Platform
│  Description: AWS to provision production EKS cluster
│  Type: HARD (vendor delivery)
│  Owner: AWS (external)
│  Status: 🟢 Delivered (2 days ahead of SLA)

├─ GitHub Enterprise License → CI/CD Platform
│  Description: GitHub contract signed and license activated
│  Type: HARD (vendor procurement)
│  Owner: GitHub (external)
│  Status: 🟢 Active

[... continues for external dependencies ...]

───────────────────────────────────────────────────────────
BOTTLENECKS IDENTIFIED
───────────────────────────────────────────────────────────

🔴 CRITICAL BOTTLENECK: Security Review Capacity

Location: Team Onboarding Phase
Impact: 15 teams waiting for security review approval
Delay: 2-3 weeks per team (should be 2-3 days)
Root Cause: Security team capacity (2 FTE for 50 teams)

Resolution Strategy:
1. Automate security baseline checks (reduce manual review need)
2. Batch reviews (5 teams per week vs 1 at a time)
3. Hire 1 additional security engineer (approved, Q2 start)
4. Create "pre-approved" templates for standard architectures

Owner: CISO
Target Resolution: March 15, 2026
Risk if Unresolved: 6-week program delay

───────────────────────────────────────────────────────────

🟡 MEDIUM BOTTLENECK: Platform Team Bandwidth

Location: Observability, Developer Portal support
Impact: Concurrent work across 3 verticals (CI/CD, containers, observability)
Delay: 1-2 week slip in non-critical path items
Root Cause: Platform team size (6 FTE for broad scope)

Resolution Strategy:
1. Hire 2 additional platform engineers (approved, Q2)
2. Prioritize critical path work (deprioritize nice-to-haves)
3. Leverage vendor support (AWS, Datadog) for operational load
4. Automate repetitive tasks (onboarding workflows)

Owner: VP Engineering
Target Resolution: April 1, 2026
Risk if Unresolved: Team burnout, quality issues

───────────────────────────────────────────────────────────
DEPENDENCY MATRIX
───────────────────────────────────────────────────────────

              │Cont│CICD│Sec │Obs │Port│Svc │Team
              │Plat│Plat│Base│    │    │Cat │On
──────────────┼────┼────┼────┼────┼────┼────┼────
Container Plat│ -  │    │    │    │    │    │
CI/CD Platform│ ●  │ -  │    │    │    │    │
Security Base │    │    │ -  │    │    │    │
Observability │ ●  │    │ ●  │ -  │    │    │
Portal        │ ●  │ ●  │ ●  │    │ -  │    │
Service Catalog│ ●  │ ●  │ ●  │    │ ●  │ -  │
Team Onboard  │ ●  │ ●  │ ●  │ ●  │ ●  │ ●  │ -

● = Depends on (blocks if not complete)

Reading: Each row depends on columns with ●
Example: Team Onboarding depends on Container Platform, CI/CD,
         Security Baseline, Observability, Portal, Service Catalog

───────────────────────────────────────────────────────────
CRITICAL PATH ANALYSIS
───────────────────────────────────────────────────────────

Critical Path (12 weeks total):

Week 0-2:   Platform Foundation (Infrastructure setup)
            Status: 🟢 Complete

Week 2-5:   Container Platform (EKS staging + production)
            Status: 🟡 90% complete (prod final testing)
            Float: 0 weeks (on critical path)

Week 5-7:   Service Catalog + Developer Portal
            Status: 🟢 Complete
            Float: 0 weeks

Week 7-10:  Observability Integration
            Status: 🟡 60% complete
            Float: 0 weeks (CRITICAL - no buffer)
            Risk: 🔴 Potential 1-week slip

Week 10-12: Team Onboarding (first wave, 15 teams)
            Status: 🟡 Not started (blocked by observability)
            Float: 0 weeks
            Risk: 🔴 Security review bottleneck

Week 12:    MVP Complete (50 teams target)
            Status: ⏳ On track with risks
            Confidence: 70% (due to bottlenecks)

CRITICAL PATH RISKS:
⚠ Observability delay would cascade to onboarding (no float)
⚠ Security review bottleneck could add 2-3 weeks
⚠ Any critical path item slip directly impacts MVP date

───────────────────────────────────────────────────────────
DEPENDENCY RESOLUTION STATUS
───────────────────────────────────────────────────────────

Total Dependencies: 26
├─ Resolved (Complete): 12 (46%)  🟢
├─ In Progress:         10 (38%)  🟡
├─ Blocked:              3 (12%)  🔴
└─ Not Started:          1 (4%)   ⏳

Blocked Dependencies:

1. Team C Onboarding → Blocked by Security Review
   Blocker: Security team capacity bottleneck
   Impact: 3-week delay for Team C
   Resolution: Fast-track security automation (ETA: Mar 15)

2. Observability Prod Rollout → Blocked by Datadog Config
   Blocker: Complex APM instrumentation for legacy apps
   Impact: 1-week delay
   Resolution: Datadog support engaged (ETA: Mar 1)

3. Self-Service DB Provisioning → Blocked by DBA Approval
   Blocker: DBA team requires manual review per request
   Impact: Not on critical path, but slows Phase 2
   Resolution: Negotiate automated approval for standard configs

───────────────────────────────────────────────────────────
RECOMMENDATIONS
───────────────────────────────────────────────────────────

🔴 URGENT (This Week):

1. Unblock Security Review Bottleneck
   - Implement automated security baseline checks
   - Batch team reviews (5 teams/week)
   - Fast-track security engineer hiring

2. Accelerate Observability Rollout
   - Assign dedicated engineer (pull from non-critical work)
   - Engage Datadog support for complex legacy apps
   - Consider phased rollout (new apps first, legacy later)

🟡 IMPORTANT (Next 2 Weeks):

3. Add Buffer to Critical Path
   - Identify opportunities to parallelize work
   - Pre-approve standard architectures (reduce review cycles)
   - Add 1 week buffer before MVP deadline (move from June 30 → June 23)

4. Improve Cross-Team Coordination
   - Weekly dependency sync meeting (Platform, Security, Product teams)
   - Shared dependency tracker (visible to all teams)
   - Early warning system for slipping dependencies
```

### Matrix Format
```
═══════════════════════════════════════════════════════════
DEPENDENCY MATRIX: PLATFORM TRANSFORMATION
═══════════════════════════════════════════════════════════

                        DEPENDS ON ──>
              │Foun│Cont│CICD│Sec│Obs│Port│Svc│Team│MVP
              │dat │Plat│Plat│   │   │    │Cat│On  │
──────────────┼────┼────┼────┼───┼───┼────┼───┼────┼────
Foundation    │ -  │    │    │   │   │    │   │    │
Container Plat│ ●  │ -  │    │   │   │    │   │    │
CI/CD Platform│ ●  │ ●  │ -  │   │   │    │   │    │
Security Base │ ●  │    │    │ - │   │    │   │    │
Observability │ ●  │ ●  │    │ ● │ - │    │   │    │
Portal        │ ●  │ ●  │ ●  │ ● │   │ -  │   │    │
Service Cat   │ ●  │ ●  │ ●  │ ● │   │ ●  │ - │    │
Team Onboard  │ ●  │ ●  │ ●  │ ● │ ● │ ●  │ ● │ -  │
MVP Complete  │ ●  │ ●  │ ●  │ ● │ ● │ ●  │ ● │ ●  │ -

● = Hard dependency (must complete before dependent item)
○ = Soft dependency (helpful but not blocking)
- = Not applicable (self)

Interpretation:
- Read rows left-to-right: "This item depends on..."
- Read columns top-to-bottom: "This item is depended on by..."
- Items with most ● in their column are critical (many dependents)
- Items with most ● in their row have most risk (many dependencies)

Critical Items (Most Dependents):
1. Foundation:      8 dependents (everything depends on this)
2. Container Platform: 6 dependents
3. Security Baseline:  6 dependents
```

### Critical Path Format
```
═══════════════════════════════════════════════════════════
CRITICAL PATH ANALYSIS
═══════════════════════════════════════════════════════════

Program Duration: 12 weeks (Jan 1 - Mar 31, 2026)
Critical Path Duration: 12 weeks (0 weeks float)
Completion Confidence: 70% (moderate risk)

───────────────────────────────────────────────────────────
CRITICAL PATH SEQUENCE
───────────────────────────────────────────────────────────

Week 0 ════════════════════════════════════> Week 12
│                                                      │
├─> [Foundation] ═════════════> [Container Platform]
    (2 weeks)                   (3 weeks)
    🟢 COMPLETE                 🟡 90% COMPLETE
                                Float: 0 weeks
                                                       │
                                ┌──────────────────────┘
                                │
                                ▼
                        [Service Catalog]
                        (2 weeks)
                        🟢 COMPLETE
                        Float: 0 weeks
                                │
                                ▼
                        [Observability]
                        (3 weeks)
                        🟡 60% COMPLETE  ⚠️ RISK
                        Float: 0 weeks
                                │
                                ▼
                        [Team Onboarding]
                        (2 weeks)
                        ⏳ NOT STARTED   🔴 BLOCKED
                        Float: 0 weeks
                                │
                                ▼
                        [MVP Complete]
                        (Week 12 target)

───────────────────────────────────────────────────────────
NON-CRITICAL PATH ITEMS (Have Float)
───────────────────────────────────────────────────────────

[CI/CD Platform]
Duration: 3 weeks
Float: 2 weeks (can slip without impacting MVP)
Status: 🟢 Complete (finished 2 weeks early)

[Developer Portal]
Duration: 2 weeks
Float: 1 week
Status: 🟢 Complete (on time)

[Security Baseline]
Duration: 3 weeks
Float: 1 week
Status: 🟢 Complete (on time)

───────────────────────────────────────────────────────────
CRITICAL PATH RISKS
───────────────────────────────────────────────────────────

🔴 HIGH RISK: Observability (Week 7-10)

Current Status: 60% complete, Week 8 of 12
Problem: Complex legacy app instrumentation taking longer than expected
Impact: If delayed 1 week, cascades to onboarding and MVP
Mitigation:
  - Dedicated engineer assigned (highest priority)
  - Datadog support engaged for legacy apps
  - Consider phased rollout (new apps first)

🔴 HIGH RISK: Team Onboarding (Week 10-12)

Current Status: Not started, blocked by observability + security reviews
Problem: Security review bottleneck (2 FTE for 50 teams)
Impact: Could extend MVP date by 2-3 weeks
Mitigation:
  - Automate security checks
  - Batch reviews (5 teams/week)
  - Fast-track security engineer hire

───────────────────────────────────────────────────────────
WHAT-IF SCENARIOS
───────────────────────────────────────────────────────────

Scenario 1: Observability Slips 1 Week
├─ Impact: MVP date moves from Mar 31 → Apr 7 (+1 week)
├─ Probability: 40%
└─ Mitigation: Allocate 1 additional engineer to observability

Scenario 2: Security Review Bottleneck Not Resolved
├─ Impact: MVP date moves from Mar 31 → Apr 21 (+3 weeks)
├─ Probability: 30%
└─ Mitigation: Automate security baseline + hire engineer

Scenario 3: Both Observability + Security Slip
├─ Impact: MVP date moves from Mar 31 → Apr 28 (+4 weeks)
├─ Probability: 15%
└─ Mitigation: Escalate to CTO, request additional resources

───────────────────────────────────────────────────────────
RECOMMENDATIONS
───────────────────────────────────────────────────────────

1. Add 1-Week Buffer to MVP Date
   Change target from March 31 → March 24 (internal buffer)
   Gives 1 week contingency for critical path slips

2. Daily Standups for Critical Path Items
   Observability and Team Onboarding teams sync daily
   Surface blockers immediately

3. Fast-Track Security Automation
   Highest priority to unblock team onboarding bottleneck
   Target: Automated checks live by March 15
```

### Timeline Format
```
═══════════════════════════════════════════════════════════
DEPENDENCY TIMELINE (GANTT VIEW)
═══════════════════════════════════════════════════════════

Week:   1    2    3    4    5    6    7    8    9   10   11   12
        │    │    │    │    │    │    │    │    │    │    │    │

Foundation
████████
🟢 COMPLETE

Container Platform
     ████████████████████
     🟡 90% COMPLETE (CRITICAL PATH)

CI/CD Platform
     ████████████████
     🟢 COMPLETE (2 weeks float)

Security Baseline
          ████████████████
          🟢 COMPLETE (1 week float)

Developer Portal
               ████████████
               🟢 COMPLETE (1 week float)

Service Catalog
                    ████████████
                    🟢 COMPLETE (CRITICAL PATH)

Observability
                         ████████████████
                         🟡 60% (CRITICAL PATH) ⚠️

Team Onboarding
                                     ████████████
                                     ⏳ BLOCKED 🔴

MVP Complete
                                                 ▼
                                                W12

Legend:
████ = Work completed
▒▒▒▒ = Work in progress
░░░░ = Work not started
═══  = Critical path
- -  = Float (slack time)
⚠️   = Risk/delay indicator
🔴   = Blocked
```

## Dependency Types

### Technical Dependencies
```
- Infrastructure prerequisites
- API/integration requirements
- Data dependencies
- Technology stack requirements
- Platform capabilities
```

### Process Dependencies
```
- Approval workflows
- Review cycles (security, architecture, legal)
- Compliance sign-offs
- Budget approvals
- Governance gates
```

### Resource Dependencies
```
- Team capacity constraints
- Shared resource contention
- Subject matter expert availability
- Budget allocation timing
- Equipment/infrastructure availability
```

### Knowledge Dependencies
```
- Training completion
- Documentation availability
- Expertise transfer
- Learning curves
- Best practice dissemination
```

### External Dependencies
```
- Vendor deliveries
- Third-party integrations
- Procurement cycles
- Partner coordination
- Regulatory approvals
```

## Examples

### Example 1: Network Graph View
```bash
/dependency-analysis --initiative "platform-transformation" --teams 50 --format network-graph
```

### Example 2: Dependency Matrix
```bash
/dependency-analysis --initiative "ci-cd-migration" --format matrix --verticals "cicd,containers"
```

### Example 3: Critical Path Focus
```bash
/dependency-analysis --initiative "platform-transformation" --format critical-path --time-horizon current-quarter
```

### Example 4: Timeline View
```bash
/dependency-analysis --initiative "platform-transformation" --format timeline --phase execution
```

### Example 5: Planning Phase
```bash
/dependency-analysis --initiative "platform-transformation" --phase planning --include-external true
```

## Integration with Agents

```bash
# Dependency analysis via Delivery Agent
@delivery-agent "Analyze dependencies for our platform transformation"

# Agent invokes:
/dependency-analysis --initiative "platform-transformation" --teams 50

# Can combine with risk assessment:
@risk-agent "What are the risks from these dependencies?"
```

## Best Practices

1. **Map Early**: Identify dependencies in planning phase
2. **Update Frequently**: Dependencies change as work progresses
3. **Visualize**: Use network graphs to communicate complexity
4. **Track Critical Path**: Monitor items with zero float closely
5. **Resolve Blockers Fast**: Blocked dependencies compound quickly
6. **Build Buffers**: Add slack time to critical path items

## Common Pitfalls

❌ **Hidden Dependencies**: Not identifying all dependencies upfront
❌ **No Critical Path**: Not knowing which dependencies are critical
❌ **Ignoring External**: Underestimating vendor/partner dependencies
❌ **Static Analysis**: Treating as one-time exercise
❌ **No Ownership**: Dependencies without clear owners don't get resolved

## Dependency Resolution Strategies

### Parallelize
```
Break dependencies to enable concurrent work
Example: Separate staging and production EKS clusters
```

### Stub/Mock
```
Create temporary placeholders to unblock dependent work
Example: Mock API while real API is being developed
```

### Escalate
```
Raise blocker to leadership for resolution
Example: CFO approval holding up vendor procurement
```

### Fast-Track
```
Prioritize critical path items over non-critical work
Example: Pull engineers from non-critical path to observability
```

### Automate
```
Remove manual dependency bottlenecks
Example: Automated security baseline checks vs manual reviews
```

## Related Skills
- `/create-roadmap` - Align dependencies to roadmap phases
- `/risk-assessment` - Identify dependency-related risks
- `/exec-briefing` - Communicate dependency blockers to executives

## Related Agents
- `@delivery-agent` - Comprehensive delivery and dependency management
- `@risk-agent` - Dependency risk analysis
- `@governance-agent` - Escalate blocked dependencies

## Implementation Notes

This skill uses:
- Critical Path Method (CPM) for analysis
- Network diagram techniques (PERT charts)
- Dependency Structure Matrix (DSM) methodology
- Program management best practices (PMI)

For complex dependency analysis, consider using project management tools (Jira, MS Project) to track dependencies dynamically.
