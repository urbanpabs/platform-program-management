# Skill: Stakeholder Map

## Description
Create comprehensive stakeholder influence and engagement map using Power/Interest matrix with tailored communication strategies.

## Usage
```bash
/stakeholder-map --initiative "platform-transformation" --format visual --include-engagement-plan
```

## Parameters

### Required
- `--initiative` (string): Initiative name or description (e.g., "platform-transformation", "ci-cd-migration")

### Optional
- `--format` (string): Output format: "visual", "table", "detailed", "engagement-plan" (default: "visual")
- `--include-engagement-plan` (boolean): Include detailed engagement strategies (default: true)
- `--organization-size` (string): Organization size: "startup", "mid-market", "enterprise" (default: "enterprise")
- `--phase` (string): Program phase: "planning", "execution", "scaling" (default: "planning")
- `--sentiment` (boolean): Include stakeholder sentiment analysis (default: true)

## Output Formats

### Visual Format (Power/Interest Matrix)
```
===========================================
STAKEHOLDER MAP: PLATFORM TRANSFORMATION
===========================================
Initiative: Platform Transformation Program
Phase: Planning
Date: January 2026

────────────────────────────────────────
POWER/INTEREST MATRIX
────────────────────────────────────────

Power
  ↑
  │
H │  MANAGE CLOSELY          │  KEEP SATISFIED
I │  (High Power, High Int)  │  (High Power, Low Int)
G │                          │
H │  • CTO (Champion)        │  • CFO (Skeptic)
  │  • VP Engineering (Ally) │  • CISO (Neutral)
  │  • VP Product (Ally)     │  • VP Operations (Neutral)
  │                          │  • Board (Monitor)
──┼──────────────────────────┼─────────────────────────
  │                          │
L │  KEEP INFORMED           │  MONITOR
O │  (Low Power, High Int)   │  (Low Power, Low Int)
W │                          │
  │  • Platform Team Leads   │  • Individual Contributors
  │  • Dev Team Leads (50)   │  • QA Team (Neutral)
  │  • SRE Team (Champion)   │  • Support Team
  │  • Security Eng (Ally)   │
  │                          │
  └──────────────────────────┴─────────────────────────→
       HIGH INTEREST              LOW INTEREST

────────────────────────────────────────
STAKEHOLDER CLASSIFICATION
────────────────────────────────────────

Champions (Actively Promote):
✓ CTO - Executive sponsor, budget owner
✓ SRE Team - Direct beneficiaries, early adopters
✓ Platform Team - Primary implementers

Allies (Support):
✓ VP Engineering - Recognizes developer productivity value
✓ VP Product - Interested in faster delivery
✓ Security Engineering - Values security automation

Neutrals (On the Fence):
○ CISO - Needs security assurance
○ VP Operations - Concerned about disruption
○ QA Team - Unclear on impact

Skeptics (Resistant):
✗ CFO - Questions ROI, budget constraints
✗ Senior Backend Team Lead - Prefers current Jenkins setup
✗ Legacy App Team - Fears forced migration

Blockers (Active Resistance):
⛔ None currently identified

────────────────────────────────────────
ENGAGEMENT PRIORITY TIERS
────────────────────────────────────────

TIER 1 (Weekly): CTO, VP Engineering
TIER 2 (Bi-weekly): CFO, CISO, VP Product, VP Operations
TIER 3 (Monthly): Platform Team Leads, Dev Team Leads
TIER 4 (Quarterly): Board, Individual Contributors
```

### Table Format
```
┌──────────────────┬────────┬──────────┬───────────┬───────────┬─────────────────┐
│ Stakeholder      │ Power  │ Interest │ Stance    │ Sentiment │ Engagement Tier │
├──────────────────┼────────┼──────────┼───────────┼───────────┼─────────────────┤
│ CTO              │ HIGH   │ HIGH     │ Champion  │ +2        │ Tier 1 (Weekly) │
│ VP Engineering   │ HIGH   │ HIGH     │ Ally      │ +1        │ Tier 1 (Weekly) │
│ VP Product       │ HIGH   │ HIGH     │ Ally      │ +1        │ Tier 2          │
│ CFO              │ HIGH   │ LOW      │ Skeptic   │ -1        │ Tier 2          │
│ CISO             │ HIGH   │ MEDIUM   │ Neutral   │  0        │ Tier 2          │
│ VP Operations    │ MEDIUM │ LOW      │ Neutral   │  0        │ Tier 2          │
│ SRE Team         │ LOW    │ HIGH     │ Champion  │ +2        │ Tier 3          │
│ Platform Leads   │ MEDIUM │ HIGH     │ Champion  │ +2        │ Tier 3          │
│ Dev Team Leads   │ LOW    │ HIGH     │ Ally      │ +1        │ Tier 3          │
│ Security Eng     │ LOW    │ HIGH     │ Ally      │ +1        │ Tier 3          │
│ Legacy App Team  │ LOW    │ MEDIUM   │ Skeptic   │ -1        │ Tier 3          │
│ Board            │ HIGH   │ LOW      │ Monitor   │  0        │ Tier 4          │
└──────────────────┴────────┴──────────┴───────────┴───────────┴─────────────────┘

Sentiment Scale: +2 (Strong Support) → -2 (Strong Opposition)
```

