# Platform Program Management - Claude Agents & Skills

A comprehensive template repository providing **Claude Code agents and skills** designed specifically for Platform Engineering Program Management across the entire transformation lifecycle.

## 🎯 Overview

This repository provides AI-powered agents and executable skills to support **Platform Program Managers** (PPMs) in delivering complex platform transformation initiatives. Each agent is specialized for one of the seven core domains of platform program management.

## 📋 Seven Core Domains

### 1. **Program Strategy & Vision**
*Vision & Roadmap*
- Executive vision & strategic ownership
- Multi-year transformation roadmapping
- Unified product strategy across platform verticals
- Value definition and measurement frameworks

### 2. **Stakeholder Identification & Management**
*Alignment & Trust*
- Stakeholder engagement planning
- Cross-organizational alignment
- Executive interface and trust building

### 3. **Delivery & Execution**
*Coordination & Value*
- Cross-vertical program coordination
- Dependency management
- Incremental value delivery

### 4. **Governance & Communication**
*Accountability & Reporting*
- Governance framework establishment
- Executive reporting
- Program-level decision authority

### 5. **People, Process, and Technology Integration**
*Model Alignment*
- Organizational alignment
- Process optimization
- Technology investment coordination

### 6. **Risk, Compliance, and Security Oversight**
*Maturity & Audits*
- Comprehensive risk management
- Security and compliance integration
- Audit preparation

### 7. **Financial Stewardship**
*Budget & Vendor Management*
- CAPEX investment management
- ROI tracking and reporting
- OPEX budget management
- Vendor relationship oversight

## 🤖 Agent Architecture

Each domain has:
- **Primary Agent**: Main decision-making and analysis agent
- **Research Agent**: Gathers data and insights
- **Execution Agent**: Performs specific tasks and generates artifacts

## 🛠️ Repository Structure

```
platform-program-management/
├── agents/                      # Claude Code agent definitions
│   ├── strategy/                # Strategy & Vision agents
│   ├── stakeholder/             # Stakeholder Management agents
│   ├── delivery/                # Delivery & Execution agents
│   ├── governance/              # Governance & Communication agents
│   ├── integration/             # People, Process, Tech agents
│   ├── risk/                    # Risk & Compliance agents
│   └── financial/               # Financial Stewardship agents
│
├── skills/                      # Executable Claude Code skills
│   ├── strategy/                # Strategy skills (/roadmap, /mvp, etc.)
│   ├── stakeholder/             # Stakeholder skills
│   ├── delivery/                # Delivery skills
│   ├── governance/              # Governance skills
│   ├── integration/             # Integration skills
│   ├── risk/                    # Risk skills
│   └── financial/               # Financial skills
│
├── templates/                   # Document templates
│   ├── roadmaps/
│   ├── reports/
│   ├── presentations/
│   └── frameworks/
│
├── docs/                        # Documentation
│   ├── getting-started.md
│   ├── agent-guide.md
│   ├── skill-reference.md
│   └── best-practices.md
│
├── examples/                    # Example usage
│   └── sample-program/
│
└── .claude/                     # Claude Code configuration
    └── config.json
```

## 🚀 Quick Start

