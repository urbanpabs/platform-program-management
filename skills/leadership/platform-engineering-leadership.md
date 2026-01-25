# Skill: Platform Engineering Leadership

## Description
Leadership skill for Platform Engineering leaders managing platform teams, driving developer experience, and enabling organizational transformation. Covers team structure, developer advocacy, platform adoption strategies, technical leadership practices, and engineering culture.

## Usage
```bash
/platform-engineering-leadership --action "team-structure" --size "medium"
/platform-engineering-leadership --action "adoption-strategy" --target "70%"
/platform-engineering-leadership --action "devex-assessment" --scope "full"
/platform-engineering-leadership --action "culture-playbook"
/platform-engineering-leadership --action "leadership-principles"
```

## Parameters

### Required
- `--action` (string): Leadership action to perform:
  - `team-structure` - Design platform team structure
  - `adoption-strategy` - Create platform adoption strategy
  - `devex-assessment` - Developer experience assessment
  - `culture-playbook` - Engineering culture playbook
  - `leadership-principles` - Platform leadership principles
  - `stakeholder-influence` - Influence without authority
  - `hiring-guide` - Platform team hiring guide
  - `career-ladder` - Platform engineering career ladder
  - `onboarding-plan` - Team onboarding plan

### Optional
- `--size` (string): Team size: "small" (3-5), "medium" (6-12), "large" (13-25), "enterprise" (25+) (default: "medium")
- `--target` (string): Adoption target percentage (e.g., "70%")
- `--scope` (string): Assessment scope: "quick", "standard", "full" (default: "standard")
- `--maturity` (string): Platform maturity: "early", "scaling", "mature" (default: "scaling")
- `--output` (string): Output format: "markdown", "html", "slides" (default: "markdown")

---

## Core Capabilities

### 1. Platform Team Structure

```markdown
# Platform Team Structure: Medium (6-12 people)

## Team Topology: Platform Team

### Team Mission
Enable product teams to deliver value faster through self-service platform capabilities, reducing cognitive load and eliminating infrastructure friction.

---

## Recommended Structure (10 people)

### Leadership (1)
```
Platform Engineering Manager
├── Owns team vision, roadmap, stakeholder relationships
├── Manages team health, hiring, career development
├── Reports to: VP of Engineering / CTO
└── Key metrics: Platform adoption, developer NPS, team velocity
```

### Platform Product (2)
```
Platform Product Manager
├── Owns platform backlog, prioritization, user research
├── Defines success metrics, OKRs, feature specs
└── Works with: All platform engineers, stakeholders

Platform Designer (Optional / 0.5 FTE)
├── Developer portal UX, documentation design
├── User research support, journey mapping
└── Often shared with other teams
```

### Core Platform Engineers (6)
```
Senior Platform Engineer (2)
├── Technical leadership, architecture decisions
├── Mentoring, code review, standards
└── Specialization: Infrastructure / Developer Experience

Platform Engineer (3)
├── Feature development, maintenance
├── Tooling, automation, integrations
└── Rotation: On-call, support

Associate Platform Engineer (1)
├── Learning, pair programming
├── Documentation, testing
└── Growth path to Platform Engineer
```

### Platform SRE (1)
```
Platform SRE
├── Platform reliability, SLOs, incident response
├── Observability, alerting, capacity planning
└── Bridge between platform team and SRE org
```

---

## Team Interactions

```
                    ┌─────────────────┐
                    │   Leadership    │
                    │   (VP/CTO)      │
                    └────────┬────────┘
                             │
                    ┌────────▼────────┐
                    │ Platform Eng    │
                    │ Manager         │
                    └────────┬────────┘
                             │
        ┌────────────────────┼────────────────────┐
        │                    │                    │
┌───────▼───────┐   ┌───────▼───────┐   ┌───────▼───────┐
│ Platform      │   │ Core          │   │ Platform      │
│ Product       │   │ Engineers     │   │ SRE           │
└───────────────┘   └───────────────┘   └───────────────┘
        │                    │                    │
        └────────────────────┼────────────────────┘
                             │
                    ┌────────▼────────┐
                    │ Product Teams   │
                    │ (Customers)     │
                    └─────────────────┘
