# Cortex.io IDP Implementation - Program Plan

> Comprehensive reference document for the Platform as a Product initiative at Fiserv

---

## Executive Summary

### Investment & Value Proposition

| Metric | Value |
|--------|-------|
| **Investment** | $20 Million (Labor Capital & Licenses) |
| **License Allocation** | 1,000 Coder seats, 500 Cortex seats |
| **Addressable Value** | $1 Billion+ |
| **Production Applications** | 1,690 |
| **Selling Points** | Stability, Quality, Efficiency, Velocity, Trust, Resilience |

**Vision Statement:**
> "A $20 million investment in labor capital and initial license procurement (1,000 Coder seats, 500 Cortex seats) establishes the manufacturing capability to address $1 Billion+ in cognitive load from context switching, opportunity cost, and redundant efforts in collecting and visualizing data across our engineering organization. We are delivering stability, quality, efficiency, velocity, trust, and resilience."

**Goal:** Create a platform that abstracts complexity so developers focus on features, not friction — with fully automated pipelines, policy-as-code guardrails, and resilience built in from day one. **Frictionless by Design. Compliant by Default. Resilient at Core.**

### The Problem We're Solving

- **30+ Disconnected Tools**
- **40 Panes of Glass**
- **Cognitive Load and Tool Sprawl**

### The Solution: Flight Deck Platform

Three integrated platform products delivering unified developer experience:

---

## Platform Products

### 1. Cortex (IDP) - The Unified Flight Deck
**Type:** Internal Developer Platform

**Key Capabilities:**
- Software Component Catalog — Single source of truth for every service, API, database
- Health Scorecards & Trust Signals — Real-time security, compliance, reliability status
- Global Observability Nexus — Unified logs, metrics, traces view
- Engineering Intelligence Dashboards — DORA metrics, scorecard trends
- Leadership Dashboards — Executive reports, initiative tracking

### 2. Coder (CDE) - Cloud Development Environment
**Type:** Cloud Development Environment

**Key Capabilities:**
- Instant dev environment provisioning
- Pre-configured IDE templates
- Integrated with Cortex catalog
- Secure cloud workspaces

### 3. Kratix (IDP) - Platform Orchestrator
**Type:** Platform Orchestrator

**Key Capabilities:**
- Multi-cluster deployment (AKS/EKS)
- Golden path promises
- Harness CD integration
- Self-service infrastructure
- Known/Unknown namespace promises

---

## Implementation Phases

### Phase 0: Prerequisites (Foundation)

#### Contract Checklist
| Task | Status |
|------|--------|
| VEQ (Vendor Evaluation Questionnaire) | ✅ Complete |
| SaaS Review | ⬜ Pending |
| AI Review | ⬜ Pending |
| Purchase Request | ✅ Complete |
| MSA (Master Service Agreement) | ⬜ Pending |
| Contract Executed | ⬜ Pending |

#### Infrastructure Setup
| Task | Status |
|------|--------|
| Install Axion Relay | ✅ Complete |
| Network & Connectivity Setup | ⬜ Pending |
| Install Cortex.io App | ⬜ Pending |

#### Platform Orchestration
| Task | Status |
|------|--------|
| Kratix Integration with Harness | ✅ Complete |
| AKS Cluster Deployment (Azure) | ✅ Complete |
| Kratix Promise — Known Namespace | ✅ Complete |
| Kratix Promise — Unknown Namespace | ✅ Complete |

#### Development Environment
| Task | Status |
|------|--------|
| Coder — Cloud Dev Environment | ⬜ Pending |
| Coder + Cortex.io Integration | ⬜ Pending |
| CI Build Tools & Dependencies | ⬜ Pending |

#### Data Ingestion — CI/CD/CV Tools
| Tool | Purpose | Status |
|------|---------|--------|
| GitHub | Source Control | ⬜ Pending |
| GitLab | Source Control | ⬜ Pending |
| Nexus | Artifact Repository | ⬜ Pending |
| Fortify | Security Scanning (SAST) | ⬜ Pending |
| Sonatype | Dependency Analysis (SCA) | ⬜ Pending |
| Harness | CI/CD Pipeline | ⬜ Pending |
| SonarQube | Code Quality Analysis | ⬜ Pending |
| Dynatrace | Application Performance Monitoring | ⬜ Pending |
| Splunk | Log Management & Analytics | ⬜ Pending |
| ServiceNow | IT Service Management | ⬜ Pending |
| KatanaDB | Database Management | ⬜ Pending |