### Prerequisites
- [Claude Code](https://claude.com/claude-code) installed
- VS Code or compatible IDE
- Access to your platform program documentation

### Installation

1. **Clone this repository** into your platform program workspace:
```bash
git clone <your-repo-url> platform-pm-tools
cd platform-pm-tools
```

2. **Initialize Claude Code configuration**:
```bash
# Claude Code will auto-detect agents and skills
code .
```

3. **Start using agents**:
```bash
# In Claude Code, invoke an agent:
@strategy-agent "Analyze our current platform roadmap and identify gaps"

# Or use a skill:
/create-roadmap
```

## 📖 Usage Examples

### Strategy & Vision

```bash
# Generate a multi-year platform roadmap
/create-roadmap --phases 3 --duration 36-months

# Define MVP requirements
/define-mvp --verticals "ci-cd,containers,observability"

# Align product strategies
@strategy-agent "Unify roadmaps across CI/CD, Container, and Observability platforms"
```

### Stakeholder Management

```bash
# Create stakeholder engagement plan
/stakeholder-map --org-chart ./org.json

# Generate executive briefing
/exec-briefing --topic "Q1 Platform Progress"

# Analyze stakeholder alignment
@stakeholder-agent "Identify misalignment risks between Product and Engineering"
```

### Delivery & Execution

```bash
# Analyze cross-team dependencies
/dependency-analysis --teams all

# Generate sprint planning artifacts
/sprint-plan --iteration Q1-2026

# Track program milestones
@delivery-agent "What's blocking our container platform MVP delivery?"
```

### Governance & Communication

```bash
# Create governance framework
/governance-framework --model decision-rights

# Generate executive report
/exec-report --period Q4-2025 --format slides

# Analyze decision bottlenecks
@governance-agent "Map our current decision-making bottlenecks"
```

### Financial Stewardship

```bash
# Calculate platform ROI
/calculate-roi --investment 2.5M --period 12-months

# Generate budget forecast
/budget-forecast --fy 2026

# Vendor analysis
@financial-agent "Compare costs: GitHub Enterprise vs GitLab Ultimate"
```

## 🎯 Agent Capabilities

### What Agents Can Do

✅ **Analyze** complex program data and identify patterns
✅ **Generate** roadmaps, reports, and strategic artifacts
✅ **Recommend** prioritization and resource allocation
✅ **Identify** risks, dependencies, and bottlenecks
✅ **Draft** executive communications and presentations
✅ **Calculate** ROI, TCO, and financial metrics
✅ **Map** stakeholder relationships and influence
✅ **Assess** platform maturity and capability gaps

### What Agents Cannot Do

❌ Make final executive decisions (you own that)
❌ Replace human judgment in complex trade-offs
❌ Access proprietary data without explicit permission
❌ Execute production changes without approval

## 📚 Domain Deep Dives

### 1. Strategy & Vision Agents

**Primary Agent**: `@strategy-agent`
- Analyzes market trends and internal adoption patterns
- Synthesizes multi-vertical strategies into unified vision
- Identifies roadmap gaps and sequencing issues

**Skills**:
- `/create-roadmap` - Generate multi-phase roadmap
- `/define-mvp` - Scope Minimum Viable Platform
- `/value-metrics` - Define success metrics and KRs

### 2. Stakeholder Management Agents

**Primary Agent**: `@stakeholder-agent`
- Maps organizational power structures
- Analyzes stakeholder sentiment and alignment
- Recommends engagement strategies

**Skills**:
- `/stakeholder-map` - Visual stakeholder mapping
- `/engagement-plan` - Structured engagement calendar
- `/exec-briefing` - Generate executive briefings

### 3. Delivery & Execution Agents

**Primary Agent**: `@delivery-agent`
- Tracks cross-vertical dependencies
- Identifies critical path bottlenecks
- Recommends resource reallocation

**Skills**:
- `/dependency-analysis` - Dependency mapping
- `/milestone-tracker` - Program milestone dashboard
- `/sprint-plan` - Sprint planning artifacts

### 4. Governance & Communication Agents

**Primary Agent**: `@governance-agent`
- Analyzes decision-making patterns
- Identifies governance gaps
- Drafts executive communications

**Skills**:
- `/governance-framework` - Define governance model
- `/exec-report` - Executive status reports
- `/decision-log` - Track program decisions

### 5. Integration Agents (People, Process, Tech)

**Primary Agent**: `@integration-agent`
- Maps organizational roles to outcomes
- Identifies process inefficiencies
- Analyzes technology investment overlap

**Skills**:
- `/role-clarity` - Define RACI matrices
- `/process-optimize` - Process improvement analysis
- `/tech-portfolio` - Technology investment analysis

### 6. Risk & Compliance Agents

**Primary Agent**: `@risk-agent`
- Identifies technical and schedule risks
- Analyzes compliance gaps
- Prepares audit materials

**Skills**:
- `/risk-assessment` - Comprehensive risk analysis
- `/compliance-check` - Security/compliance validation
- `/audit-prep` - Audit preparation materials

### 7. Financial Stewardship Agents

**Primary Agent**: `@financial-agent`
- Calculates platform ROI and TCO
- Forecasts budget needs
- Analyzes vendor contracts

**Skills**:
- `/calculate-roi` - ROI calculation and tracking
- `/budget-forecast` - Budget planning and forecasting
- `/vendor-analysis` - Vendor comparison and negotiation support

## 🔧 Customization

### Adding Custom Agents

1. Create agent definition in `agents/<domain>/`
2. Define agent capabilities and context
3. Register in `.claude/config.json`

### Creating Custom Skills

1. Create skill file in `skills/<domain>/`
2. Define skill parameters and outputs
3. Add to skill registry

See [docs/customization-guide.md](docs/customization-guide.md) for details.

## 📊 Success Metrics

Track your platform program using these agents:

- **Developer Velocity**: Deployment frequency, lead time
- **Platform Adoption**: Active users, service coverage
- **Operational Efficiency**: Cost per deploy, incident MTTR
- **ROI**: Cost savings, productivity gains
- **Stakeholder Satisfaction**: NPS, engagement scores

## 🤝 Contributing

We welcome contributions! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## 📄 License

MIT License - see [LICENSE](LICENSE) for details.

## 🆘 Support

- **Documentation**: [docs/](docs/)
- **Examples**: [examples/](examples/)
- **Issues**: GitHub Issues
- **Discussions**: GitHub Discussions

## 🎓 Learn More

- [Platform Engineering Principles](docs/platform-engineering.md)
- [Program Management Best Practices](docs/best-practices.md)
- [Claude Code Agent Development](docs/agent-development.md)

---

**Built for Platform Program Managers who lead complex transformations** 🚀