```

---

## Scaling Guidelines

| Team Size | Platform Engineers | PM | SRE | Manager |
|-----------|-------------------|-----|-----|---------|
| Small (3-5) | 3-4 | 0.5 | 0 | 0.5 (Tech Lead) |
| Medium (6-12) | 6-8 | 1 | 1 | 1 |
| Large (13-25) | 12-18 | 2 | 2-3 | 2 |
| Enterprise (25+) | 20+ | 3+ | 4+ | 3+ (Director) |

---

## Anti-Patterns to Avoid

❌ **Ticket Takers**: Platform team just processes requests
✅ **Product Mindset**: Platform team builds products for developers

❌ **Gatekeepers**: Platform team blocks deployments
✅ **Enablers**: Platform team accelerates deployments

❌ **Ivory Tower**: Platform team builds without user input
✅ **Embedded**: Platform team works closely with product teams

❌ **Hero Culture**: One person knows everything
✅ **Distributed Knowledge**: Documentation, pairing, rotation
```

---

### 2. Platform Adoption Strategy

```markdown
# Platform Adoption Strategy: Target 70%

## Adoption Philosophy
Adoption is earned, not mandated. Build something developers love, and they'll use it.

---

## Current State Assessment

### Adoption Metrics
| Metric | Current | Target | Gap |
|--------|---------|--------|-----|
| Platform awareness | 60% | 95% | 35% |
| Platform trial | 30% | 80% | 50% |
| Platform adoption | 20% | 70% | 50% |
| Platform advocacy | 5% | 30% | 25% |

### Adoption Funnel
```
Awareness (60%) → Trial (30%) → Adoption (20%) → Advocacy (5%)
                   ↓             ↓                ↓
              "What is it?"  "Does it work?"  "I love it!"
```

---

## Adoption Strategy Pillars

### Pillar 1: Make It Easy (Reduce Friction)

**Goal**: Zero-friction getting started

**Tactics**:
- [ ] One-command getting started: `platform init`
- [ ] Pre-configured templates for common stacks
- [ ] No approval required for non-prod environments
- [ ] Self-service everything (no tickets)

**Success Metric**: Time to first value <15 minutes

---

### Pillar 2: Make It Valuable (Solve Real Problems)

**Goal**: Platform solves top developer pain points

**Top Pain Points (from research)**:
1. Environment setup takes days (solve with: instant provisioning)
2. Deployment is manual and scary (solve with: automated pipelines)
3. Can't find documentation (solve with: developer portal)
4. Security blocks deployments (solve with: shift-left security)

**Success Metric**: Developer NPS >50

---

### Pillar 3: Make It Visible (Build Awareness)

**Goal**: Every developer knows about platform capabilities

**Tactics**:
- [ ] Monthly platform newsletter
- [ ] Quarterly platform demo days
- [ ] Slack channel with active engagement
- [ ] Internal conference talks
- [ ] Success story spotlights

**Success Metric**: 95% awareness

---

### Pillar 4: Make It Social (Leverage Champions)

**Goal**: Developers sell platform to developers

**Champion Program**:
- Identify 10-15 early adopter champions
- Provide early access to new features
- Create champion Slack channel
- Monthly champion sync meetings
- Recognition and swag for contributions

**Champion Activities**:
- Answer questions in Slack
- Present at team meetings
- Write blog posts / documentation
- Provide feedback on roadmap

**Success Metric**: 30% of adoption from peer referral

---

### Pillar 5: Make It Required (Strategic Mandates)

**Goal**: Platform is the paved path for key scenarios

**Strategic Mandates** (use sparingly):
- All new services MUST use standard CI/CD
- All production deployments MUST go through platform
- All services MUST be registered in Cortex catalog

**Important**: Only mandate after platform is proven and loved

**Success Metric**: 100% compliance for mandated scenarios

---

## Adoption Phases

### Phase 1: Foundation (Month 1-3)
**Focus**: Early adopters and champions
**Target**: 20% adoption

| Activity | Owner | Timeline |
|----------|-------|----------|
| Identify 15 champions | PM | Week 1-2 |
| Launch champion program | PM | Week 3 |
| Deploy MVP platform | Engineering | Week 4-8 |
| Onboard 5 pilot teams | PM + Eng | Week 8-12 |

---

### Phase 2: Growth (Month 4-6)
**Focus**: Broader team adoption
**Target**: 50% adoption

| Activity | Owner | Timeline |
|----------|-------|----------|
| Platform demo days | PM | Monthly |
| Self-service documentation | Eng | Ongoing |
| Champion office hours | Champions | Weekly |
| Success story campaign | PM | Bi-weekly |

---

### Phase 3: Scale (Month 7-12)
**Focus**: Organization-wide adoption
**Target**: 70% adoption

| Activity | Owner | Timeline |
|----------|-------|----------|
| Executive mandate (new services) | Leadership | Month 7 |
| Migration support for legacy | Eng | Ongoing |
| Advanced features rollout | Eng | Quarterly |
| Platform as default | Leadership | Month 10 |

---

## Resistance Handling

### Common Objections

| Objection | Response | Tactic |
|-----------|----------|--------|
| "Works fine for me" | Show time savings data | Demo, pilot |
| "Too busy to learn" | Reduce learning curve | Templates, docs |
| "Don't trust platform" | Prove reliability | SLOs, transparency |
| "Doesn't fit my stack" | Add support | Prioritize in backlog |
| "Had bad experience" | Address specific issue | 1:1 follow-up |

---

## Adoption Dashboard

Track weekly:
- New teams onboarded
- Services on platform
- Developer NPS (monthly)
- Time to first deploy
- Support ticket volume
- Champion activity
```