---

### Phase 1: PoV Workshop

#### Test Scenarios
| Scenario | Description | Status |
|----------|-------------|--------|
| Java/SpringBoot Demo App | Simulated application for PoV | ⬜ Pending |
| One-Touch Assembly → Launch Control & Verify | Platform engineering workflow | ⬜ Pending |
| Greenfield Test | New project deployment scenario | ⬜ Pending |
| Brownfield Test | Existing application migration | ⬜ Pending |

#### Deliverables
| Deliverable | Description | Status |
|-------------|-------------|--------|
| Scorecards | Production readiness validation (Bronze/Silver/Gold) | ⬜ Pending |
| Engineering Intelligence | DORA metrics, scorecard trends, service analytics | ⬜ Pending |
| Leadership Dashboards | Executive reports, initiative tracking | ⬜ Pending |

#### Scorecards to Validate
1. Production Readiness — Deployment criteria, documentation, ownership
2. Onboarding Scorecard — Required onboarding steps
3. Security Standards — Fortify SAST, Sonatype SCA
4. Service Maturity — Observability, reliability, documentation
5. Velocity Scorecard — DORA metrics

#### Initiatives to Track
1. **Marshall Plan** — Code quality coverage <80%
2. **AppSec SCM Policy Compliance** — GitHub/GitLab security policy adherence

---

### Phase 2: Production Pilot

#### Production Deployment
| Task | Status |
|------|--------|
| Real Java Application | ⬜ Pending |
| EKS Cluster Deployment (AWS) | ⬜ Pending |
| Complete All Integrations | ⬜ Pending |
| Kratix Promises for EKS | ⬜ Pending |

---

### Scale Phase: Enterprise Rollout

#### Mission Critical Application Coverage

| Tier | Applications | Description |
|------|--------------|-------------|
| MC-1 | 85 | Highest criticality — Core banking & payment systems |
| MC-2 | 245 | High criticality — Essential business operations |
| MC-3 | 520 | Medium criticality — Supporting services |
| MC-4 | 840 | Standard criticality — Internal & development tools |
| **Total** | **1,690** | **Production Applications** |

#### Scale Activities
- MC-2 Application Coverage
- Business Unit Expansion
- Additional Kratix Promises
- Champions Program
- Enterprise License Agreement
- Full Organization Coverage

---

## Workflows

### One-Touch Assembly → Launch Control & Verify

**Purpose:** Automated service onboarding and validation workflow using Cortex's drag-and-drop block orchestrator with 200+ integration-aware components.

#### One-Touch Assembly Blocks
| Block | Action |
|-------|--------|
| User Input Block | Collect service metadata (name, team, domain, owner, GitHub username) |
| Scaffolder Block | Generate repository from Cookiecutter templates with cortex.yaml descriptor |
| GitHub/GitLab Block | Create repo, branch protection, team permissions, trigger workflow |
| Harness Block | Provision CI/CD pipeline from template |
| PagerDuty Block | Create service entry, assign escalation policy |
| Jira Block | Create project board, link work items for initiative tracking |

#### Launch Control & Verify Blocks
| Block | Action |
|-------|--------|
| Branch Block | Conditional paths (greenfield vs brownfield) using CEL expressions |
| Jenkins/Harness Block | Trigger CI build, run security scans (Fortify, Sonatype, SonarQube) |
| Manual Approval Block | Require Platform Engineer sign-off |
| Scorecard Trigger | Execute CQL rules, validate Bronze level achievement |
| Slack Block | Send notification with score results |
| ServiceNow Block | Create change record for onboarding completion |

**Reference:** https://app.demo.cortex.io/admin/workflows

---

## Stakeholders

### Enterprise Stakeholders
- C-Suite Sponsors — Executive visibility & strategic direction
- Business Unit Leaders — Business requirements & prioritization
- Finance & Procurement — Budget approval & vendor management
- Security & Compliance — Risk assessment & policy alignment
- Legal & Contracts — MSA negotiation & contract execution

