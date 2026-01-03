# Skill: Value Narrative

## Description
Generate elegant, eloquent, and precise narratives that articulate product capabilities and the value they deliver. Transforms technical features into compelling business outcomes with crisp, executive-ready language.

## Usage
```bash
/value-narrative --capability "self-service-provisioning" --audience executive --format narrative
```

## Parameters

### Required
- `--capability` (string): Platform capability to describe (e.g., "developer-portal", "self-service-provisioning", "ci-cd-automation")

### Optional
- `--audience` (string): Target audience: "executive", "developer", "product", "sales", "board" (default: "executive")
- `--format` (string): Output format: "narrative", "value-prop", "elevator-pitch", "press-release" (default: "narrative")
- `--tone` (string): Writing tone: "inspiring", "confident", "data-driven", "transformational" (default: "confident")
- `--length` (string): Content length: "brief" (1 paragraph), "standard" (3-4 paragraphs), "comprehensive" (full page) (default: "standard")
- `--include-metrics` (boolean): Include quantified value metrics (default: true)

## Output Formats

### Narrative Format

```
═══════════════════════════════════════════════════════════
VALUE NARRATIVE: SELF-SERVICE PROVISIONING
═══════════════════════════════════════════════════════════

In the modern enterprise, velocity is victory. Every hour developers spend
waiting for infrastructure is an hour not spent building the features that
define your competitive edge. Self-service provisioning transforms this
fundamental constraint.

Where traditional approaches trap developers in multi-day approval cycles
and ticket queues, self-service provisioning delivers what developers need,
when they need it—in minutes, not days. Through intelligent automation and
thoughtful guardrails, teams provision environments, create services, and
access resources with a few clicks, while governance and security operate
seamlessly in the background.

The impact is immediate and measurable. Organizations see provisioning time
collapse from three days to ten minutes—a 99% reduction. But the real value
transcends speed: developers regain focus, teams ship faster, and the
organization unlocks the compounding returns of unblocked productivity. What
was once a bottleneck becomes a capability that scales with ambition.

This is infrastructure that accelerates innovation rather than impedes it.
Self-service provisioning doesn't just save time—it fundamentally redefines
what's possible when engineering teams operate without friction.
```

---

### Value Proposition Format

```
═══════════════════════════════════════════════════════════
VALUE PROPOSITION: DEVELOPER PORTAL
═══════════════════════════════════════════════════════════

THE CHALLENGE
-------------
Engineering organizations lose countless hours to fragmented tooling,
scattered documentation, and tribal knowledge. New developers spend weeks
ramping up. Experienced engineers spend hours hunting for APIs, searching
for runbooks, and navigating inconsistent workflows. This friction compounds
daily, eroding productivity and morale.

THE SOLUTION
------------
A unified developer portal serves as the single source of truth and gateway
to your platform's capabilities. One search bar. One catalog. One place for
everything developers need to be productive from day one.

THE VALUE
---------
• Productivity Reclaimed: Reduce documentation search time from 45 minutes
  to 2 minutes—a 96% improvement that returns hours to every developer,
  every week.

• Onboarding Accelerated: New developers deploy their first service in
  2 hours instead of 2 weeks, reaching productivity 10x faster.

• Knowledge Democratized: Self-service answers eliminate 80% of support
  tickets, freeing both developers and platform teams to focus on higher-value
  work.

• Consistency Delivered: Standardized workflows ensure every team follows
  best practices without requiring constant oversight or tribal knowledge.

THE OUTCOME
-----------
Organizations with developer portals report 40% higher developer productivity,
55-point improvements in developer satisfaction (NPS), and measurably faster
time-to-market. When developers spend time building instead of searching,
everyone wins.
```

---

### Elevator Pitch Format