---

### 3. Developer Experience Assessment

```markdown
# Developer Experience Assessment: Full Scope

## Assessment Framework

### DevEx Dimensions (SPACE Framework)

| Dimension | What It Measures |
|-----------|------------------|
| **S**atisfaction | How developers feel about their work |
| **P**erformance | Outcomes and impact of developer work |
| **A**ctivity | What developers actually do |
| **C**ommunication | How developers collaborate |
| **E**fficiency | Flow and productivity |

---

## Assessment Results

### Overall DevEx Score: 62/100 (Needs Improvement)

| Dimension | Score | Rating |
|-----------|-------|--------|
| Satisfaction | 58 | ⚠️ Needs Work |
| Performance | 70 | ✅ Good |
| Activity | 65 | ✅ Good |
| Communication | 68 | ✅ Good |
| Efficiency | 50 | ❌ Poor |

---

### Satisfaction Deep Dive (Score: 58)

| Factor | Score | Insight |
|--------|-------|---------|
| Tool satisfaction | 52 | "Tools are outdated and fragmented" |
| Process satisfaction | 55 | "Too much bureaucracy to deploy" |
| Team satisfaction | 78 | "My team is great" |
| Work-life balance | 60 | "On-call is stressful" |
| Career growth | 55 | "Limited learning opportunities" |

**Key Pain Points**:
1. CI/CD pipeline unreliable (45% satisfaction)
2. Documentation hard to find (40% satisfaction)
3. Environment setup painful (35% satisfaction)

---

### Efficiency Deep Dive (Score: 50)

| Factor | Score | Insight |
|--------|-------|---------|
| Build time | 45 | Average build: 18 minutes |
| Deploy time | 40 | Average deploy: 45 minutes |
| Environment time | 30 | New env setup: 2-3 days |
| Feedback loop | 55 | Test results: 20 minutes |
| Context switching | 60 | 3-4 tools for one task |

**Flow Killers** (interruptions per day):
- Slack notifications: 47
- Meetings: 4.2
- Context switches: 8.5
- Incidents: 0.8

---

### Benchmarks

| Metric | Our Score | Industry Avg | Best-in-Class |
|--------|-----------|--------------|---------------|
| DevEx Score | 62 | 65 | 85+ |
| Developer NPS | +12 | +20 | +50 |
| Deployment Frequency | Weekly | Daily | On-demand |
| Lead Time | 5 days | 2 days | <1 hour |
| Change Failure Rate | 15% | 10% | <5% |

---

## Recommendations

### Quick Wins (1-2 months)
| Action | Impact | Effort | Owner |
|--------|--------|--------|-------|
| Fix CI pipeline reliability | High | Low | Platform |
| Improve documentation search | Medium | Low | DevRel |
| Reduce meeting load | Medium | Low | Managers |

### Strategic Investments (3-6 months)
| Action | Impact | Effort | Owner |
|--------|--------|--------|-------|
| Self-service environments | High | High | Platform |
| Developer portal | High | Medium | Platform |
| Build time optimization | Medium | Medium | Platform |

### Culture Changes (6-12 months)
| Action | Impact | Effort | Owner |
|--------|--------|--------|-------|
| Engineering excellence program | High | High | Engineering |
| Reduce toil rotation | Medium | Medium | SRE |
| Learning time allocation | Medium | Low | Managers |

---

## Action Plan

### Priority 1: Self-Service Environments
**Problem**: 2-3 days to set up development environment
**Solution**: Cloud development environments (Coder)
**Expected Impact**: +15 DevEx points

### Priority 2: Developer Portal
**Problem**: Documentation fragmented across 12 systems
**Solution**: Unified portal with search (Backstage/Cortex)
**Expected Impact**: +10 DevEx points

### Priority 3: CI/CD Reliability
**Problem**: 45% satisfaction with CI/CD
**Solution**: Pipeline standardization, better observability
**Expected Impact**: +8 DevEx points

---

## Measurement Plan

| Metric | Frequency | Method | Target |
|--------|-----------|--------|--------|
| DevEx Survey | Quarterly | Survey | +10 points/quarter |
| Developer NPS | Quarterly | Survey | +50 by EOY |
| DORA Metrics | Weekly | Automated | Elite tier |
| Support Tickets | Weekly | ServiceNow | -40% |
| Tool Satisfaction | Monthly | Pulse survey | 80% |
```