### Detailed Format
```markdown
# Stakeholder Analysis: Platform Transformation

## Executive Summary

**Total Stakeholders Identified**: 15
**Champions**: 3 (20%)
**Allies**: 4 (27%)
**Neutrals**: 5 (33%)
**Skeptics**: 3 (20%)
**Blockers**: 0 (0%)

**Overall Sentiment**: Positive (+0.4 average)
**Risk Level**: Medium (CFO skepticism, legacy team resistance)

---

## Detailed Stakeholder Profiles

### 1. CTO (Sarah Chen)

**Position**: Chief Technology Officer
**Power Level**: HIGH (Budget authority, strategic decisions)
**Interest Level**: HIGH (Direct responsibility)
**Stance**: Champion ✓
**Sentiment**: +2 (Strong Support)

**Motivations**:
- Strategic mandate to improve engineering velocity
- Board pressure for digital transformation
- Personal track record of platform success at previous company

**Concerns**:
- Execution risk (timeline, budget adherence)
- Organizational change resistance
- Measuring and demonstrating ROI

**Influence on Others**:
- Direct authority over VP Engineering, VP Product
- Strong influence on CFO budget decisions
- Board confidence and credibility

**Engagement Strategy**:
- Weekly 1:1 status updates (30 min)
- Monthly executive steering committee (with CFO, CISO)
- Quarterly board presentation support
- Immediate escalation for blockers

**Communication Preferences**:
- Format: Executive dashboard + brief narrative
- Frequency: Weekly
- Channel: Email + in-person
- Focus: ROI, risks, key decisions

---

### 2. CFO (Michael Rodriguez)

**Position**: Chief Financial Officer
**Power Level**: HIGH (Budget approval authority)
**Interest Level**: LOW (Not directly impacted)
**Stance**: Skeptic ✗
**Sentiment**: -1 (Mild Opposition)

**Motivations**:
- Cost control and budget discipline
- Demonstrable ROI on investments
- Shareholder value

**Concerns**:
- $4.8M budget request in constrained fiscal year
- Unproven ROI assumptions (20% productivity gain)
- Opportunity cost vs other investments

**Influence on Others**:
- Budget veto power
- Board financial recommendation weight
- FP&A team follows his lead

**Engagement Strategy**:
- Bi-weekly ROI review meetings
- Monthly financial deep-dive (actuals vs forecast)
- Quarterly business case refresh
- Involve in vendor negotiations (demonstrate cost discipline)

**Communication Preferences**:
- Format: Financial models, variance reports
- Frequency: Bi-weekly
- Channel: Scheduled meetings + Excel models
- Focus: ROI, budget adherence, risk mitigation

**Conversion Plan** (Skeptic → Neutral → Ally):
1. Month 1-2: Address ROI concerns with detailed financial model
2. Month 3-4: Demonstrate early wins (pilot team productivity gains)
3. Month 6: Show actual cost savings vs forecast
4. Month 12: Celebrate payback milestone

[... continues for all 15 stakeholders ...]
```