### Platform Engineering Stakeholders
| Role | Count | Responsibility |
|------|-------|----------------|
| Executive Sponsor | 1 | Strategic vision & executive advocacy |
| Co-Program Sponsors | 2 | Program governance & cross-team coordination |
| Platform Engineering VPs | — | Technical strategy & resource allocation |
| Co-Product Leads | 2 | Product roadmap & feature prioritization |
| Co-Engineering Leads | 2 | Technical implementation & delivery |

### Developer Teams Stakeholders
- Engineering Directors — Team alignment & adoption strategy
- Engineering Managers — Team enablement & feedback loops
- Tech Leads — Technical guidance & best practices
- Software Engineers — Primary platform users & advocates
- QA Engineers — Quality validation & testing workflows

---

## Communications Plan

### Regular Cadence
| Frequency | Communication | Audience |
|-----------|---------------|----------|
| Weekly | Platform Engineering Stand-up | Platform Engineering Team |
| Bi-Weekly | Stakeholder Sync | Program Sponsors, Product & Engineering Leads |
| Monthly | Executive Steering Committee | Executive Sponsor, VPs, C-Suite |
| Monthly | Platform Newsletter | All Engineering Teams |
| Quarterly | All-Hands Town Hall | All Engineering Organization |

### Key Milestone Communications
| Event | Communication Actions |
|-------|----------------------|
| Contract Executed | Executive Email, Slack Announcement |
| PoV Workshop Complete | Demo Day, Case Study |
| Pilot Success / License Expansion | Exec Briefing, Business Case |
| Early Adopter Onboarding | Training Sessions, Office Hours |
| MC-2 Coverage Milestone | Success Metrics, Town Hall |
| Enterprise License Agreement | ROI Report, Exec Approval |
| Business Unit Expansion | BU Kickoffs, Champions Program |

### Adoption Scaling Milestones
| Phase | Target | Services |
|-------|--------|----------|
| Phase 1 | PoV Workshop | 1-5 |
| Phase 2 | Pilot / Early Adopters | 10-25 |
| Phase 3 | MC-2 Coverage | 50-100 |
| Phase 4 | Enterprise Scale | 500+ |

---

## Release Notes Summary

### Phase 0 Releases
- **v0.1.0** (Milestone) — Contract Execution
- **v0.2.0** (Major) — Infrastructure Foundation
- **v0.3.0** (Minor) — Platform Orchestration Setup
- **v0.4.0** (Minor) — Dev Environment & Data Ingestion

### Phase 1 Releases
- **v1.0.0** (Milestone) — PoV Workshop Kickoff
- **v1.1.0** (Minor) — Test Scenarios Complete
- **v1.2.0** (Major) — Scorecards & Intelligence Dashboards
- **v1.3.0** (Milestone) — PoV Workshop Complete

### Phase 2 Releases
- **v2.0.0** (Major) — Production Pilot Launch
- **v2.1.0** (Minor) — Integration Completion & Training
- **v2.2.0** (Milestone) — Pilot Success / License Expansion Decision

### Scale Releases (Planned)
- **v3.0.0** — MC-2 Application Coverage (245 apps)
- **v3.1.0** (Milestone) — Enterprise License Agreement
- **v4.0.0** — Business Unit Expansion (MC-3: 520, MC-4: 840 apps)
- **v5.0.0** (Milestone) — Full Organization Coverage (1,690 apps)

---

## Reference Links

### Cortex.io Demo
| Resource | URL |
|----------|-----|
| Workflows | https://app.demo.cortex.io/admin/workflows |
| Scorecards | https://app.demo.cortex.io/admin/scorecards |
| Engineering Intelligence | https://app.demo.cortex.io/admin/eng-intelligence/dashboards |
| Executive Reports | https://app.demo.cortex.io/admin/reports/executive |

### Documentation
| Resource | URL |
|----------|-----|
| Cortex Workflows | https://docs.cortex.io/workflows |
| Workflow Blocks | https://docs.cortex.io/streamline/workflows/blocks |
| Scaffolder Templates | https://docs.cortex.io/streamline/workflows/scaffolder |

---

## Project Files