---

### 4. Engineering Culture Playbook

```markdown
# Platform Engineering Culture Playbook

## Culture Vision
A culture where platform engineers are empowered to build with ownership, collaborate with empathy, and continuously improve.

---

## Core Values

### 1. Developer Empathy
**Principle**: We succeed when developers succeed.

**Behaviors**:
- Sit with product teams to understand their pain
- Respond to developer questions within 4 hours
- Never say "that's not a platform issue" without helping find the right owner
- Celebrate when developers ship faster

**Anti-patterns**:
- ❌ "RTFM"
- ❌ "That's not how you're supposed to use it"
- ❌ Building features without user input

---

### 2. Operational Excellence
**Principle**: We run what we build, and we build it to run.

**Behaviors**:
- All platform services have SLOs
- Blameless postmortems for every incident
- Automate toil before it becomes a burden
- On-call rotation is fair and sustainable

**Anti-patterns**:
- ❌ "The SRE team handles ops"
- ❌ Ignoring alerts
- ❌ Manual processes "because it's faster"

---

### 3. Continuous Improvement
**Principle**: We're never done learning or improving.

**Behaviors**:
- 20% time for learning and experiments
- Monthly team retrospectives
- Celebrate failures that teach us something
- Share knowledge through docs, talks, pairing

**Anti-patterns**:
- ❌ "We've always done it this way"
- ❌ Hoarding knowledge
- ❌ Blaming individuals for systemic issues

---

### 4. Transparent Communication
**Principle**: Share early, share often, share openly.

**Behaviors**:
- Public roadmap updated monthly
- Incidents communicated in real-time
- Decisions documented with rationale
- Feedback welcome at all levels

**Anti-patterns**:
- ❌ Hiding problems until they explode
- ❌ Making decisions in private
- ❌ "Need to know" culture

---

## Rituals and Practices

### Daily
| Practice | Purpose | Duration |
|----------|---------|----------|
| Async standup (Slack) | Visibility, blockers | 5 min |
| Pairing sessions | Knowledge sharing | Varies |

### Weekly
| Practice | Purpose | Duration |
|----------|---------|----------|
| Team sync | Alignment, decisions | 30 min |
| Office hours | Developer support | 1 hour |
| Demo Friday | Celebrate progress | 30 min |

### Monthly
| Practice | Purpose | Duration |
|----------|---------|----------|
| Retrospective | Continuous improvement | 1 hour |
| Platform demo day | Awareness, feedback | 1 hour |
| 1:1s (manager) | Career development | 30 min |

### Quarterly
| Practice | Purpose | Duration |
|----------|---------|----------|
| OKR review | Strategy alignment | 2 hours |
| Team offsite | Bonding, vision | 1 day |
| DevEx survey | Measure progress | Ongoing |

---

## Communication Norms

### Slack Guidelines
- **#platform-support**: User questions (SLA: 4 hours)
- **#platform-team**: Team discussions
- **#platform-incidents**: Real-time incident updates
- **#platform-wins**: Celebrate successes

### Meeting Guidelines
- Default to async; meet only when necessary
- Meetings have agendas and notes
- Decisions documented in Slack or Confluence
- No meetings on Focus Fridays

### Documentation Standards
- Every feature has user-facing docs
- Architecture decisions in ADRs
- Runbooks for all on-call scenarios
- Keep docs updated (quarterly review)

---

## Psychological Safety

### Creating Safety
- Leaders admit mistakes publicly
- "I don't know" is an acceptable answer
- Questions are encouraged, not judged
- Failure is a learning opportunity

### Safety Check-In Questions
Ask in retrospectives:
1. "Did anyone feel uncomfortable raising a concern this sprint?"
2. "Did anyone hold back an idea because they feared judgment?"
3. "Did anyone feel blamed for something outside their control?"

### Escalation Path
If someone feels unsafe:
1. Talk to manager
2. Talk to skip-level manager
3. Talk to HR partner
4. Anonymous feedback form

---

## Recognition and Celebration

### Recognition Types
| Type | Frequency | Method |
|------|-----------|--------|
| Shout-outs | Daily | Slack #platform-wins |
| Kudos | Weekly | Team sync |
| Spot bonus | Quarterly | Manager discretion |
| Promotion | Annual | Performance cycle |

### What We Celebrate
- Shipping features that improve DevEx
- Helping a team solve a hard problem
- Reducing toil through automation
- Great postmortem and learning
- Mentoring and knowledge sharing
```

