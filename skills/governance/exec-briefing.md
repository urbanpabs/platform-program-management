# Skill: Executive Briefing

## Description
Generate executive-level briefing document with status summary, key metrics, decisions needed, and risks.

## Usage
```bash
/exec-briefing --initiative "platform-transformation" --period Q1-FY2026 --audience CTO --format dashboard
```

## Parameters

### Required
- `--initiative` (string): Initiative or program name
- `--period` (string): Reporting period (e.g., "Q1-FY2026", "January-2026", "Week-of-Jan-15")

### Optional
- `--audience` (string): Primary audience: "CTO", "CFO", "Board", "Executive-Team", "All-Hands" (default: "CTO")
- `--format` (string): Output format: "dashboard", "narrative", "slides", "memo" (default: "dashboard")
- `--status` (string): Overall program status: "green", "yellow", "red" (auto-detected if not specified)
- `--include-metrics` (boolean): Include detailed metrics (default: true)
- `--include-risks` (boolean): Include risk section (default: true)
- `--include-decisions` (boolean): Highlight decisions needed (default: true)
- `--tone` (string): Communication tone: "confident", "balanced", "cautious" (default: "balanced")

## Output Formats

### Dashboard Format
```
═══════════════════════════════════════════════════════════
EXECUTIVE BRIEFING: PLATFORM TRANSFORMATION
═══════════════════════════════════════════════════════════
Period: Q1 FY2026 (Jan-Mar 2026)
Audience: CTO
Date: March 31, 2026
Status: 🟢 ON TRACK

───────────────────────────────────────────────────────────
EXECUTIVE SUMMARY
───────────────────────────────────────────────────────────

The Platform Transformation program delivered a successful Q1
with MVP foundation 85% complete and pilot team onboarding
ahead of schedule. Budget is on target, and early productivity
metrics show 25% deployment time reduction. CFO concerns around
ROI have been addressed with tangible pilot results.

Key Wins: ✓ Developer Portal launched  ✓ 15 teams onboarded
          ✓ CI/CD standardized       ✓ Security baseline met

───────────────────────────────────────────────────────────
STATUS AT A GLANCE (RAG)
───────────────────────────────────────────────────────────

Overall Program:        🟢 GREEN   (On track)
├─ Schedule:            🟢 GREEN   (2 weeks ahead)
├─ Budget:              🟢 GREEN   (3% under)
├─ Scope:               🟢 GREEN   (All Q1 features delivered)
├─ Quality:             🟢 GREEN   (Zero P0 defects)
├─ Stakeholder Sentiment: 🟡 YELLOW  (CFO skepticism improving)
└─ Team Morale:         🟢 GREEN   (Platform team engaged)

───────────────────────────────────────────────────────────
KEY METRICS
───────────────────────────────────────────────────────────

Adoption & Usage:
├─ Teams Onboarded:             15 / 50 (30% of MVP target)
├─ Active Developers:           60 / 200 (30%)
├─ Services Deployed:           42 services on new platform
└─ Self-Service Provisions:     120 (vs 0 baseline)

Productivity (Early Indicators):
├─ Deployment Frequency:        3.2x increase (was 2/week → 6.4/week)
├─ Deployment Lead Time:        -25% (was 4 hours → 3 hours)
├─ Failed Deployment Rate:      -40% (was 10% → 6%)
└─ Time to First Deployment:    -85% (was 2 days → 2 hours)

Platform Performance:
├─ Platform Uptime:             99.8% (target: 99.5%)
├─ Developer Portal Uptime:     99.9%
├─ API Response Time (p95):     120ms (target: <200ms)
└─ Support Response Time:       15 min avg (target: <30 min)

Developer Satisfaction:
├─ Developer NPS:               +35 (target: +30 by year-end)
├─ Platform Team NPS:           +65
├─ Support Satisfaction:        8.2/10
└─ Documentation Rating:        7.5/10

Financial:
├─ Q1 Spend:                    $1,625K (budget: $1,650K, -2%)
├─ CAPEX:                       $1,180K (on target)
├─ OPEX:                        $445K (on target)
└─ Early ROI Signal:            $180K productivity savings (pilot teams)

───────────────────────────────────────────────────────────
PROGRESS HIGHLIGHTS
───────────────────────────────────────────────────────────

✓ Developer Portal (COMPLETED)
  - Launched Jan 15, 99.9% uptime
  - 200+ active users, 4.5 stars average rating
  - Self-service provisioning: 120 services created

✓ CI/CD Standardization (COMPLETED)
  - GitHub Actions templates for Node.js, Python, Go
  - 42 services migrated from Jenkins
  - 3.2x increase in deployment frequency

✓ Container Platform MVP (85% COMPLETE)
  - EKS staging environment live
  - Production environment in final testing (launching April 5)
  - 15 teams successfully containerized

✓ Security Baseline (COMPLETED)
  - Vault integration: 100% secrets migrated
  - Container scanning: 0 critical vulnerabilities
  - RBAC implemented, SOC 2 compliant

⏳ Observability (IN PROGRESS, 60% complete)
  - Datadog agents deployed to staging
  - Production rollout scheduled for April
  - Custom dashboards: 5/10 complete

───────────────────────────────────────────────────────────
DECISIONS NEEDED
───────────────────────────────────────────────────────────

🔴 URGENT (This Week):

1. Production EKS Go/No-Go Decision (April 5)
   - Recommendation: APPROVE
   - Readiness: 95% (minor load testing pending)
   - Risk: Low (staging proven stable for 6 weeks)
   - Impact: Unlocks Q2 scale phase

2. Additional Budget for Datadog ($50K)
   - Recommendation: APPROVE
   - Reason: Usage 20% higher than estimate (good problem - high adoption)
   - Impact: Avoid service disruption, support 15 additional teams
   - Alternative: Reduce log retention (not recommended)

🟡 IMPORTANT (Next 2 Weeks):

3. Q2 Hiring: Add 2 Platform Engineers
   - Recommendation: APPROVE
   - Reason: Onboarding velocity exceeding plan (need support capacity)
   - Impact: Sustain momentum, avoid team burnout
   - Cost: $200K additional OPEX (within contingency budget)

───────────────────────────────────────────────────────────
TOP RISKS & MITIGATIONS
───────────────────────────────────────────────────────────

🟡 MEDIUM RISK: CFO Budget Scrutiny for Q2

Probability: 60% | Impact: HIGH
Description: CFO questioning Q2 budget increase (+$50K Datadog, +$200K hiring)
Mitigation:
  ✓ Schedule CFO deep-dive on pilot team ROI results (April 10)
  ✓ Show $180K early productivity savings vs $50K ask
  ✓ Demonstrate higher-than-expected adoption (reduced risk)
Status: Under control, CFO meeting scheduled

🟡 MEDIUM RISK: Legacy Team Resistance

Probability: 50% | Impact: MEDIUM
Description: 5 legacy teams hesitant to migrate from Jenkins
Mitigation:
  ✓ Voluntary opt-in only (no forced migration)
  ✓ "Concierge" migration support for skeptical teams
  ✓ Showcase success stories from similar teams
Status: Monitoring, no escalation needed yet

🟢 LOW RISK: Kubernetes Skills Gap

Probability: 30% | Impact: MEDIUM
Description: Platform team learning Kubernetes, potential velocity impact
Mitigation:
  ✓ Hired Kubernetes expert (started Feb 1)
  ✓ Team training: 80% completed
  ✓ AWS EKS support contract in place
Status: Resolved, team velocity improving

───────────────────────────────────────────────────────────
STAKEHOLDER SENTIMENT
───────────────────────────────────────────────────────────

Champions (Strong Support):
✓ VP Engineering - "Best investment we've made in years"
✓ SRE Team - Actively evangelizing to dev teams
✓ Security Team - Praising security automation

Allies (Support):
✓ VP Product - Seeing faster feature delivery
✓ Platform Team - High morale, engaged

Neutrals → Improving:
→ CFO - Skepticism easing with pilot results (was Skeptic)
→ CISO - Security posture validation complete

Skeptics (Watching closely):
⚠ Legacy App Team Leads - Waiting to see migration ease

───────────────────────────────────────────────────────────
WHAT'S NEXT: Q2 PREVIEW
───────────────────────────────────────────────────────────

Q2 Focus: SCALE (Apr-Jun 2026)

Target: 35 additional teams onboarded (15 → 50 total, 100% of MVP goal)

Major Milestones:
• April 15: Production EKS launch
• May 1: Observability full rollout
• May 15: Self-service database provisioning
• June 1: Advanced CI/CD features (blue/green deploys)
• June 30: MVP COMPLETE - 50 teams onboarded

Budget: Q2 ask is $1,350K (+$250K vs Q1 for hiring and scale)

───────────────────────────────────────────────────────────
RECOMMENDATION
───────────────────────────────────────────────────────────

Recommend: CONTINUE FULL SPEED

Rationale:
✓ Strong Q1 execution (ahead of schedule, under budget)
✓ Early ROI signals positive ($180K savings in 3 months)
✓ High developer adoption and satisfaction (NPS +35)
✓ CFO concerns being addressed with data
✓ No major blockers identified

Approve Q2 budget adjustments to sustain momentum.
```

