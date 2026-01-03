# Skill: Risk Assessment

## Description
Comprehensive platform program risk assessment with probability/impact scoring, mitigation strategies, and risk register.

## Usage
```bash
/risk-assessment --initiative "platform-transformation" --phase execution --format register
```

## Parameters

### Required
- `--initiative` (string): Initiative or program name

### Optional
- `--phase` (string): Program phase: "planning", "execution", "scaling", "steady-state" (default: "execution")
- `--format` (string): Output format: "register", "matrix", "dashboard", "heat-map" (default: "register")
- `--risk-appetite` (string): Organization risk appetite: "conservative", "moderate", "aggressive" (default: "moderate")
- `--include-mitigations` (boolean): Include detailed mitigation plans (default: true)
- `--include-contingency` (boolean): Include contingency plans for top risks (default: true)
- `--timeframe` (string): Risk assessment timeframe: "immediate", "6-months", "12-months" (default: "6-months")

## Output Formats

### Register Format
```
═══════════════════════════════════════════════════════════
RISK REGISTER: PLATFORM TRANSFORMATION
═══════════════════════════════════════════════════════════
Initiative: Platform Transformation Program
Phase: Execution (Q1-Q2 FY2026)
Assessment Date: January 15, 2026
Risk Appetite: Moderate
Timeframe: 6 months

───────────────────────────────────────────────────────────
RISK SUMMARY
───────────────────────────────────────────────────────────

Total Risks Identified: 18
├─ Critical (Prob × Impact ≥ 16):    3 risks  🔴
├─ High (Prob × Impact 12-15):       5 risks  🟠
├─ Medium (Prob × Impact 6-11):      7 risks  🟡
└─ Low (Prob × Impact ≤ 5):          3 risks  🟢

Top Risk: Budget Overrun (Score: 20)
Risk Exposure: $1.2M (sum of financial impacts × probability)

───────────────────────────────────────────────────────────
CRITICAL RISKS (SCORE ≥ 16)
───────────────────────────────────────────────────────────

RISK #1: Budget Overrun - Cloud Infrastructure Costs
───────────────────────────────────────────────────────────
Risk ID: R-001
Category: Financial
Owner: Platform Program Manager
Status: ACTIVE

Probability: VERY HIGH (80%)  │  Impact: VERY HIGH (5/5)
Risk Score: 20 (4 × 5)        │  Priority: 🔴 CRITICAL

Description:
Cloud infrastructure costs (AWS EKS, compute, storage) may exceed
budget by 30-50% due to:
- Underestimated container resource requirements
- Higher-than-expected data transfer costs
- Inefficient resource allocation in early phases
- Lack of FinOps optimization

Potential Impact:
- Budget overrun: $400K-$600K over FY2026
- CFO loss of confidence in program
- Potential budget cuts or program slowdown
- Delayed Phase 2 capabilities

Mitigation Strategy:
✓ Implement resource quotas and limits (namespace-level)
✓ Enable AWS Cost Explorer alerts (weekly reviews)
✓ Right-size instances using Kubernetes VPA recommendations
✓ Implement pod autoscaling (HPA) to reduce idle capacity
✓ Schedule non-prod environments to shut down nights/weekends
✓ Negotiate AWS EDP (Enterprise Discount Program) - Target: 15% discount

Contingency Plan (if risk materializes):
1. Immediate freeze on new team onboarding (preserve budget)
2. Emergency FinOps audit and optimization sprint
3. Request contingency budget release (+$200K)
4. Negotiate with AWS for retroactive discounts
5. Communicate revised forecast to CFO with recovery plan

Risk Reduction Target: Reduce probability to 40% by March 31
Current Status: In progress - FinOps tools being deployed

───────────────────────────────────────────────────────────

RISK #2: Key Personnel Loss - Platform Team Attrition
───────────────────────────────────────────────────────────
Risk ID: R-002
Category: People
Owner: VP Engineering
Status: ACTIVE

Probability: MEDIUM (40%)     │  Impact: VERY HIGH (5/5)
Risk Score: 16 (4 × 4)        │  Priority: 🔴 CRITICAL

Description:
Loss of 1-2 senior platform engineers due to:
- Competitive job market for Kubernetes/platform expertise
- Burnout from aggressive delivery schedule
- Compensation not competitive with FAANG
- Limited career growth visibility

Potential Impact:
- 2-3 month knowledge transfer and backfill delay
- Project schedule slip by 4-6 weeks
- Team morale impact
- Increased load on remaining team members
- Risk of cascading attrition

Mitigation Strategy:
✓ Retention bonuses for key platform engineers (cliff: 12 months)
✓ Bi-weekly 1:1s to monitor morale and address concerns
✓ Career development plans with clear growth path
✓ Workload balancing to prevent burnout
✓ Competitive compensation review (February)
✓ Recognition and visibility (exec demos, conference talks)

Contingency Plan:
1. Pre-identified backfill candidates (warm pipeline)
2. Cross-training to reduce single points of failure
3. Engage premium recruiters (budget: $50K)
4. Contractor bridge capacity if needed

Risk Reduction Target: Reduce probability to 20% by April
Current Status: Retention packages approved, being communicated

───────────────────────────────────────────────────────────

RISK #3: Security Vulnerability - Platform Breach
───────────────────────────────────────────────────────────
Risk ID: R-003
Category: Security
Owner: CISO
Status: ACTIVE

Probability: LOW (20%)        │  Impact: CATASTROPHIC (5/5)
Risk Score: 16 (4 × 4)        │  Priority: 🔴 CRITICAL

Description:
Security breach in platform infrastructure exposing:
- Customer data via compromised containers
- Secrets leaked from Vault misconfiguration
- Supply chain attack via container images
- Kubernetes API access compromise

Potential Impact:
- Customer data breach (GDPR, compliance violations)
- Reputational damage
- Regulatory fines: $500K-$2M
- Customer churn
- Board/executive confidence loss

Mitigation Strategy:
✓ Weekly security scans (Trivy, Snyk) with zero-critical policy
✓ Penetration testing (Q1, Q3) by external firm
✓ Vault audit logging and access reviews (monthly)
✓ Image signing and admission control (only trusted registries)
✓ Network policies (zero-trust, least privilege)
✓ SOC 2 Type II audit (scheduled June 2026)
✓ Incident response plan and runbooks

Contingency Plan:
1. Incident response team on-call 24/7
2. Cyber insurance policy ($5M coverage)
3. Pre-negotiated IR firm retainer (CrowdStrike)
4. Communication plan (legal, PR, customer notifications)

Risk Reduction Target: Maintain probability ≤20%
Current Status: Security baseline met, pen test scheduled

───────────────────────────────────────────────────────────
HIGH RISKS (SCORE 12-15)
───────────────────────────────────────────────────────────

RISK #4: Organizational Resistance - Low Adoption
───────────────────────────────────────────────────────────
Risk Score: 15 (Probability: 60%, Impact: 4/5)

Description: Development teams resist migrating to new platform,
preferring existing Jenkins/EC2 workflows. Adoption falls below
50% target, undermining ROI.

Mitigation:
- Voluntary opt-in approach (no forced migration)
- "Concierge" migration support for each team
- Showcase early wins and productivity gains
- Executive mandate for new projects (greenfield only)

───────────────────────────────────────────────────────────

RISK #5: Vendor Lock-In - GitHub Dependency
───────────────────────────────────────────────────────────
Risk Score: 12 (Probability: 60%, Impact: 3/5)

Description: Heavy dependency on GitHub (Actions, repos, security)
creates lock-in and pricing risk.

Mitigation:
- Multi-year contract negotiation (lock pricing)
- Abstract CI/CD logic (portable to GitLab if needed)
- Maintain export/migration capability

───────────────────────────────────────────────────────────

RISK #6: Skills Gap - Kubernetes Expertise
───────────────────────────────────────────────────────────
Risk Score: 12 (Probability: 50%, Impact: 4/5)

Description: Platform team lacks deep Kubernetes expertise,
leading to production incidents and slow feature delivery.

Mitigation:
- Hired Kubernetes expert (Feb 1 start)
- Team training program (80% complete)
- AWS EKS support contract
- Leverage managed services (reduce operational burden)

───────────────────────────────────────────────────────────

[... continues for all 18 risks ...]

───────────────────────────────────────────────────────────
RISK TRENDS
───────────────────────────────────────────────────────────

Since Last Assessment (Dec 2025):

Risks Increased:
↑ Budget Overrun (was 12, now 20) - Cloud cost estimates too low
↑ Vendor Lock-In (new risk, score 12)

Risks Decreased:
↓ Skills Gap (was 16, now 12) - Kubernetes expert hired
↓ Schedule Delay (was 15, now 9) - Ahead of schedule

Risks Closed:
✓ GitHub Enterprise License (approved, funded)
✓ CISO Security Approval (granted with conditions)
```