### Engagement Plan Format
```
===========================================
STAKEHOLDER ENGAGEMENT PLAN
===========================================

Initiative: Platform Transformation
Planning Horizon: 12 months
Owner: Platform Program Manager

────────────────────────────────────────
COMMUNICATION CALENDAR
────────────────────────────────────────

WEEKLY:
• Monday 9am: CTO 1:1 (30 min) - Status, blockers, decisions
• Tuesday 10am: VP Engineering sync (30 min) - Technical progress
• Friday 2pm: Platform team standup (30 min) - Execution updates

BI-WEEKLY:
• 1st/3rd Thursday: CFO ROI review (45 min) - Financial performance
• 2nd/4th Tuesday: CISO security review (30 min) - Compliance, risks
• Alternating Friday: VP Product sync (30 min) - Roadmap alignment

MONTHLY:
• First Monday: Executive Steering Committee (90 min)
  - Attendees: CTO, CFO, CISO, VP Eng, VP Product, VP Ops
  - Agenda: Status, decisions, budget, risks
  - Format: Dashboard + key topics + Q&A

• Mid-month: All-Hands Developer Q&A (60 min)
  - Audience: All developers, dev leads
  - Format: Demo + roadmap + open Q&A
  - Goal: Build grassroots support

• Last Friday: Platform Team Retrospective (90 min)
  - Team reflection and continuous improvement

QUARTERLY:
• Board Update (30 min presentation)
  - Focus: Strategic progress, ROI, key risks
  - Owner: CTO (with Platform PM support)

• Quarterly Business Review (2 hours)
  - Deep dive on metrics, lessons, planning
  - Attendees: All Tier 1 & 2 stakeholders

────────────────────────────────────────
COMMUNICATION ARTIFACTS
────────────────────────────────────────

Weekly Status Report:
- Audience: CTO, VP Engineering
- Format: 1-page summary
- Content: Progress (RAG), risks, decisions needed
- Delivery: Friday 4pm via email

Monthly Executive Dashboard:
- Audience: Executive Steering Committee
- Format: PowerPoint (5 slides max)
- Content: Metrics, budget, roadmap, risks
- Delivery: 2 days before steering meeting

Quarterly Board Deck:
- Audience: Board of Directors
- Format: PowerPoint (10 slides)
- Content: Strategic narrative, ROI, major milestones
- Delivery: 1 week before board meeting

Developer Newsletter:
- Audience: All developers (400+)
- Format: Email newsletter
- Content: New capabilities, tutorials, success stories
- Frequency: Monthly

────────────────────────────────────────
STAKEHOLDER-SPECIFIC TACTICS
────────────────────────────────────────

CFO (Convert Skeptic → Ally):
✓ Invite to pilot team demo (Month 3) - See productivity gains firsthand
✓ Co-present ROI results to board (Month 6) - Share success
✓ Include in vendor negotiations (Ongoing) - Show cost discipline
✓ Monthly "Actual vs Forecast" review - Build trust with transparency

CISO (Convert Neutral → Ally):
✓ Security review checkpoint in every phase gate
✓ Highlight security automation wins (vulnerability reduction)
✓ Invite to platform security architecture review
✓ Celebrate SOC 2 audit success (platform contribution)

Legacy App Team (Convert Skeptic → Neutral):
✓ Don't force migration - voluntary opt-in only
✓ Dedicate migration support resources (make it easy)
✓ Showcase early adopter success stories from similar teams
✓ Offer "concierge" onboarding for first migration

────────────────────────────────────────
RESISTANCE MANAGEMENT
────────────────────────────────────────

Anticipated Resistance Points:

1. "Not Invented Here" Syndrome (Legacy teams)
   - Mitigation: Involve skeptics in design reviews, incorporate feedback
   - Tactic: Create "Platform Advisory Council" with skeptic representation

2. Budget Constraints (CFO)
   - Mitigation: Phase spending, demonstrate early ROI
   - Tactic: Quick wins in first 3 months to validate business case

3. Change Fatigue (Developers)
   - Mitigation: Don't force adoption, voluntary opt-in
   - Tactic: Make platform so good that teams *want* to migrate

4. Security Concerns (CISO)
   - Mitigation: Security-first design, early CISO involvement
   - Tactic: Platform *improves* security posture (scanning, secrets management)

────────────────────────────────────────
SUCCESS METRICS
────────────────────────────────────────

Stakeholder Engagement Effectiveness:

• Stakeholder sentiment score: Target +1.0 (currently +0.4)
• Executive meeting attendance: Target 90%
• CFO conversion: Target Ally by Month 6
• Developer NPS: Target 30+ by Month 12
• No surprise escalations: 0 per quarter
```

## Stakeholder Categories

### By Organizational Level
```
C-Suite: CTO, CFO, CISO, COO, CPO
VP/Director: VP Engineering, VP Product, VP Ops, Dir Security
Manager: Engineering Managers, Product Managers, Team Leads
Individual Contributor: Developers, SREs, Security Engineers
```