---

### 5. Leadership Principles

```markdown
# Platform Engineering Leadership Principles

## Principle 1: Lead with Empathy
**Statement**: Understand the humans—developers, team members, stakeholders—before solving the technology.

**In Practice**:
- Start every project by talking to users
- Ask "how does this affect people?" before "how does this affect systems?"
- Create psychological safety for your team
- Celebrate the person, not just the work

**Questions to Ask**:
- "What is the developer experience like for someone using this?"
- "How is my team feeling about this project?"
- "Who might be negatively affected by this decision?"

---

## Principle 2: Enable, Don't Gatekeep
**Statement**: Our job is to make developers faster, not to control them.

**In Practice**:
- Default to self-service over approval processes
- Build guardrails, not gates
- Trust developers to make good decisions
- Provide escape hatches when needed

**Questions to Ask**:
- "Does this require approval, or can we make it self-service?"
- "Are we blocking developers or enabling them?"
- "What's the cost of removing this control vs. keeping it?"

---

## Principle 3: Measure What Matters
**Statement**: If we're not measuring developer experience, we're guessing.

**In Practice**:
- Track DORA metrics for delivery performance
- Survey developers quarterly on satisfaction
- Monitor platform adoption and usage
- Tie platform work to business outcomes

**Questions to Ask**:
- "How do we know this is working?"
- "What would success look like in numbers?"
- "Are we measuring outputs or outcomes?"

---

## Principle 4: Build for Adoption
**Statement**: A feature not adopted is a feature not delivered.

**In Practice**:
- Involve users in design and testing
- Optimize for ease of use, not just functionality
- Create migration paths, not big-bang rollouts
- Make the new way easier than the old way

**Questions to Ask**:
- "Will developers actually use this?"
- "What's the adoption friction?"
- "How do we make the right thing the easy thing?"

---

## Principle 5: Own the Outcome
**Statement**: We're not done when we ship; we're done when developers are successful.

**In Practice**:
- Run what you build
- Monitor adoption and satisfaction post-launch
- Follow up on feedback and issues
- Continuously iterate and improve

**Questions to Ask**:
- "What happens after we ship?"
- "How will we know if this is successful?"
- "What's our plan if adoption is low?"

---

## Principle 6: Influence Without Authority
**Statement**: We lead through trust and value, not org charts.

**In Practice**:
- Build relationships before you need them
- Demonstrate value before asking for commitment
- Find allies and champions
- Use data to make the case

**Questions to Ask**:
- "Who do I need to influence to make this happen?"
- "What value can I provide to earn their trust?"
- "How do I make this their idea?"

---

## Principle 7: Simplify Ruthlessly
**Statement**: Complexity is the enemy of adoption and reliability.

**In Practice**:
- Say no to "nice to have" features
- Consolidate tools, don't accumulate
- Choose boring technology when possible
- Question every abstraction

**Questions to Ask**:
- "Can we remove something instead of adding?"
- "Is this complexity necessary?"
- "What's the simplest solution that works?"

---

## Applying Principles

### Decision Framework
When making decisions, ask:
1. Does this improve developer experience? (Empathy)
2. Does this enable or restrict? (Enable)
3. How will we measure success? (Measure)
4. Will developers actually use this? (Adoption)
5. How will we ensure long-term success? (Ownership)
6. Do we have buy-in from stakeholders? (Influence)
7. Is this the simplest solution? (Simplify)

### Example: Self-Service Database Provisioning

| Principle | Application |
|-----------|-------------|
| Empathy | Talked to 15 developers about provisioning pain |
| Enable | Self-service CLI, no approval for non-prod |
| Measure | Tracking provisioning time, adoption rate, NPS |
| Adoption | Designed with developers, started with pilot |
| Ownership | Platform team on-call for database service |
| Influence | Built champion program, got PM buy-in |
| Simplify | One CLI command, not 10 config files |
```