| File | Purpose |
|------|---------|
| `index.html` | Critical Path Roadmap (main dashboard) |
| `executive-summary.html` | Investment value proposition & Flight Deck overview |
| `capabilities.html` | Platform technology matrix (languages, pipelines, deployments, support layers) |
| `stakeholders.html` | Program stakeholders by category |
| `communications.html` | Communication cadence & milestone events |
| `roadmap.html` | Capability roadmap & MC tier coverage |
| `release-notes.html` | Versioned release notes by phase |
| `reference.html` | Platform technology reference (Cortex, Coder, Kratix, Platform Engineering tools) |
| `CRITICAL-PATH-WORKFLOW.md` | Markdown documentation with Mermaid diagrams |
| `plan.md` | This comprehensive reference document |
| `policy-as-code.html` | CD maturity practices with OPA/Rego policy samples |
| `cd-practices.json` | Minimum CD practice definitions (57 practices) |
| `risks.html` | Risk assessment and mitigation strategies |

---

## Fiserv Branding

| Color | Hex Code | Usage |
|-------|----------|-------|
| Fiserv Blue | #237cb8 | Primary accent, links, Phase 1 |
| Fiserv Orange | #ff6600 | Secondary accent, highlights, Phase 2 |
| Fiserv Black | #0e0e0e | Background |
| Fiserv Gray | #666666 | Phase 0, muted elements |

---

## Key Concepts

### Cortex-Synapse-Atlas Platform

| Component | Name | Function |
|-----------|------|----------|
| 🧠 Cortex | The Unified Flight Deck | Single pane of glass, service catalog, scorecards |
| ⚡ Synapse | One-Touch Assembly | Golden path templates, self-service provisioning |
| 🌐 Atlas | The Invisible Foundation | Universal abstraction, automated rollback/recovery |

### Golden Path / Paved Road
Pre-configured, secure-by-default pathways for developers to create and deploy services following best practices from day 0.

### CQL (Cortex Query Language)
Query language for building custom scorecards and rules in Cortex.io.

### Kratix Promises
Declarative platform contracts that define what resources can be provisioned and how they should be configured.

---

## Session Notes

### Session: January 2026 — Documentation Enhancement

#### New Pages Created

| Page | Purpose |
|------|---------|
| `reference.html` | Platform technology reference cards with architecture diagram |
| `capabilities.html` | Technology matrix placemat for stakeholder presentations |

#### Index Navigation Updates
- Added **Capabilities** button (right of Executive Summary)
- Added **Reference** button (right of Release Notes)

#### Reference Page (`reference.html`)
- Four technology cards: Coder, Cortex, Kratix, Platform Engineering Tools
- Architecture diagram showing product integration flow
- Product color coding standardized with roadmap.html:
  - Coder: `#10b981` (emerald green)
  - Cortex: `#237cb8` (Fiserv blue)
  - Kratix: `#8b5cf6` (purple)
- Card order: Coder → Cortex → Kratix (matching roadmap)

#### Capabilities Page (`capabilities.html`)
**5-Column Technology Matrix:**
| Column | Contents |
|--------|----------|
| Languages | Java, C#/.NET, Python, Go, NodeJS, Kotlin |
| Build Tools | Maven/Gradle, MSBuild/NuGet, pip/Poetry, Go Modules, npm/Yarn, Ant |
| Deployment Strategies | Blue/Green, Canary, Rolling, Feature Flags, A/B Testing, Shadow |
| Deployment Types | Containers, Virtual Machines, Serverless, Bare Metal, Edge, Hybrid |
| Deployment Destinations | Public Cloud (AWS, Azure, GCP), Private Cloud (Tanzu, OpenShift, Orange.os), On-Premises, Multi-Cloud, Edge Locations, Hybrid |

**OS Support Legend:**
- Linux: RHEL, Ubuntu, Alpine
- Windows: Server 2019, Server 2022

**5 Engineering Support Layers:**
| Layer | Tools | Functions |
|-------|-------|-----------|
| Performance Engineering | JMeter, LoadRunner | Load testing, performance monitoring, capacity planning |
| Quality Assurance | SauceLabs, qTest | Test automation, regression testing, cross-browser testing |
| Application Security | Fortify, Sonatype, Apiiro | SAST, SCA, runtime protection, vulnerability management |
| Monitoring & Observability | Dynatrace, Splunk, Moogsoft, Grafana | APM, log analytics, alerting, dashboards |
| Policy as Code | OPA | Policy enforcement, compliance automation, governance |

