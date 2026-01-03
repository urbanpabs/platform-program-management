# Getting Started with Platform Program Management Tools

## 🎯 Quick Start

This repository provides AI-powered Claude Code agents and skills for Platform Program Managers leading complex platform transformation initiatives.

## What's Inside

### 🤖 Agents (AI Assistants)
- **@strategy-agent**: Roadmapping, MVP definition, value metrics
- **@financial-agent**: ROI calculation, budgeting, vendor analysis
- **@stakeholder-agent**: Stakeholder mapping and engagement (coming soon)
- **@delivery-agent**: Dependency tracking and milestone management (coming soon)
- **@governance-agent**: Executive reporting and decision tracking (coming soon)
- **@integration-agent**: People, process, and tech alignment (coming soon)
- **@risk-agent**: Risk assessment and compliance (coming soon)

### ⚡ Skills (Executable Commands)
- `/calculate-roi`: Calculate platform transformation ROI
- `/create-roadmap`: Generate multi-year roadmaps (coming soon)
- `/define-mvp`: Scope Minimum Viable Platform (coming soon)
- `/budget-forecast`: Generate budget forecasts (coming soon)
- `/vendor-analysis`: Compare vendor options (coming soon)
- `/stakeholder-map`: Create stakeholder maps (coming soon)
- `/exec-briefing`: Generate executive briefings (coming soon)
- `/risk-assessment`: Comprehensive risk analysis (coming soon)

## Installation