### Narrative Format
```markdown
# Executive Briefing: Platform Transformation Program

**To**: CTO
**From**: Platform Program Manager
**Date**: March 31, 2026
**Period**: Q1 FY2026
**Status**: 🟢 ON TRACK

---

## Executive Summary

I'm pleased to report that the Platform Transformation program delivered
a strong Q1, completing 85% of the MVP foundation and onboarding 15 pilot
teams—ahead of our aggressive schedule. We're under budget by 2% ($25K)
and already seeing tangible productivity gains: deployment frequency up
3.2x and lead time down 25%.

The Developer Portal launched successfully in mid-January and has become
the central hub for our engineering organization, with 200+ active users
and a 4.5-star rating. Our CI/CD standardization effort has migrated 42
services from Jenkins to GitHub Actions, and early adopters report
significantly improved developer experience.

Most importantly, we're demonstrating ROI earlier than expected. Pilot
teams have achieved $180K in productivity savings in just 3 months,
which is helping to address CFO skepticism around our business case.

**Bottom Line**: The program is on track. I recommend approving Q2 budget
adjustments to sustain our momentum and capitalize on higher-than-expected
adoption.

---

## Progress Against Plan

### What We Delivered in Q1

**Developer Portal** (✓ COMPLETED)
Launched January 15, two weeks ahead of schedule. The portal has become
the single pane of glass for our developers, with self-service
provisioning, searchable service catalog, and comprehensive documentation.
Adoption has exceeded expectations: 200+ active users and 120 services
self-provisioned.

**CI/CD Standardization** (✓ COMPLETED)
Standardized build pipelines for our three primary languages (Node.js,
Python, Go). 42 services have migrated from Jenkins, and teams report
3.2x faster deployment frequency and significantly reduced configuration
burden.

**Container Platform** (⏳ 85% COMPLETE)
Our EKS-based container platform is production-ready, with staging
environment validated over 6 weeks. Production environment is in final
load testing and scheduled for April 5 go-live. 15 teams have
successfully containerized their applications.

**Security Baseline** (✓ COMPLETED)
All platform components meet SOC 2 requirements. Vault integration is
complete with 100% of secrets migrated. Container scanning integrated
into CI/CD with zero critical vulnerabilities detected.

### What's Tracking Behind

**Observability** (⏳ 60% COMPLETE)
Datadog rollout is 2 weeks behind schedule due to higher-than-expected
configuration complexity. Staging is complete; production rollout now
scheduled for mid-April. Not on critical path for Q2 goals.

---

## Financial Performance

**Q1 Spend: $1,625K** (Budget: $1,650K, **-2% under**)

We delivered strong budget discipline in Q1, coming in $25K under
budget despite accelerated onboarding velocity. The underspend was
driven by:
- Datadog usage optimization ($15K savings)
- Delayed hiring (1 platform engineer started Feb instead of Jan, $10K)

However, I'm requesting two budget adjustments for Q2:
1. **+$50K for Datadog**: Higher adoption driving 20% more usage than estimated
2. **+$200K for 2 additional platform engineers**: Support capacity for scale phase

Both adjustments are within our contingency budget and justified by
accelerated adoption (reduced program risk).

**Early ROI Signal**: Pilot teams have achieved **$180K** in productivity
savings over 3 months, putting us on track for 18-month payback.

[Continues with detailed narrative...]
```

