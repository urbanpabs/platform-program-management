# Dependency Tracker

**Program**: [Program Name]
**Created By**: [Name, Title]
**Date**: [Date]
**Program Phase**: [Planning | Execution | Scaling]
**Reporting Period**: [e.g., Q1 FY2026, January 2026]
**Last Updated**: [Date]

---

## Dependency Summary

**Total Dependencies Identified**: [#]
- **Hard Dependencies** (Blocking): [#]
- **Soft Dependencies** (Capacity constraints): [#]
- **External Dependencies** (Vendor/third-party): [#]

**Dependency Status**:
- ✅ **Resolved** (Complete): [#] ([%]%)
- ⏳ **In Progress**: [#] ([%]%)
- 🔴 **Blocked**: [#] ([%]%)
- ⏸️ **Not Started**: [#] ([%]%)

**Critical Blockers**: [#] dependencies blocking critical path

---

## Critical Path Dependencies

### Critical Path Overview

**Total Program Duration**: [#] weeks
**Critical Path Duration**: [#] weeks
**Critical Path Float**: [#] weeks ([Low | Medium | High] buffer)
**Completion Confidence**: [%]% ([Low | Medium | High])

**Critical Path Sequence**:
```
[Item 1] → [Item 2] → [Item 3] → [Item 4] → [Goal]
 (Weeks)   (Weeks)   (Weeks)   (Weeks)
```

**Critical Path Items** (Zero or Low Float):
- [Item 1]: [Status, Float]
- [Item 2]: [Status, Float]
- [Item 3]: [Status, Float]

**Risk**: Any delay in critical path items directly impacts program completion date.

---

## Dependency Register

### Dependency #1: [Dependency Name]

**Dependency ID**: DEP-001
**Type**: 🔴 Technical | Process | Resource | Knowledge | External
**Criticality**: 🔴 Critical Path | 🟡 High | 🟢 Medium | ⬜ Low
**Status**: ✅ Resolved | ⏳ In Progress | 🔴 Blocked | ⏸️ Not Started
**Last Updated**: [Date]

**Dependent Item**: [What is waiting/blocked]
**Depends On**: [What it needs to complete first]

**Description**:
[2-3 sentences explaining the dependency relationship. What can't start until what completes?]

**Dependency Relationship**:
- **Blocker**: [Item A] (must complete)
- **Blocked**: [Item B] (waiting to start)
- **Type**: Hard (cannot proceed) | Soft (can proceed but suboptimal)

**Impact if Not Resolved**:
- **Schedule**: [e.g., 2-week delay to MVP]
- **Budget**: [e.g., $50K contractor costs if delayed]
- **Quality**: [e.g., Reduced testing coverage]
- **Risk**: [e.g., Deployment failures increase]

**Owner**:
- **Blocking Item Owner**: [Name, responsible for completing the blocker]
- **Blocked Item Owner**: [Name, waiting for resolution]
- **Dependency Coordinator**: [Name, tracking and escalating]

**Timeline**:
- **Blocker Start Date**: [Date]
- **Blocker Target Completion**: [Date]
- **Blocker Actual Completion**: [Date]
- **Blocked Item Can Start**: [Date]
- **Float**: [#] days

**Resolution Plan**:
- [ ] [Action 1 - ETA: [Date], Owner: [Name]]
- [ ] [Action 2 - ETA: [Date], Owner: [Name]]
- [ ] [Action 3 - ETA: [Date], Owner: [Name]]

**Resolution Status**: 🟢 On Track | 🟡 At Risk | 🔴 Behind Schedule

**Workarounds** (if blocker delays):
- [Workaround 1 - e.g., Use mock API while real API is built]
- [Workaround 2 - e.g., Proceed with reduced scope]

**Escalation**:
- **Escalated**: [Yes | No]
- **Escalation Date**: [Date]
- **Escalated To**: [Name, Title]
- **Resolution**: [Summary]

**Next Review**: [Date]

---

### Dependency #2: [Dependency Name]

**Dependency ID**: DEP-002
**Type**: Process
**Criticality**: 🟡 High
**Status**: 🔴 Blocked

[Similar structure as Dependency #1]

---

## Dependency Matrix

### Cross-Team Dependency Matrix

```
              │Foun│Cont│CICD│Sec │Obs │Port│Team│MVP
              │dat │Plat│Plat│Base│    │    │On  │
──────────────┼────┼────┼────┼────┼────┼────┼────┼────
Foundation    │ -  │    │    │    │    │    │    │
Container Plat│ ●  │ -  │    │    │    │    │    │
CI/CD Platform│ ●  │ ●  │ -  │    │    │    │    │
Security Base │ ●  │    │    │ -  │    │    │    │
Observability │ ●  │ ●  │    │ ●  │ -  │    │    │
Portal        │ ●  │ ●  │ ●  │ ●  │    │ -  │    │
Team Onboard  │ ●  │ ●  │ ●  │ ●  │ ●  │ ●  │ -  │
MVP Complete  │ ●  │ ●  │ ●  │ ●  │ ●  │ ●  │ ●  │ -

● = Hard dependency (must complete before dependent item)
○ = Soft dependency (helpful but not blocking)
- = Not applicable (self)
```

**Reading the Matrix**:
- **Rows** depend on **columns** with ● marks
- Example: "Team Onboard" depends on Container Platform, CI/CD Platform, Security Baseline, Observability, and Portal

**Critical Items** (Most Dependents):
1. **Foundation**: [#] items depend on this
2. **Container Platform**: [#] items depend on this
3. **Security Baseline**: [#] items depend on this

---

## Dependency Categories

### Technical Dependencies ([#] total)

| ID | Blocker | Blocked Item | Owner | Status | Due Date | Float |
|----|---------|-------------|-------|--------|----------|-------|
| DEP-001 | [Blocker] | [Blocked] | [Name] | ⏳ | [Date] | [#] days |
| DEP-002 | [Blocker] | [Blocked] | [Name] | ✅ | [Date] | - |
| DEP-XXX | [Blocker] | [Blocked] | [Name] | 🔴 | [Date] | 0 days |

**Critical Technical Dependencies**:
- [Dependency 1]: [Status and impact]
- [Dependency 2]: [Status and impact]

---

### Process Dependencies ([#] total)

| ID | Process/Approval | Waiting Item | Approver | Status | Due Date |
|----|------------------|-------------|----------|--------|----------|
| DEP-XXX | [Process] | [Blocked] | [Name] | ⏳ | [Date] |
| DEP-XXX | [Process] | [Blocked] | [Name] | 🔴 | [Date] |

**Examples**:
- Security reviews required for production deployments
- CFO budget approval for vendor procurement
- Architecture review board sign-off

---

### Resource Dependencies ([#] total)

| ID | Resource Constraint | Impacted Work | Owner | Status | Mitigation |
|----|---------------------|--------------|-------|--------|-----------|
| DEP-XXX | [Constraint] | [Work] | [Name] | ⏳ | [Plan] |

**Examples**:
- Platform team bandwidth (6 FTE across multiple verticals)
- Security team review capacity (bottleneck)
- Shared subject matter experts

---

### Knowledge Dependencies ([#] total)

| ID | Knowledge/Training | Gated Work | Status | Completion Date |
|----|-------------------|-----------|--------|-----------------|
| DEP-XXX | [Training] | [Work] | ⏳ | [Date] |

**Examples**:
- Kubernetes training required before production deployment
- Developer documentation needed before self-service onboarding
- Security training before handling PII data

---

### External Dependencies ([#] total)

| ID | External Party | Deliverable | Contact | Status | SLA | Actual |
|----|---------------|------------|---------|--------|-----|--------|
| DEP-XXX | [Vendor] | [Deliverable] | [Contact] | ⏳ | [Days] | [Days] |

**Examples**:
- AWS EKS cluster provisioning (5 business day SLA)
- GitHub Enterprise license activation (2 week SLA)
- Datadog account setup (1 week SLA)

---

## Blocked Dependencies (Immediate Attention Required)

### 🔴 Blocker #1: [Blocker Name]

**Dependency ID**: [DEP-XXX]
**Blocked Items**: [List of items waiting]
**Impact**: [#] teams waiting, [#] weeks delay potential
**Owner**: [Name]
**Status**: 🔴 **BLOCKED** - [#] days overdue

**Root Cause**:
[Why is this blocked? What's preventing resolution?]

**Unblock Plan**:
- [ ] [Action 1 - Owner: [Name], ETA: [Date]]
- [ ] [Action 2 - Owner: [Name], ETA: [Date]]
- [ ] [Action 3 - Owner: [Name], ETA: [Date]]

**Escalation**:
- Escalated to: [Name, Title] on [Date]
- Decision needed: [What decision is required to unblock?]

**Target Resolution**: [Date]

---

### 🔴 Blocker #2: [Blocker Name]

[Similar structure]

---

## Dependency Network Graph

```
[Simplified ASCII representation of dependency network]

                    [Platform Foundation]
                            │
                ┌───────────┼───────────┐
                │           │           │
                ▼           ▼           ▼
        [Container      [CI/CD       [Security
         Platform]      Platform]     Baseline]
                │           │           │
                └───────────┼───────────┘
                            ▼
                    [Service Catalog]
                            │
                            ▼
                    [Team Onboarding]
                            │
                            ▼
                    [MVP Complete]

Legend:
→ = "Depends on" relationship
Bold = Critical path
```

---

## Dependency Timeline (Gantt View)

```
Week:   1    2    3    4    5    6    7    8    9   10   11   12
        │    │    │    │    │    │    │    │    │    │    │    │

Foundation
████████
✅ COMPLETE

Container Platform (depends on Foundation)
     ████████████████████
     ⏳ IN PROGRESS (CRITICAL PATH)

CI/CD Platform (depends on Container Platform)
     ████████████████
     ⏳ IN PROGRESS

Security Baseline (depends on Foundation)
          ████████████████
          ✅ COMPLETE

Team Onboarding (depends on Container, CI/CD, Security, Observability)
                                     ████████████
                                     🔴 BLOCKED

MVP Complete (depends on Team Onboarding)
                                                 ▼
                                                W12

Legend:
████ = Completed work
▒▒▒▒ = In progress
░░░░ = Not started
🔴 = Blocked
```

---

## Dependency Resolution Progress

### Overall Progress

| Metric | Count | % |
|--------|-------|---|
| Total Dependencies | [#] | 100% |
| Resolved | [#] | [%]% |
| In Progress | [#] | [%]% |
| Blocked | [#] | [%]% |
| Not Started | [#] | [%]% |

**Progress Trend**: ↑ Improving | → Stable | ↓ Declining

---

### Dependency Burn-Down Chart

```
Dependencies
Remaining
    │
 20 │●
    │  ●
 15 │    ●
    │      ●
 10 │        ○─── Target
    │          ●
  5 │            ●─── Actual
    │              ●
  0 └──────────────────────────────→
      W1  W2  W3  W4  W5  W6  W7  W8
```

**Status**: ✅ Ahead | → On Track | ⚠️ Behind

---

## Bottlenecks

### Identified Bottlenecks

#### Bottleneck #1: [Bottleneck Name]

**Location**: [Where in the program this bottleneck occurs]
**Type**: [Resource | Process | Technical | Knowledge]
**Impact**: [#] dependencies affected, [#] teams blocked

**Root Cause**:
[Why is this a bottleneck? What's the constraint?]

**Affected Dependencies**:
- DEP-XXX: [Dependency name]
- DEP-XXX: [Dependency name]
- DEP-XXX: [Dependency name]

**Resolution Strategy**:
- [ ] [Strategy 1 - e.g., Automate manual process]
- [ ] [Strategy 2 - e.g., Add capacity (hire)]
- [ ] [Strategy 3 - e.g., Parallelize work]

**Owner**: [Name]
**Target Resolution**: [Date]
**Risk if Unresolved**: [Impact on program]

---

### Bottleneck Impact Analysis

| Bottleneck | Dependencies Affected | Schedule Impact | Resolution ETA |
|-----------|----------------------|-----------------|----------------|
| [Bottleneck 1] | [#] | [#] weeks | [Date] |
| [Bottleneck 2] | [#] | [#] weeks | [Date] |

---

## Dependency Management Strategies

### Strategies in Use

#### Parallelize
**Definition**: Break dependencies to enable concurrent work

**Applied To**:
- [Dependency ID]: [How we parallelized - e.g., Separate staging and production environments]

---

#### Stub/Mock
**Definition**: Create temporary placeholders to unblock dependent work

**Applied To**:
- [Dependency ID]: [Mock created - e.g., Mock API while real API is being developed]

---

#### Fast-Track
**Definition**: Prioritize critical path items over non-critical work

**Applied To**:
- [Dependency ID]: [Resource reallocation - e.g., Pulled engineers from non-critical work to observability]

---

#### Escalate
**Definition**: Raise blocker to leadership for resolution

**Applied To**:
- [Dependency ID]: [Escalation outcome - e.g., CFO expedited vendor approval]

---

## Dependency Tracking & Reviews

### Review Cadence

- **Critical Path Dependencies**: Daily standup
- **Blocked Dependencies**: Daily review until unblocked
- **High Priority Dependencies**: Bi-weekly review
- **All Dependencies**: Monthly comprehensive review

---

### Upcoming Dependency Milestones

| Milestone | Date | Dependencies Resolved | Status |
|-----------|------|----------------------|--------|
| [Milestone 1] | [Date] | [#]/[#] | 🟢 |
| [Milestone 2] | [Date] | [#]/[#] | 🟡 |
| [Milestone 3] | [Date] | [#]/[#] | ⏸️ |

---

## Action Items

### Due This Week

| Action | Dependency ID | Owner | Due Date | Status |
|--------|--------------|-------|----------|--------|
| [Action] | DEP-XXX | [Name] | [Date] | ⏳ |
| [Action] | DEP-XXX | [Name] | [Date] | ⏳ |

---

### Due This Month

| Action | Dependency ID | Owner | Due Date | Status |
|--------|--------------|-------|----------|--------|
| [Action] | DEP-XXX | [Name] | [Date] | [ ] |
| [Action] | DEP-XXX | [Name] | [Date] | [ ] |

---

## Escalations

### Active Escalations

| Dependency ID | Issue | Escalated To | Date | Status | Resolution |
|--------------|-------|-------------|------|--------|------------|
| DEP-XXX | [Issue] | [Name] | [Date] | ⏳ | [Update] |

---

## Recommendations

### Short-Term (This Week)

1. **[Recommendation 1]**
   - Action: [What to do]
   - Owner: [Who]
   - Impact: [Expected outcome]

2. **[Recommendation 2]**
   - Action: [What to do]
   - Owner: [Who]
   - Impact: [Expected outcome]

---

### Medium-Term (This Month)

1. **[Recommendation 1]**
   - Rationale: [Why this is needed]
   - Action: [What to do]
   - Expected Benefit: [Outcome]

---

## Change Log

| Date | Change | Dependency ID | Impact | Updated By |
|------|--------|--------------|--------|------------|
| [Date] | [Change] | DEP-XXX | [Impact] | [Name] |
| [Date] | [Change] | DEP-XXX | [Impact] | [Name] |

---

## Appendices

### Appendix A: Dependency Mapping Workshop
[List of participants and date of dependency identification workshop]

### Appendix B: Detailed Dependency Network Diagram
[Link to visual dependency diagram - Miro, Lucidchart, etc.]

### Appendix C: Integration with Project Schedule
[Link to Gantt chart or project management tool]

---

## Next Review

**Review Frequency**: [Daily | Weekly | Monthly]
**Next Review Date**: [Date]
**Review Owner**: [Program Manager / Delivery Manager]

---

**Document Owner**: [Program Manager / Delivery Manager]
**Last Updated**: [Date]
**Version**: [1.0]