#### Navigation Consistency Updates
Updated all pages to use consistent gradient navigation button style (`.nav-btn`):
- `executive-summary.html`
- `communications.html`
- `stakeholders.html`
- `roadmap.html`
- `release-notes.html`

**Button Style:**
```css
.nav-btn {
    background: linear-gradient(135deg, var(--fiserv-blue), var(--fiserv-orange));
    color: white;
    border-radius: 8px;
    box-shadow: 0 4px 15px rgba(255, 102, 0, 0.3);
}
```

#### Key Design Decisions
- Uniform column spacing using flexbox with `flex: 1` child elements
- OS legend bar above technology columns for clean visualization
- Devicon.dev icons for technology identification
- Consistent Fiserv branding (blue-to-orange gradients)

---

### Session: January 2026 — Policy-as-Code & Stakeholder Updates

#### Stakeholders Page Updates (`stakeholders.html`)

| Role | Previous | Updated |
|------|----------|---------|
| Executive Sponsor | — | SVP, Platform Engineering (Amanda Rodriguez) |
| Co-Program Sponsors | — | VP level (Lisa Park - VP, Platform Strategy; Kevin O'Brien - VP, Developer Enablement) |
| Co-Engineering Leads | 2 | 6 (2 Architects + 4 Engineers) |
| Co-Product Leads | — | Renamed to "Platform Product Manager" |
| Cloud Security | — | VP level (Natalie Simmons) |

#### Capabilities Page Updates (`capabilities.html`)

**New Engineering Support Layer Added:**
| Layer | Tools | Functions |
|-------|-------|-----------|
| Docs-as-Code | UML, Markdown, GitHub Pages, GitLab Pages | Documentation generation, architecture diagrams, living documentation |

**Icon Sourcing Strategy:**
| Source | Icons Used |
|--------|------------|
| Devicon.dev | qTest, Dynatrace, Splunk, Grafana, Markdown, GitHub, GitLab, UML |
| VectorLogo.zone | SauceLabs, Moogsoft, OPA |
| Simple Icons CDN | Sonatype, Apache JMeter |
| Custom SVG | LoadRunner, Fortify, Apiiro (no public icons available) |

**Style Updates:**
- Layer capability text changed from `text-muted` to `text-secondary`
- Added `font-weight: 500` for improved readability
- Renamed "Policy as Code" → "Policy-as-Code"
- Renamed "Docs as Code" → "Docs-as-Code"

#### Index Page Updates (`index.html`)

**New Navigation Row:**
```html
<!-- Navigation Links - Row 2 -->
<div class="nav-bar" style="justify-content: center; gap: 1rem; margin-bottom: 2rem;">
    <a href="policy-as-code.html" class="nav-btn">
        <span>📜</span>
        <span>Policy-as-Code</span>
        <span>→</span>
    </a>
</div>
```

#### New Page: Policy-as-Code (`policy-as-code.html`)

**Purpose:** Interactive CD (Continuous Delivery) maturity practice explorer with OPA/Rego policy samples for Cortex scorecards.

**Data Source:** `cd-practices.json` (57 practices from minimumcd.org)

**Practice Categories:**
| Category | Description |
|----------|-------------|
| Automation | Technical practices that can be automated |
| Behavior | Cultural/process practices requiring human adoption |
| Behavior-Enabled-Automation | Practices that combine both aspects |

**Practice Types:**
- Essential (Bronze tier)
- Recommended (Silver tier)
- Advanced (Gold tier)

**Interactive Features:**
- Clickable practice tiles organized by category
- Modal popup displaying:
  - Practice name, type, category badges
  - Maturity level indicator
  - Description
  - Requirements checklist (✓ green checkmarks)
  - Benefits list (★ orange stars)
  - OPA/Rego policy sample with syntax highlighting
  - Copy-to-clipboard functionality for policy code

**Key JavaScript Functions:**
```javascript
// Dynamic loading from JSON
fetch('cd-practices.json')
    .then(response => response.json())
    .then(data => {
        practicesData = data;
        renderPractices();
    });

// Modal interaction
function openModal(practiceId) {
    // Displays practice details with requirements, benefits, Rego policy
}

// Policy generation
function generateRego(practice) {
    // Creates OPA/Rego policy with syntax highlighting
}
```

#### New Data File: `cd-practices.json`

**Source:** https://github.com/bdfinst/interactive-cd.git (Minimum CD practices)

**Structure:**
```json
{
  "practices": [
    {
      "id": "build-automation",
      "name": "Build Automation",
      "description": "...",
      "type": "essential|recommended|advanced",
      "category": "automation|behavior|behavior-enabled-automation",
      "maturityLevel": "bronze|silver|gold",
      "requirements": ["requirement1", "requirement2"],
      "benefits": ["benefit1", "benefit2"]
    }
  ]
}
```

**Total Practices:** 57 practices across all categories

#### Project Files Update

| File | Purpose |
|------|---------|
| `policy-as-code.html` | CD maturity practices with OPA/Rego policy samples |
| `cd-practices.json` | Minimum CD practice definitions (57 practices) |

---

### Session: January 2026 — Branding, Data Mapping & Communications Updates

#### Global Branding Updates

**Footer Rebranding:**
Updated all 11 HTML pages to replace "FISERV" with "© Paula Braden":
| Page | New Footer |
|------|------------|
| index.html | © Paula Braden • PLATFORM AS A PRODUCT • CRITICAL PATH |
| roadmap.html | © Paula Braden • PLATFORM AS A PRODUCT • CAPABILITY ROADMAP |
| release-notes.html | © Paula Braden • PLATFORM AS A PRODUCT • RELEASE NOTES |
| capabilities.html | © Paula Braden • PLATFORM AS A PRODUCT • PLATFORM CAPABILITIES |
| policy-as-code.html | © Paula Braden • PLATFORM AS A PRODUCT • POLICY-AS-CODE |
| communications.html | © Paula Braden • PLATFORM AS A PRODUCT • COMMUNICATIONS PLAN |
| risks.html | © Paula Braden • PLATFORM AS A PRODUCT • RISK REGISTER |
| reference.html | © Paula Braden • PLATFORM AS A PRODUCT • PLATFORM REFERENCE |
| stakeholders.html | © Paula Braden • PLATFORM AS A PRODUCT • PROGRAM STAKEHOLDERS |
| executive-summary.html | © Paula Braden • PLATFORM AS A PRODUCT • EXECUTIVE SUMMARY |
| plateng-flow.html | © Paula Braden • PLATFORM ENGINEERING AS CODE • DIGITAL THREAD |

**Page Title Updates:**
- capabilities.html: "Platform Capabilities | Platform as a Product"
- policy-as-code.html: "Policy-as-Code | Platform as a Product"
- communications.html: "Communications | Platform as a Product"

**Reference Page:**
- Renamed "Fiserv Practices" button to "Continuous Delivery Practices"

#### Index Page Updates (`index.html`)

**PoV Workshop Section Reorganization:**
| Section | Contents |
|---------|----------|
| Production Deployment | Java/SpringBoot Demo App, One-Touch Assembly → Launch Control & Verify |
| Data Foundation | Data Ingestion & Mapping (NEW) |
| Test Scenarios | Greenfield Test, Brownfield Test |
| Deliverables | Scorecards, Engineering Intelligence, Leadership Dashboards |

**New Modal: Data Ingestion & Mapping**
Comprehensive modal for establishing the "Digital Thread" from commit to production:

**Org Hierarchy & App Taxonomy:**
- Business Unit → Division → APM → Application Name hierarchy chain
- APM (Application Portfolio Management) — unique application identifier
- MC-1 → MC-2 → MC-3 → Manager executive hierarchy (Management Committee)
- App Owner — accountable individual for application lifecycle
- App metadata: Language, framework, version, deployment target, lifecycle stage
- Cost center and budget allocation mapping for chargeback services

**Team Topologies:**
- Stream-aligned teams — product/feature delivery ownership
- Platform teams — internal platform capabilities
- Enabling teams — coaching and capability uplift
- Complicated-subsystem teams — specialized domain expertise
- On-call rotation and escalation paths

**Repository → Application Mapping:**
- Mono-repo vs Multi-repo — identify repo-to-app cardinality
- GitHub/GitLab organization and repo naming conventions
- Branch strategy: trunk-based, GitFlow, release branches
- CI pipeline association (Harness, GitLab CI, GitHub Actions)
- Artifact registry mapping (Nexus)

**Digital Thread: Commit → Production:**
- Commit SHA → linked to PR, linked to Jira ticket
- Build ID → CI pipeline execution with test results
- Artifact Version → container image tag, Nexus artifact
- Deployment ID → Harness pipeline, Kratix resource request
- Runtime Instance → K8s pod, namespace, cluster, cloud region

**Data Sources to Correlate:**
| Category | Tools |
|----------|-------|
| Identity & Org | Active Directory, Workday, ServiceNow CMDB |
| Source Control | GitHub, GitLab |
| CI/CD Pipeline | Harness, GitLab CI, GitHub Actions |
| Artifact Registry | Nexus |
| Runtime & Observability | K8s, Dynatrace, Splunk, Grafana |
| Security & Compliance | Fortify, Sonatype, SonarQube, Apiiro, OPA |

#### Communications Page Updates (`communications.html`)

**Regular Cadence Updates:**
- Removed: Quarterly All-Hands Town Hall
- Added: Monthly Platform Capability Demos
  - Live demonstrations of new developer-consumable capabilities: workspace templates, scaffolds, scorecards, deployment workflows, and initiative tracking (Marshall Plan, AppSec SCM Policy)
  - Audience: Application Developers, App Owners, Engineering Managers

**Adoption Scaling Section (Aligned with Roadmap):**
| Phase | Title | Target | Metric |
|-------|-------|--------|--------|
| Phase 1 | PoV Workshop | Demo Applications | 1-5 Services |
| Phase 2 | Pilot | Real Java App on EKS | 1 Production App |
| Cohort 1 | Card Services | 7 VPs • 44 App Owners | 168 Applications |
| Cohort 2 | Issuer Solutions | 10 VPs • 48 App Owners | 221 Applications |

**Summary Stats Bar Added:**
- 389 Target Apps (Cohort 1 + 2)
- ~23% of 1,690 Production Apps
- 17 VPs (Executive Stakeholders)
- 92 App Owners

#### New Page: PlatEng Flow (`plateng-flow.html`)

**Purpose:** Experimental visualization page for Platform Engineering as Code — showing the "Digital Thread" concept where a single commit triggers a chain reaction across infrastructure.

**Sections Created:**
1. **The Digital Thread (Commit to Production)**
   - Animated flow: Coder → CI/CD → Kafka → Kratix → Apigee → Cortex
   - Each node shows role ("The Blueprint", "The Messenger", "The Orchestrator", etc.)
   - "As code" file representation for each component
   - Animated pulse traveling along the thread path

2. **The Layered Cake View (Stack Architecture)**
   - Experience Layer: Cortex + Coder (catalog.yaml, workspace.tf)
   - Logic Layer: Kratix + Kafka (promise.yaml, topic-config.json)
   - Infrastructure Layer: K8s + Apigee (deployment.yaml, proxy-bundle.zip)

3. **Self-Healing MTTR Visualization**
   - 5-step recovery flow when a "stitch" breaks
   - Timeline: Detection → Signal → Reaction → Resolution → Result
   - 4-minute total recovery time
   - No human intervention required

4. **Force Multiplier Visual (200 vs 13,000)**
   - 200 Platform Engineers ("Engine Designers") — write Promises, Kafka Streams, Apigee Policies
   - 13,000 Application Developers ("Drivers") — use Coder Workspaces, browse Cortex, one-click deploy

5. **Visualization Checklist**
   - Kafka in the Middle (The Bus)
   - Kratix as the Brain (The Logic)
   - Apigee as the Shield (The Gateway)
   - Coder as the Starting Line (The Workspace)

**Note:** Page is accessible via direct URL but button removed from index.html navigation for future work.

#### Project Files Update

| File | Status | Purpose |
|------|--------|---------|
| `plateng-flow.html` | NEW | Platform Engineering as Code visualization (Digital Thread) |

---

*Document generated: Session aggregation for Cortex.io IDP Implementation Program*