```
═══════════════════════════════════════════════════════════
ELEVATOR PITCH: CI/CD AUTOMATION
═══════════════════════════════════════════════════════════

Imagine if your teams could deploy to production five times a day instead of
twice a week—with higher reliability, not lower. That's the power of modern
CI/CD automation.

By replacing manual deployments and fragmented pipelines with standardized,
automated workflows, we eliminate the deployment bottleneck that constrains
innovation. Developers commit code. Automation handles the rest: testing,
scanning, building, deploying. What once took 45 minutes now takes 3. What
once failed 15% of the time now succeeds 95% of the time.

The business impact? Teams ship features 25x faster. Time-to-market shrinks.
Competitive velocity increases. And developers—freed from deployment toil—
focus on what they do best: solving customer problems through great software.

This isn't just faster deployment. It's a fundamental shift in how quickly
you can respond to market opportunities and customer needs.
```

---

### Press Release Format (Amazon-style "Working Backwards")

```
═══════════════════════════════════════════════════════════
PRESS RELEASE: CONTAINER PLATFORM LAUNCH
═══════════════════════════════════════════════════════════

Platform Engineering Team Launches Kubernetes-Based Container Platform,
Delivering 99.9% Uptime and 10x Deployment Velocity for Engineering Teams

[CITY, DATE] — The Platform Engineering team today announced the general
availability of its Kubernetes-based container platform, enabling all
engineering teams to deploy, scale, and operate services with unprecedented
reliability and speed.

The new platform replaces manually-managed EC2 infrastructure with a
modern, automated approach that handles deployment, scaling, and recovery
autonomously. Early adopter teams report deployment times dropping from
45 minutes to 3 minutes, while service uptime has improved from 97.5% to
99.9%—a tenfold reduction in downtime.

"We've fundamentally changed how quickly teams can deliver value to customers,"
said [Platform Lead]. "What used to require manual coordination and careful
timing now happens automatically and safely. Teams deploy when they're ready,
scale based on demand, and recover from failures in seconds instead of hours."

The platform serves all engineering teams across the organization, supporting
120 services in production. Key capabilities include:

• Automated Deployment: Push-button deployments with automated health checks
  and rollback
• Intelligent Scaling: Services automatically scale based on load, eliminating
  over-provisioning
• Self-Healing: Failed containers restart automatically, achieving 99.9% uptime
• Cost Optimization: Autoscaling reduces infrastructure costs by 60% while
  improving reliability

Engineering teams can now provision a new service and deploy to production
in minutes instead of days, removing what was historically a significant
constraint on innovation velocity. The platform handles operational complexity
behind standardized interfaces, allowing developers to focus on building
features rather than managing infrastructure.

"This is infrastructure that gets out of the way," added [VP Engineering].
"Our developers spend time solving customer problems, not fighting deployment
pipelines. That's exactly where we want their talent focused."

The platform is now available to all engineering teams with comprehensive
documentation, self-service onboarding, and dedicated support channels.

About the Platform Engineering Team
The Platform Engineering team builds and operates the foundational capabilities
that power innovation across the engineering organization, serving 200 developers
across 50 teams.

###

For more information, visit [developer portal URL] or contact [team].
```

---

## Capability Templates

### Template: Self-Service Provisioning

**Narrative (Executive Audience)**:
> Infrastructure should never be the reason innovation waits. Self-service
> provisioning transforms a three-day approval process into a ten-minute
> automated workflow, returning hundreds of hours to engineering teams while
> maintaining the governance and security controls that keep the organization
> safe. This isn't just faster provisioning—it's the foundation for operating
> at a pace that matches market opportunity.

**Key Value Points**:
- Speed: 3 days → 10 minutes (99% faster)
- Developer autonomy without sacrificing governance
- Compounds across every team, every project
- Eliminates ticket queues and approval bottlenecks

---

### Template: Developer Portal

**Narrative (Executive Audience)**:
> Knowledge should be discoverable, not hidden in wikis and heads. A developer
> portal creates a single source of truth where every API, every service, every
> runbook lives in one searchable, navigable space. New developers become
> productive in hours instead of weeks. Experienced developers find answers in
> seconds instead of Slack threads. The result: an organization that moves
> faster because information flows freely.

**Key Value Points**:
- Onboarding: 2 weeks → 2 hours (10x faster)
- Search: 45 minutes → 2 minutes (96% faster)
- Reduced cognitive load and context switching
- Self-service answers eliminate support burden

---

### Template: CI/CD Automation