---

## Output Structure

```
platform-leadership/
├── team/
│   ├── structure.md
│   ├── hiring-guide.md
│   ├── career-ladder.md
│   └── onboarding-plan.md
├── adoption/
│   ├── strategy.md
│   ├── champion-program.md
│   └── adoption-metrics.md
├── devex/
│   ├── assessment.md
│   ├── improvement-plan.md
│   └── survey-templates.md
├── culture/
│   ├── playbook.md
│   ├── rituals.md
│   └── recognition.md
└── leadership/
    ├── principles.md
    ├── influence-playbook.md
    └── stakeholder-guide.md
```

---

## Integration with Agents

```bash
# Use with Strategy Agent
@strategy-agent "Align team structure with platform roadmap"

# Combine with Stakeholder Agent
@stakeholder-agent "Build influence strategy for VP Engineering"

# Work with Governance Agent
@governance-agent "Create platform team operating model"

# Coordinate with Delivery Agent
@delivery-agent "Plan team capacity for Q1 roadmap"
```

---

## Related Skills

- `/stakeholder-map` - Map platform stakeholders
- `/create-roadmap` - Platform roadmap planning
- `/exec-briefing` - Executive communication
- `/value-narrative` - Communicate platform value
- `/product-management` - Product-led platform thinking

---

## Related Agents

- `@stakeholder-agent` - Stakeholder engagement
- `@strategy-agent` - Platform strategy
- `@governance-agent` - Operating model
- `@delivery-agent` - Capacity planning
- `@risk-agent` - Team and delivery risks

---

## Best Practices

### 1. Product Mindset Over Project Mindset
Treat the platform as a product with users, not a project with tasks.

### 2. Developer-First, Always
Every decision should pass the "does this make developers faster?" test.

### 3. Build Trust Before Building Platform
Relationships and credibility enable platform adoption.

### 4. Measure Outcomes, Not Outputs
Track developer success, not just features shipped.

### 5. Embrace Boring Technology
Reliability and simplicity beat novelty and complexity.

---

**Skill Owner**: Platform Program Management Repository
**Last Updated**: January 2026
**Version**: 1.0