### Matrix Format
```
═══════════════════════════════════════════════════════════
RISK PROBABILITY × IMPACT MATRIX
═══════════════════════════════════════════════════════════

Impact
  ↑
  │
  5│                    │           │ R-001 (Budget)    │
CA │                    │           │ R-002 (Attrition) │
TA │                    │           │ R-003 (Security)  │
ST │────────────────────┼───────────┼───────────────────│
RO │                    │           │                   │
PH │                    │ R-006     │ R-004 (Adoption)  │
IC │                    │ (Skills)  │                   │
  4│────────────────────┼───────────┼───────────────────│
  │                    │           │                   │
  │         R-009      │ R-007     │ R-005             │
HI │        (Timeline)  │ (Scope)   │ (Vendor Lock-In)  │
GH│────────────────────┼───────────┼───────────────────│
  3│                    │           │                   │
  │         R-010      │ R-011     │ R-008             │
ME │        (Quality)   │ (Tech     │ (Compliance)      │
DI │                    │  Debt)    │                   │
UM│────────────────────┼───────────┼───────────────────│
  2│                    │           │                   │
  │         R-015      │ R-012     │                   │
LO │        (Docs)      │ (Support) │                   │
W │                    │           │                   │
  1│────────────────────┴───────────┴───────────────────│
  └────────────────────────────────────────────────────→
       LOW (20%)    MEDIUM (40%)   HIGH (60%)  V.HIGH (80%)
                        PROBABILITY

Legend:
  Critical (≥16): Address immediately
  High (12-15): Monitor closely, active mitigation
  Medium (6-11): Monitor, contingency plans
  Low (≤5): Accept or minimal mitigation
```