**Narrative (Executive Audience)**:
> Deployment should be mundane, not momentous. When deployment is automated,
> tested, and reliable, teams ship continuously instead of batching risk into
> infrequent releases. This transforms deployment from a high-stakes event
> requiring cross-team coordination into a routine operation that happens
> dozens of times per day. The competitive advantage: your organization's
> ability to respond to customers and markets at the speed of code commits.

**Key Value Points**:
- Frequency: 2/week → 5/day (25x increase)
- Reliability: 85% → 95% success rate
- Time: 45 minutes → 3 minutes per deployment
- Risk reduction through smaller, incremental changes

---

### Template: Container Platform (Kubernetes)

**Narrative (Executive Audience)**:
> Infrastructure should be resilient by default, not fragile by design. A
> container platform treats failures as inevitable and recovers automatically,
> achieving 99.9% uptime without heroic manual intervention. Services scale
> based on demand, optimizing costs while ensuring performance. Deployments
> happen safely through automated health checks and instant rollbacks. This
> is infrastructure that operates itself, freeing teams to focus on customers
> instead of servers.

**Key Value Points**:
- Uptime: 97.5% → 99.9% (10x reliability improvement)
- Recovery: 2 hours → 5 minutes (automated self-healing)
- Cost: 60% reduction through autoscaling
- Operational overhead: 3 FTE → 0.5 FTE

---

### Template: Observability Stack

**Narrative (Executive Audience)**:
> You can't fix what you can't see. Unified observability transforms debugging
> from a hours-long archaeology expedition through scattered logs into a
> minutes-long investigation with comprehensive context. When every service
> reports metrics, logs, and traces to a single system, teams identify and
> resolve issues before customers notice. Mean time to recovery drops from
> hours to minutes. Customer-impacting incidents decrease. Engineering teams
> operate with confidence instead of uncertainty.

**Key Value Points**:
- MTTR: 2 hours → 15 minutes (87% faster recovery)
- Visibility: 100% service coverage
- Proactive alerting prevents incidents
- Unified view eliminates tool-switching

---

### Template: Security Baseline

**Narrative (Executive Audience)**:
> Security should be embedded, not bolted on. An automated security baseline
> ensures every service meets compliance requirements from day one, without
> slowing teams down. Secret scanning, vulnerability detection, and access
> controls operate continuously and automatically. The result: zero critical
> vulnerabilities in production, SOC 2 compliance maintained effortlessly, and
> security teams focused on strategic threats instead of routine reviews.

**Key Value Points**:
- Zero critical vulnerabilities in production
- Automated compliance (SOC 2, etc.)
- Secrets management eliminates credential leaks
- Security gates integrated into deployment pipeline

---

## Writing Principles

### Principle 1: Lead with Value, Not Features

❌ **Feature-Focused**:
"Our developer portal has a service catalog, API explorer, and documentation hub."

✅ **Value-Focused**:
"When developers find what they need in seconds instead of hours, they spend
time building instead of searching. A unified developer portal delivers this
transformation."

---

### Principle 2: Quantify Impact

❌ **Vague**:
"Self-service provisioning makes developers more productive."

✅ **Quantified**:
"Self-service provisioning reduces environment provisioning from three days to
ten minutes, returning 200+ hours per month to engineering teams."

---

### Principle 3: Connect to Business Outcomes

❌ **Technical**:
"Kubernetes provides container orchestration with automated scaling."

✅ **Business-Oriented**:
"Container orchestration eliminates over-provisioning, reducing infrastructure
costs by 60% while improving uptime to 99.9%. Teams deploy faster, operate
cheaper, and scale effortlessly."

---

### Principle 4: Use Concrete Language

❌ **Abstract**:
"Our platform enables teams to leverage best practices."

✅ **Concrete**:
"Golden path templates give teams production-ready deployment pipelines in
minutes. No guesswork. No tickets. No waiting."

---

### Principle 5: Show Transformation

❌ **Static**:
"We have a CI/CD platform."

✅ **Transformative**:
"Where teams once deployed twice a week with 15% failures, they now deploy
five times a day with 95% success. This is how modern software organizations
operate."

---

## Examples by Audience

### For Executives (CTO, CEO, Board)