### Prerequisites
1. **Claude Code** - Install from [https://claude.com/claude-code](https://claude.com/claude-code)
2. **VS Code** (or compatible IDE)
3. **Git** (for cloning the repository)

### Setup

1. **Clone the repository**:
```bash
git clone https://github.com/YOUR-USERNAME/platform-program-management.git
cd platform-program-management
```

2. **Open in VS Code**:
```bash
code .
```

3. **Claude Code will automatically detect** the agents and skills defined in `.claude/config.json`

## Using Agents

Agents are conversational AI assistants specialized in specific domains.

### Invoking an Agent

In Claude Code, use the `@` symbol followed by the agent name:

```bash
@strategy-agent "Help me create a 3-year platform roadmap"
```

```bash
@financial-agent "Calculate ROI for a $2.5M platform investment with 200 developers"
```

### Example Agent Conversations

#### Strategy Agent Example
```
You: @strategy-agent "We have 6 platform verticals. How should we phase our
transformation over 2 years?"

Strategy Agent: I'll help you create a phased transformation strategy.
First, let me ask some questions:

1. What are your 6 verticals? (e.g., CI/CD, Containers, Observability, etc.)
2. What's your total budget?
3. What are the top 3 developer pain points today?
4. Are there any mandated delivery dates?

Based on typical platform transformations, I recommend a 3-phase approach:

**Phase 1 (Months 1-8): Foundation MVP**
Focus on CI/CD + Containers (highest impact, enables other verticals)
[Detailed phase breakdown...]

**Phase 2 (Months 9-16): Scale & Secure**
[...]

Would you like me to generate a detailed roadmap document?
```

#### Financial Agent Example
```
You: @financial-agent "Our platform costs $3M initial investment and
$800K/year OPEX. We have 300 developers. What's our ROI?"

Financial Agent: I'll calculate your 3-year platform ROI.

**Investment Summary**:
- Year 1 CAPEX: $3M
- Annual OPEX: $800K
- 3-Year Total Cost: $5.4M

**Developer Productivity Calculation**:
- 300 developers × $150K avg salary = $45M/year in dev costs
- Assuming 20% time savings = $9M/year productivity value
- 3-year benefit: $27M

**ROI**: 400% over 3 years
**Payback Period**: 4 months

[Full detailed report with sensitivity analysis...]
```

## Using Skills

Skills are executable commands that generate specific artifacts.

### Invoking a Skill

Use the `/` symbol followed by the skill name and parameters:

```bash
/calculate-roi --investment 2.5M --period 3-years --devs 200
```

### Skill Parameters

Most skills support parameters using `--flag value` syntax:

```bash
/calculate-roi \
  --investment 5M \
  --period 36-months \
  --devs 500 \
  --avg-salary 175K \
  --time-savings 25 \
  --format report
```

### Example Skill Outputs

#### /calculate-roi Example

Input:
```bash
/calculate-roi --investment 2M --period 3-years --devs 150
```

Output:
```
===========================================
PLATFORM TRANSFORMATION ROI CALCULATION
===========================================

Investment:          $2,000,000 (CAPEX)
Period:              36 months
Annual OPEX:         $400,000
Total 3-Year Cost:   $3,200,000

Benefits:
 Developer Productivity:  $13,500,000
 Infrastructure Savings:  $300,000
 Incident Reduction:      $150,000
 Total Benefits:          $13,950,000

ROI:                 336%
Payback Period:      5 months
NPV (10% discount):  $9,580,000

===== SENSITIVITY ANALYSIS =====
Conservative (15% savings):  ROI 252%
Optimistic (25% savings):    ROI 420%
50% Adoption:                ROI 168%
```

## Customization

### Creating Custom Agents

1. Create a new markdown file in the appropriate `agents/` subdirectory
2. Define the agent's role, capabilities, and context requirements
3. Register it in `.claude/config.json`

Example:
```json
{
  "agents": {
    "my-custom-agent": {
      "path": "agents/custom/my-agent.md",
      "description": "Custom agent for specific needs",
      "tags": ["custom"]
    }
  }
}
```

### Creating Custom Skills

1. Create a new markdown file in the appropriate `skills/` subdirectory
2. Define parameters, outputs, and examples
3. Register it in `.claude/config.json`

## Common Workflows

### Workflow 1: Strategic Planning

```bash
# 1. Get strategic roadmap help
@strategy-agent "Create a 3-year platform transformation roadmap"

# 2. Define MVP scope
@strategy-agent "What should be in our MVP vs Phase 2?"

# 3. Calculate ROI
/calculate-roi --investment 3M --period 3-years --devs 250

# 4. Create stakeholder briefing
/exec-briefing --topic "Platform Transformation Strategy"
```

### Workflow 2: Financial Planning

```bash
# 1. Calculate ROI
/calculate-roi --investment 5M --period 3-years --format report

# 2. Compare vendors
@financial-agent "Compare GitHub Enterprise vs GitLab for 500 users"

# 3. Generate budget forecast
/budget-forecast --fy 2026 --format detailed

# 4. Create executive financial dashboard
@financial-agent "Create a financial dashboard for Q1 review"
```

### Workflow 3: Stakeholder Management

```bash
# 1. Create stakeholder map
/stakeholder-map --org-chart ./org.json

# 2. Identify alignment risks
@stakeholder-agent "Where are we misaligned between Product and Engineering?"

# 3. Generate executive briefing
/exec-briefing --topic "Q1 Platform Progress" --audience CTO

# 4. Track engagement
@stakeholder-agent "Create an engagement plan for next quarter"
```

## Best Practices

### For Agents
1. **Provide Context**: The more context you provide, the better the recommendations
2. **Ask Follow-ups**: Agents can refine recommendations based on feedback
3. **Use for Complex Decisions**: Agents excel at analysis, not simple lookups
4. **Combine Agents**: Use multiple agents for comprehensive analysis

### For Skills
1. **Use Consistent Units**: Stick to M (millions) or K (thousands)
2. **Conservative Estimates**: Err on the side of caution for financial projections
3. **Document Assumptions**: Save skill outputs for audit trails
4. **Automate Reporting**: Integrate skills into regular reporting cadence

## Troubleshooting

### Agent Not Responding
- Ensure `.claude/config.json` is properly formatted
- Check that agent markdown file exists at specified path
- Restart Claude Code / VS Code

### Skill Not Found
- Verify skill is registered in `.claude/config.json`
- Check skill markdown file exists
- Ensure you're using correct syntax: `/skill-name` not `@skill-name`

### Incorrect Outputs
- Review input parameters
- Check for typos in parameter names
- Provide more context to the agent

## Next Steps

1. **Explore Agents**: Try each agent with sample questions
2. **Generate Artifacts**: Use skills to create real program documents
3. **Customize**: Add your own agents and skills for specific needs
4. **Integrate**: Connect outputs to your existing tools and processes

## Resources

- [Agent Development Guide](./agent-guide.md) (coming soon)
- [Skill Reference](./skill-reference.md) (coming soon)
- [Best Practices](./best-practices.md) (coming soon)
- [Examples](../examples/) (coming soon)

## Support

- **Issues**: [GitHub Issues](https://github.com/YOUR-USERNAME/platform-program-management/issues)
- **Discussions**: [GitHub Discussions](https://github.com/YOUR-USERNAME/platform-program-management/discussions)

---

**Happy Program Managing! 🚀**