### Dashboard Format
```
═══════════════════════════════════════════════════════════
RISK DASHBOARD: PLATFORM TRANSFORMATION
═══════════════════════════════════════════════════════════

Overall Risk Status: 🟡 ELEVATED (3 Critical Risks)

Risk Exposure: $1.2M (potential financial impact)
Top Risk: Budget Overrun (Score: 20)

───────────────────────────────────────────────────────────
RISK DISTRIBUTION
───────────────────────────────────────────────────────────

By Severity:
🔴 Critical (≥16):   3 risks  (17%)  ████████████
🟠 High (12-15):     5 risks  (28%)  ████████████████████████
🟡 Medium (6-11):    7 risks  (39%)  ████████████████████████████████
🟢 Low (≤5):         3 risks  (17%)  ████████████

By Category:
Financial:    4 risks  (22%)
People:       3 risks  (17%)
Technical:    5 risks  (28%)
Security:     2 risks  (11%)
Organizational: 4 risks (22%)

───────────────────────────────────────────────────────────
TOP 5 RISKS (ACTIVE MITIGATION)
───────────────────────────────────────────────────────────

1. Budget Overrun              Score: 20  🔴  Owner: PMO
   Status: FinOps tools deploying, AWS discount negotiation in progress

2. Key Personnel Attrition     Score: 16  🔴  Owner: VP Eng
   Status: Retention packages approved, morale monitoring weekly

3. Security Vulnerability      Score: 16  🔴  Owner: CISO
   Status: Pen test scheduled Q1, security baseline complete

4. Low Adoption Resistance     Score: 15  🟠  Owner: PMO
   Status: Pilot teams showing success, concierge support deployed

5. Vendor Lock-In (GitHub)     Score: 12  🟠  Owner: Architect
   Status: Multi-year contract in negotiation

───────────────────────────────────────────────────────────
RISK VELOCITY (TREND)
───────────────────────────────────────────────────────────

Risks Increasing (Last 30 Days):
↑ Budget Overrun (Δ+8 points) - Cloud costs higher than expected
↑ Vendor Lock-In (New risk)

Risks Decreasing:
↓ Skills Gap (Δ-4 points) - Expert hired
↓ Schedule Delay (Δ-6 points) - Ahead of plan

───────────────────────────────────────────────────────────
MITIGATION PROGRESS
───────────────────────────────────────────────────────────

On Track:         12 risks  (67%)  ████████████████████████
Behind Schedule:   4 risks  (22%)  ████████████
Blocked:           2 risks  (11%)  ██████

───────────────────────────────────────────────────────────
NEXT REVIEW: February 15, 2026 (Monthly Cadence)
───────────────────────────────────────────────────────────
```