### By Functional Area
```
Engineering: Developers, Team Leads, Architects
Product: Product Managers, Product Owners
Security: CISO, Security Engineers, Compliance
Finance: CFO, FP&A, Procurement
Operations: SRE, Infrastructure, IT Ops
Executive: Board, C-Suite
```

## Power/Interest Quadrants

### Manage Closely (High Power, High Interest)
```
Engagement: Weekly 1:1s, steering committee
Communication: Detailed, decision-focused
Risk: High impact if not aligned
Examples: CTO, VP Engineering, Executive Sponsor
```

### Keep Satisfied (High Power, Low Interest)
```
Engagement: Monthly updates, quarterly reviews
Communication: Executive summaries, metrics
Risk: Can become blockers if neglected
Examples: CFO, CISO, Board
```

### Keep Informed (Low Power, High Interest)
```
Engagement: Regular updates, feedback loops
Communication: Progress reports, demos
Risk: Can become champions or critics
Examples: Dev Team Leads, SRE Team, Platform Engineers
```

### Monitor (Low Power, Low Interest)
```
Engagement: Broadcast communications, occasional updates
Communication: Newsletters, announcements
Risk: Low, but don't ignore completely
Examples: Individual developers, support teams
```

## Examples

### Example 1: Basic Stakeholder Map
```bash
/stakeholder-map --initiative "platform-transformation" --format visual
```

### Example 2: Detailed Profiles
```bash
/stakeholder-map --initiative "ci-cd-migration" --format detailed --sentiment true
```

### Example 3: Engagement Plan
```bash
/stakeholder-map --initiative "platform-transformation" --format engagement-plan --phase execution
```

### Example 4: Startup Context
```bash
/stakeholder-map --initiative "devops-automation" --organization-size startup --format table
```

### Example 5: Scaling Phase
```bash
/stakeholder-map --initiative "platform-expansion" --phase scaling --include-engagement-plan true
```

## Integration with Agents

```bash
# Create stakeholder map via Stakeholder Agent
@stakeholder-agent "Map stakeholders for our platform transformation"

# Agent invokes:
/stakeholder-map --initiative "platform-transformation" --format detailed

# Can combine with governance:
@governance-agent "Create executive steering committee based on stakeholder map"
```

## Best Practices

1. **Update Regularly**: Refresh stakeholder map monthly as sentiment shifts
2. **Be Specific**: Name real people, not generic roles
3. **Sentiment Tracking**: Monitor changes over time
4. **Convert Skeptics**: Prioritize converting high-power skeptics to neutrals/allies
5. **Leverage Champions**: Use champions to influence neutrals
6. **Communicate Transparently**: Share risks and challenges openly

## Common Pitfalls

❌ **Ignoring Low-Power Stakeholders**: Grassroots resistance can derail programs
❌ **One-Time Mapping**: Stakeholder landscape changes, update frequently
❌ **Generic Engagement**: Tailor communication to each stakeholder's motivations
❌ **Avoiding Skeptics**: Engage skeptics early, don't let resistance fester
❌ **Over-Communication**: Respect stakeholder time, be concise

## Stakeholder Conversion Tactics

### Skeptic → Neutral
```
1. Listen first: Understand their concerns without being defensive
2. Address concerns: Provide data, mitigations, alternative approaches
3. Invite participation: Include in design reviews, decision-making
4. Quick wins: Demonstrate early value that addresses their concerns
```

### Neutral → Ally
```
1. Show value: Demonstrate how initiative benefits them personally
2. Involve in success: Give them credit for contributions
3. Build relationship: Regular touchpoints, build trust
4. Peer influence: Connect with existing allies
```

### Ally → Champion
```
1. Empower: Give them platform to advocate (presentations, demos)
2. Celebrate: Public recognition for their support
3. Partner: Collaborate on key decisions and milestones
4. Sustain: Maintain relationship, don't take for granted
```

## Related Skills
- `/exec-briefing` - Create executive briefing for stakeholders
- `/risk-assessment` - Identify stakeholder-related risks
- `/create-roadmap` - Align roadmap with stakeholder priorities

## Related Agents
- `@stakeholder-agent` - Complex stakeholder questions
- `@governance-agent` - Governance structures for stakeholder management
- `@strategy-agent` - Align stakeholder engagement to strategy

## Implementation Notes

This skill uses:
- Power/Interest matrix framework (Mendelow, 1991)
- Stakeholder analysis best practices (PMI, PMBOK)
- Organizational change management principles
- Influence mapping techniques

For organization-specific stakeholder maps, provide organizational context (size, culture, history of change initiatives).