### Slides Format
```
═══════════════════════════════════════════════════════════
SLIDE 1: TITLE
═══════════════════════════════════════════════════════════

Platform Transformation
Q1 FY2026 Executive Briefing

Status: 🟢 ON TRACK

Presented to: CTO
Date: March 31, 2026

───────────────────────────────────────────────────────────
SLIDE 2: EXECUTIVE SUMMARY
───────────────────────────────────────────────────────────

Q1 Highlights

✓ 85% MVP Complete (ahead of schedule)
✓ 15 Teams Onboarded (30% of goal)
✓ Under Budget by 2% ($25K savings)
✓ Early ROI: $180K productivity gains

Developer NPS: +35 (exceeded year-end target of +30)

Bottom Line: Strong execution. Recommend continuing.

───────────────────────────────────────────────────────────
SLIDE 3: STATUS DASHBOARD
───────────────────────────────────────────────────────────

        Status          Target    Actual    RAG
Schedule                Mar 31    Mar 15    🟢
Budget (Q1)             $1,650K   $1,625K   🟢
Team Onboarding         10        15        🟢
Developer NPS           +20       +35       🟢
Platform Uptime         99.5%     99.8%     🟢

CFO Sentiment           Ally      Neutral   🟡

───────────────────────────────────────────────────────────
SLIDE 4: KEY METRICS
───────────────────────────────────────────────────────────

Productivity Gains (Pilot Teams)

Deployment Frequency:    +220% (2/week → 6.4/week)
Deployment Lead Time:    -25%  (4 hours → 3 hours)
Failed Deployments:      -40%  (10% → 6%)
Time to First Deploy:    -85%  (2 days → 2 hours)

Early ROI: $180K savings in 3 months

───────────────────────────────────────────────────────────
SLIDE 5: DECISIONS NEEDED
───────────────────────────────────────────────────────────

🔴 URGENT

1. Production EKS Go/No-Go (April 5)
   Recommendation: APPROVE

2. Datadog Budget +$50K
   Recommendation: APPROVE (high adoption = good problem)

🟡 IMPORTANT

3. Q2 Hiring: +2 Platform Engineers
   Recommendation: APPROVE (within contingency)

───────────────────────────────────────────────────────────
SLIDE 6: RISKS & MITIGATIONS
───────────────────────────────────────────────────────────

Top Risks:

🟡 CFO Budget Scrutiny (Q2 increase)
   → Mitigation: ROI deep-dive April 10

🟡 Legacy Team Resistance
   → Mitigation: Voluntary migration + concierge support

🟢 Kubernetes Skills Gap
   → Resolved: Expert hired, training 80% complete

───────────────────────────────────────────────────────────
SLIDE 7: Q2 PREVIEW
───────────────────────────────────────────────────────────

Q2 Goals: SCALE ADOPTION

Target: 50 teams total (+35 in Q2)

Major Milestones:
• Apr 15: Production EKS launch
• May 15: Self-service DB provisioning
• Jun 30: MVP COMPLETE

Q2 Budget: $1,350K (+$250K for hiring + scale)

───────────────────────────────────────────────────────────
SLIDE 8: RECOMMENDATION
───────────────────────────────────────────────────────────

RECOMMENDATION: CONTINUE FULL SPEED

✓ Ahead of schedule
✓ Under budget
✓ Strong ROI signals
✓ High developer satisfaction

Approve Q2 budget adjustments to capitalize on momentum.
```