### Heat Map Format
```
═══════════════════════════════════════════════════════════
RISK HEAT MAP
═══════════════════════════════════════════════════════════

                    LIKELIHOOD
                LOW    MEDIUM    HIGH    VERY HIGH
              ┌──────┬──────┬──────┬──────┐
    CATASTRO- │      │      │      │ ████ │ R-001, R-002
      PHIC  5 │      │      │      │ ████ │ R-003
              ├──────┼──────┼──────┼──────┤
I    MAJOR  4 │      │ ██   │ ████ │      │ R-004, R-006
M             │      │ ██   │ ████ │      │
P             ├──────┼──────┼──────┼──────┤
A  MODERATE 3 │      │ ██   │ ████ │ ██   │ R-005, R-007
C             │      │ ██   │ ████ │ ██   │ R-008
T             ├──────┼──────┼──────┼──────┤
    MINOR   2 │      │ ██   │      │      │ R-012
              │      │ ██   │      │      │
              ├──────┼──────┼──────┼──────┤
  NEGLIGIBLE 1│      │      │      │      │
              └──────┴──────┴──────┴──────┘

Color Key:
████ = 3+ risks (High concentration, critical focus area)
██   = 1-2 risks (Monitor)
     = 0 risks (Low risk zone)

Heat Map Insight:
Critical risk concentration in HIGH likelihood × CATASTROPHIC impact
quadrant. Immediate attention required on Budget, Attrition, Security.
```

## Risk Categories

### Financial Risks
```
- Budget overruns (CAPEX/OPEX)
- ROI not achieved
- Vendor pricing increases
- Hidden costs (migration, training)
- Opportunity cost
```

### People Risks
```
- Key personnel attrition
- Skills gap
- Team burnout
- Change resistance
- Insufficient staffing
```

### Technical Risks
```
- Technology selection mistakes
- Technical debt accumulation
- Integration failures
- Performance issues
- Scalability limits
```

### Security Risks
```
- Security breaches
- Compliance violations
- Supply chain attacks
- Data leaks
- Insider threats
```

### Organizational Risks
```
- Executive support loss
- Low adoption
- Organizational silos
- Competing priorities
- Culture clash
```

### External Risks
```
- Vendor acquisition/discontinuation
- Regulatory changes
- Economic downturn
- Competitive pressure
- Market shifts
```

## Probability Scale