**Focus**: Business impact, competitive advantage, ROI
**Tone**: Confident, strategic, crisp
**Length**: Brief to standard (avoid technical depth)

**Example**:
> Platform engineering is how leading technology companies achieve velocity at
> scale. When infrastructure becomes self-service, teams ship faster. When
> deployment is automated, reliability improves. When observability is unified,
> incidents resolve in minutes. The cumulative effect: a 40% improvement in
> developer productivity and measurably faster time-to-market. This is the
> foundation for competing on engineering velocity.

---

### For Developers

**Focus**: Developer experience, productivity, pain point resolution
**Tone**: Empathetic, practical, precise
**Length**: Standard to comprehensive

**Example**:
> Remember the last time you spent three hours debugging a production issue
> because logs were scattered across five different systems? Or waited three
> days for a database to be provisioned? Those frustrations are solved problems
> in a well-designed platform. Unified observability gives you the full context
> in seconds. Self-service provisioning gives you what you need in minutes.
> This is infrastructure designed for how you actually work.

---

### For Product Managers

**Focus**: Time-to-market, feature velocity, customer impact
**Tone**: Collaborative, outcome-oriented
**Length**: Standard

**Example**:
> When engineering teams deploy five times a day instead of twice a week, your
> features reach customers 25x faster. When developers aren't blocked waiting
> for infrastructure, sprint velocity increases. When deployment is reliable,
> you ship with confidence. A modern platform doesn't just make engineers
> happy—it directly accelerates your ability to deliver value to customers and
> respond to market opportunities.

---

### For Sales/Business Development

**Focus**: Competitive differentiation, customer value, market positioning
**Tone**: Compelling, customer-centric
**Length**: Brief to standard

**Example**:
> Our engineering velocity is a competitive advantage you can sell. When
> customers request features, we ship in days instead of months. When markets
> shift, we adapt faster than competitors. When bugs appear, we fix them in
> hours, not weeks. This responsiveness is powered by world-class platform
> engineering. It's infrastructure you'll never see, but capabilities your
> customers will notice every day.

---

## Integration with Agents

This skill works seamlessly with platform agents:

```bash
# Generate value narrative via Communication Agent (if created)
@communication-agent "Create an executive value narrative for our self-service provisioning capability"

# Or invoke skill directly
/value-narrative --capability "self-service-provisioning" --audience executive --format narrative

# For board presentation
/value-narrative --capability "developer-portal" --audience board --format elevator-pitch --length brief

# For product marketing
/value-narrative --capability "ci-cd-automation" --audience sales --format value-prop --include-metrics true
```

---

## Best Practices

1. **Start with Impact**: Lead with what changes, not what exists
2. **Use Active Voice**: "Teams deploy" not "Deployments are made"
3. **Choose Precision**: "99.9% uptime" not "high availability"
4. **Avoid Jargon**: Kubernetes → container orchestration (when needed)
5. **Tell Stories**: Show before/after transformation
6. **Quantify Everything**: Numbers anchor value in reality

---

## Common Pitfalls

❌ **Feature Lists**: Listing capabilities without explaining value
❌ **Passive Voice**: "It can be deployed" vs "Teams deploy"
❌ **Vague Claims**: "Improved productivity" vs "40% productivity increase"
❌ **Technical Jargon**: Using acronyms without context
❌ **Missing Narrative**: Facts without a story

---

## Related Skills

- `/exec-briefing` - Executive status reports
- `/stakeholder-map` - Tailor narratives to stakeholders
- `/create-roadmap` - Strategic narratives for roadmaps

---

## Related Agents

- `@strategy-agent` - Strategic narrative development
- `@stakeholder-agent` - Audience-specific messaging
- `@governance-agent` - Executive communication

---

## Implementation Notes

This skill applies principles from:
- Amazon's "Working Backwards" press release format
- Executive communication best practices
- Value proposition frameworks (Geoffrey Moore's positioning)
- Data-driven storytelling

The skill generates narratives that work equally well in:
- Executive presentations
- Board decks
- Business cases
- Product marketing
- Internal communications
- Customer-facing materials

---

**Skill Owner**: Platform Program Management Repository
**Last Updated**: January 2026
**Version**: 1.0