### Memo Format
```
TO:       Sarah Chen, CTO
FROM:     Alex Martinez, Platform Program Manager
DATE:     March 31, 2026
SUBJECT:  Platform Transformation Q1 Review - ON TRACK
────────────────────────────────────────────────────────────

BOTTOM LINE UP FRONT

The Platform Transformation program is ON TRACK with strong Q1
execution. We're 2 weeks ahead of schedule, 2% under budget, and
already demonstrating ROI ($180K productivity savings). I recommend
approving Q2 budget adjustments (+$250K) to sustain momentum and
capitalize on higher-than-expected adoption.

────────────────────────────────────────────────────────────

Q1 RESULTS SUMMARY

✓ MVP Foundation: 85% complete (target was 75%)
✓ Teams Onboarded: 15 (target was 10)
✓ Budget: $1,625K spent (budget $1,650K, -2%)
✓ Developer NPS: +35 (year-end target was +30)
✓ Platform Uptime: 99.8% (target 99.5%)

Early ROI signal: Pilot teams achieving $180K in productivity
savings over 3 months.

────────────────────────────────────────────────────────────

WHAT WENT WELL

1. Developer Portal exceeded expectations
   - Launched 2 weeks early, 4.5-star rating
   - 200+ active users, 120 self-service provisions

2. CI/CD migration momentum
   - 42 services migrated from Jenkins
   - Deployment frequency up 3.2x

3. Strong financial discipline
   - 2% under budget despite accelerated velocity

4. Developer satisfaction
   - NPS +35 already exceeds year-end target

────────────────────────────────────────────────────────────

CHALLENGES & MITIGATIONS

1. CFO Budget Scrutiny for Q2
   - Challenge: Requesting +$250K for Q2 (Datadog + hiring)
   - Mitigation: Scheduled ROI deep-dive April 10 to show
     $180K early savings vs $50K Datadog ask

2. Legacy Team Resistance
   - Challenge: 5 teams hesitant to migrate
   - Mitigation: Voluntary approach + concierge support

────────────────────────────────────────────────────────────

DECISIONS NEEDED

🔴 URGENT (This Week):

1. Production EKS Go/No-Go (April 5 launch date)
   - Recommendation: APPROVE
   - Readiness: 95% (minor load testing pending)
   - Risk: Low (staging stable for 6 weeks)

2. Datadog Budget Increase (+$50K)
   - Recommendation: APPROVE
   - Reason: Usage 20% higher (high adoption)
   - Impact: Support 15 additional teams

🟡 IMPORTANT (Next 2 Weeks):

3. Q2 Hiring: +2 Platform Engineers (+$200K OPEX)
   - Recommendation: APPROVE
   - Reason: Support capacity for scale phase
   - Note: Within contingency budget

────────────────────────────────────────────────────────────

Q2 OUTLOOK

Focus: SCALE to 50 teams (35 additional in Q2)

Major Milestones:
- April 15: Production EKS launch
- May 15: Self-service DB provisioning
- June 30: MVP COMPLETE (50 teams onboarded)

Q2 Budget Request: $1,350K (+$250K vs Q1)

────────────────────────────────────────────────────────────

RECOMMENDATION

CONTINUE FULL SPEED. Strong Q1 execution, early ROI signals,
and high developer satisfaction justify sustained investment.
Approve Q2 budget adjustments to capitalize on momentum.
```