```
Very High (80-100%):  Will almost certainly occur
High (60-79%):        Likely to occur
Medium (40-59%):      May occur
Low (20-39%):         Unlikely to occur
Very Low (0-19%):     Rare, but possible
```

## Impact Scale

```
5 - Catastrophic:  Program failure, >$1M loss, data breach
4 - Major:         >3 month delay, $500K-$1M loss, major customer impact
3 - Moderate:      1-3 month delay, $100K-$500K loss, team morale hit
2 - Minor:         <1 month delay, $10K-$100K loss, temporary disruption
1 - Negligible:    No schedule impact, <$10K loss, minimal disruption
```

## Risk Scoring

```
Risk Score = Probability (1-5) × Impact (1-5)

Critical:  16-25  (Immediate action required)
High:      12-15  (Active mitigation, close monitoring)
Medium:    6-11   (Monitor, contingency plans)
Low:       1-5    (Accept or minimal mitigation)
```

## Examples

### Example 1: Standard Risk Register
```bash
/risk-assessment --initiative "platform-transformation" --phase execution --format register
```

### Example 2: Visual Risk Matrix
```bash
/risk-assessment --initiative "platform-transformation" --format matrix --include-mitigations true
```

### Example 3: Executive Dashboard
```bash
/risk-assessment --initiative "ci-cd-migration" --format dashboard --timeframe immediate
```

### Example 4: Planning Phase Risks
```bash
/risk-assessment --initiative "platform-transformation" --phase planning --risk-appetite conservative
```

### Example 5: Heat Map View
```bash
/risk-assessment --initiative "platform-transformation" --format heat-map
```

## Integration with Agents

```bash
# Risk assessment via Risk Agent
@risk-agent "Assess risks for our platform transformation"

# Agent invokes:
/risk-assessment --initiative "platform-transformation" --phase execution

# Can combine with other skills:
@financial-agent "Calculate financial impact of top 3 risks"
```

## Best Practices

1. **Regular Updates**: Update risk register monthly minimum
2. **Risk Ownership**: Assign owner for each risk (accountability)
3. **Quantify Impact**: Use dollar amounts, time delays, specific metrics
4. **Mitigation Plans**: Every critical/high risk needs active mitigation
5. **Track Trends**: Monitor risk velocity (increasing/decreasing)
6. **Escalate Early**: Communicate critical risks to executives immediately

## Common Pitfalls

❌ **Static Risk Register**: Treating as one-time exercise
❌ **No Risk Owners**: Risks without accountability go unmanaged
❌ **Vague Descriptions**: "Things might go wrong" isn't actionable
❌ **Ignoring Low Probability/High Impact**: Black swan events matter
❌ **No Contingency Plans**: Mitigation fails sometimes, have Plan B

## Risk Mitigation Strategies

### Avoid
```
Eliminate the risk by not doing the activity
Example: Don't support legacy OS versions (avoid compatibility risk)
```

### Reduce
```
Lower probability or impact through controls
Example: Implement resource quotas (reduce budget overrun probability)
```

### Transfer
```
Shift risk to third party
Example: Cyber insurance policy (transfer security breach financial impact)
```

### Accept
```
Acknowledge risk, no active mitigation
Example: Accept vendor lock-in risk with GitHub (strategic choice)
```

## Related Skills
- `/budget-forecast` - Quantify financial risk impacts
- `/stakeholder-map` - Identify stakeholder-related risks
- `/exec-briefing` - Communicate risks to executives
- `/dependency-analysis` - Identify dependency-related risks

## Related Agents
- `@risk-agent` - Comprehensive risk analysis
- `@financial-agent` - Financial risk quantification
- `@governance-agent` - Risk governance and escalation

## Implementation Notes

This skill uses:
- PMI risk management framework (PMBOK)
- Probability × Impact matrix methodology
- Industry risk benchmarks for platform transformations
- Risk register best practices

For organization-specific risk assessments, provide context on organizational risk appetite, past incidents, and industry-specific risks (e.g., FinTech regulatory risks).