## Briefing Templates by Audience

### CTO Briefing
```
Focus: Technical progress, architecture decisions, developer productivity
Metrics: Adoption, velocity, quality, platform performance
Tone: Balanced technical + business
Length: 2 pages max (dashboard) or 10 slides
```

### CFO Briefing
```
Focus: Financial performance, ROI, budget variance
Metrics: Spend vs budget, early ROI signals, cost per developer
Tone: Financial rigor, data-driven
Length: 1 page (memo) or 5 slides
```

### Board Briefing
```
Focus: Strategic progress, risk management, competitive positioning
Metrics: High-level outcomes (revenue impact, time-to-market)
Tone: Confident, strategic, concise
Length: 5-7 slides max
```

### All-Hands Briefing
```
Focus: Wins, team recognition, upcoming features
Metrics: Adoption, new capabilities, user stories
Tone: Inspiring, inclusive, celebratory
Length: 10 minutes presentation
```

## RAG Status Definitions

### 🟢 GREEN (On Track)
- Schedule: Within 1 week of plan
- Budget: Within ±5% of forecast
- Quality: No P0 defects, <5 P1s
- Stakeholders: Majority supportive

### 🟡 YELLOW (At Risk)
- Schedule: 1-2 weeks behind
- Budget: 5-10% variance
- Quality: 5-10 P1 defects
- Stakeholders: Key skeptics, needs attention

### 🔴 RED (Off Track)
- Schedule: >2 weeks behind
- Budget: >10% variance
- Quality: >10 P1 defects or any P0s
- Stakeholders: Active blockers

## Examples

### Example 1: CTO Dashboard
```bash
/exec-briefing --initiative "platform-transformation" --period Q1-FY2026 --audience CTO --format dashboard
```

### Example 2: CFO Financial Review
```bash
/exec-briefing --initiative "platform-transformation" --period January-2026 --audience CFO --format memo --include-metrics false
```

### Example 3: Board Presentation
```bash
/exec-briefing --initiative "platform-transformation" --period Q1-FY2026 --audience Board --format slides --tone confident
```

### Example 4: Weekly Status
```bash
/exec-briefing --initiative "ci-cd-migration" --period Week-of-Jan-15 --audience Executive-Team --format narrative
```

## Integration with Agents

```bash
# Generate executive briefing via Governance Agent
@governance-agent "Create Q1 executive briefing for CTO"

# Agent invokes:
/exec-briefing --initiative "platform-transformation" --period Q1-FY2026 --audience CTO

# Can combine with stakeholder map:
@stakeholder-agent "Who should receive this briefing?"
```

## Best Practices

1. **Lead with Bottom Line**: Busy executives want the answer first
2. **Use RAG Status**: Visual indicators (🟢🟡🔴) for quick assessment
3. **Be Honest**: Don't hide risks or challenges
4. **Actionable Decisions**: Clearly state what you need from them
5. **Data Over Opinion**: Support claims with metrics
6. **Tailor to Audience**: CFO wants finance, CTO wants technical depth

## Common Pitfalls

❌ **Too Much Detail**: Executives don't have time for 10-page reports
❌ **Hiding Bad News**: Surprises damage trust
❌ **No Clear Ask**: Don't leave them wondering what you need
❌ **Metrics Without Context**: Show baseline, target, and actual
❌ **Generic Template**: Customize for your specific program and audience

## Related Skills
- `/stakeholder-map` - Identify who needs briefings
- `/risk-assessment` - Detail risks section
- `/budget-forecast` - Financial sections
- `/dependency-analysis` - Program dependencies

## Related Agents
- `@governance-agent` - Governance and executive communication
- `@financial-agent` - Financial performance details
- `@stakeholder-agent` - Stakeholder-specific communication

## Implementation Notes

This skill uses:
- Executive communication best practices
- RAG (Red/Amber/Green) status frameworks
- Program management reporting standards (PMI)
- BLUF (Bottom Line Up Front) structure for executive memos

Customize templates based on your organizational culture and executive preferences.
