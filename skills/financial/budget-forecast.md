# Skill: Budget Forecast

## Description
Generate comprehensive budget forecast for platform transformation with CAPEX/OPEX breakdown, variance analysis, and multi-year projections.

## Usage
```bash
/budget-forecast --fiscal-year FY2026 --period quarterly --format detailed
```

## Parameters

### Required
- `--fiscal-year` (string): Fiscal year for forecast (e.g., "FY2026", "2026")

### Optional
- `--period` (string): Forecast granularity: "monthly", "quarterly", "annual" (default: "quarterly")
- `--horizon` (string): Forecast horizon: "1-year", "3-year", "5-year" (default: "1-year")
- `--current-spend` (string): Current annual platform spend (e.g., "1.2M", "500K")
- `--growth-rate` (number): Expected team growth rate percentage (default: 15)
- `--format` (string): Output format: "summary", "detailed", "variance", "executive" (default: "detailed")
- `--include-contingency` (boolean): Include 10-20% contingency buffer (default: true)
- `--cost-breakdown` (boolean): Include detailed cost category breakdown (default: true)

## Output Formats

### Summary Format
```
===========================================
BUDGET FORECAST - FY2026
===========================================
Period: Quarterly
Forecast Horizon: 1 Year
Contingency Buffer: 15%

────────────────────────────────────────
EXECUTIVE SUMMARY
────────────────────────────────────────
Total FY2026 Budget: $4,850,000
  CAPEX: $2,500,000 (52%)
  OPEX:  $2,350,000 (48%)

YoY Change: +$1,200,000 (+33%)
Primary Drivers: Platform expansion, team growth

────────────────────────────────────────
QUARTERLY BREAKDOWN
────────────────────────────────────────

Q1 FY2026 (Jan-Mar):
  CAPEX: $1,200,000 (initial infrastructure investment)
  OPEX:    $450,000 (staffing, initial licenses)
  Total: $1,650,000

Q2 FY2026 (Apr-Jun):
  CAPEX:   $800,000 (continued tooling buildout)
  OPEX:    $550,000 (increased headcount, training)
  Total: $1,350,000

Q3 FY2026 (Jul-Sep):
  CAPEX:   $300,000 (final MVP infrastructure)
  OPEX:    $650,000 (full team operational)
  Total:   $950,000

Q4 FY2026 (Oct-Dec):
  CAPEX:   $200,000 (optimization, Phase 2 planning)
  OPEX:    $700,000 (steady state operations)
  Total:   $900,000

────────────────────────────────────────
COST CATEGORIES
────────────────────────────────────────

Infrastructure (35%): $1,700,000
├─ Cloud compute (AWS/Azure): $800,000
├─ Kubernetes/container platform: $400,000
├─ Storage and databases: $300,000
└─ Network and security: $200,000

Tooling & Licenses (20%): $970,000
├─ GitHub Enterprise: $150,000
├─ Datadog (observability): $300,000
├─ Vault (secrets): $80,000
├─ JFrog Artifactory: $120,000
├─ Security scanning tools: $220,000
└─ Misc SaaS tools: $100,000

Personnel (35%): $1,700,000
├─ Platform engineers (6 FTE): $1,200,000
├─ Product owners (2 FTE): $350,000
├─ Technical writers (1 FTE): $150,000

Training & Enablement (5%): $240,000
├─ Platform team training: $100,000
├─ Developer onboarding: $100,000
└─ Conference/certifications: $40,000

Contingency (5%): $240,000

────────────────────────────────────────
VARIANCE ANALYSIS
────────────────────────────────────────

Best Case (-15%): $4,122,500
Base Case:        $4,850,000
Worst Case (+25%): $6,062,500

Key Risk Factors:
⚠ Cloud cost overruns (±20%)
⚠ Hiring delays or premium salaries (+30%)
⚠ Tool vendor price increases (+10-15%)
⚠ Scope expansion (Phase 2 pulled forward)
```

### Detailed Format
Comprehensive budget document including:
- Executive summary with totals
- Multi-year projection (if horizon > 1 year)
- Quarterly/monthly breakdown
- CAPEX vs OPEX analysis
- Cost category deep dive
- Headcount plan with fully-loaded costs
- Vendor contracts and renewal dates
- Cost allocation by vertical/initiative
- Variance scenarios (best/base/worst)
- Budget assumptions and dependencies
- Approval workflow and sign-offs

### Variance Analysis Format
```
===========================================
BUDGET VARIANCE ANALYSIS
===========================================

Scenario Planning:

┌────────────────────┬──────────────┬──────────────┬──────────────┐
│ Category           │ Best Case    │ Base Case    │ Worst Case   │
├────────────────────┼──────────────┼──────────────┼──────────────┤
│ Infrastructure     │ $1,445,000   │ $1,700,000   │ $2,125,000   │
│ Tooling/Licenses   │   $824,500   │   $970,000   │ $1,212,500   │
│ Personnel          │ $1,445,000   │ $1,700,000   │ $2,210,000   │
│ Training           │   $204,000   │   $240,000   │   $300,000   │
│ Contingency        │   $204,000   │   $240,000   │   $300,000   │
├────────────────────┼──────────────┼──────────────┼──────────────┤
│ TOTAL              │ $4,122,500   │ $4,850,000   │ $6,147,500   │
└────────────────────┴──────────────┴──────────────┴──────────────┘

Variance Drivers:

Best Case Assumptions (-15%):
✓ Competitive hiring market (salaries on target)
✓ Cloud cost optimization early
✓ Vendor discounts negotiated (multi-year contracts)
✓ No scope expansion

Worst Case Assumptions (+25%):
✗ Hiring delays requiring premium contractors
✗ Cloud cost overruns (30% over estimate)
✗ Vendor price increases at renewal
✗ Scope expansion (partial Phase 2 pulled forward)
✗ Security/compliance requirements increase tooling needs
```

### Executive Format
```
TO: CFO, CTO, VP Engineering
FROM: Platform Program Office
RE: FY2026 Platform Budget Request

===========================================
EXECUTIVE BUDGET REQUEST - FY2026
===========================================

Request: $4,850,000
  CAPEX: $2,500,000
  OPEX:  $2,350,000

YoY Change: +33% (+$1,200,000 vs FY2025)

Business Justification:
The platform transformation will deliver $12M in productivity
benefits over 3 years with 18-month payback. FY2026 represents
the foundational MVP investment.

Investment Highlights:
• 50% developer productivity improvement
• 10x deployment frequency increase
• 80% reduction in deployment lead time
• Support 200 developers across 50 teams

Budget Allocation:
1. Infrastructure (35%): Cloud platform foundation
2. Personnel (35%): 9 FTE platform team
3. Tooling (20%): Enterprise-grade developer tools
4. Training (5%): Developer enablement
5. Contingency (5%): Risk buffer

Key Milestones:
• Q2: Developer Portal launch
• Q3: 50% team onboarded
• Q4: MVP complete, positive ROI demonstrated

Approval Requested By: December 15, 2025
```

## Budget Categories

### CAPEX (Capital Expenditures)
```
One-time investments:
- Initial infrastructure setup
- Platform foundation build
- Enterprise software licenses (multi-year)
- Hardware/servers (if applicable)
- Major tooling purchases

Typical CAPEX Timeline:
- 60-70% in Q1-Q2 (initial buildout)
- 20-30% in Q3 (expansion)
- 10% in Q4 (optimization)
```

### OPEX (Operating Expenditures)
```
Recurring costs:
- Personnel (salaries, benefits)
- Cloud usage (compute, storage, networking)
- Software subscriptions (annual/monthly)
- Training and enablement
- Support and maintenance
- Vendor renewals

Typical OPEX Pattern:
- Ramps up quarterly as team scales
- Stabilizes in Q4 at "steady state"
- Grows 10-20% annually thereafter
```

## Cost Estimation Models

### Infrastructure Costs
```
Small Platform (25 teams, 100 devs):
  Cloud: $300K-$500K/year
  Kubernetes: $100K-$200K/year
  Storage/DB: $100K-$150K/year

Medium Platform (50-100 teams, 200-400 devs):
  Cloud: $800K-$1.5M/year
  Kubernetes: $300K-$500K/year
  Storage/DB: $300K-$500K/year

Large Platform (100+ teams, 500+ devs):
  Cloud: $2M-$4M/year
  Kubernetes: $600K-$1M/year
  Storage/DB: $800K-$1.5M/year
```

### Personnel Costs (Fully Loaded)
```
Platform Engineer: $180K-$250K (avg $200K)
Senior Platform Engineer: $220K-$300K (avg $250K)
Staff/Principal Engineer: $280K-$400K (avg $320K)
Product Owner: $150K-$220K (avg $175K)
Technical Writer: $120K-$160K (avg $140K)
Program Manager: $180K-$250K (avg $200K)

Note: Fully loaded = salary + benefits + overhead (typically 1.4x base)
```

### Tooling Costs
```
GitHub Enterprise: $21/user/month
Datadog: $15-$36/host/month
HashiCorp Vault: $150K-$300K/year (enterprise)
JFrog Artifactory: $30K-$150K/year
Snyk (security): $50K-$200K/year
PagerDuty: $9K-$50K/year
```

## Examples

### Example 1: Basic Annual Forecast
```bash
/budget-forecast --fiscal-year FY2026 --period quarterly
```

Output: Quarterly budget breakdown for FY2026 with CAPEX/OPEX split

### Example 2: Multi-Year Projection
```bash
/budget-forecast --fiscal-year FY2026 --horizon 3-year --format detailed
```

Output: Detailed 3-year budget projection showing MVP (Year 1), Scale (Year 2), Optimize (Year 3)

### Example 3: Variance Analysis
```bash
/budget-forecast --fiscal-year FY2026 --format variance --include-contingency true
```

Output: Best/base/worst case scenarios with risk factors and mitigation strategies

### Example 4: Executive Summary
```bash
/budget-forecast --fiscal-year FY2026 --format executive --current-spend 3.2M
```

Output: Executive-friendly budget request document showing YoY change and business justification

### Example 5: Monthly Granularity
```bash
/budget-forecast --fiscal-year FY2026 --period monthly --cost-breakdown true
```

Output: Month-by-month budget with detailed cost category breakdown

## Budget Assumptions

### Standard Assumptions
```
Team Growth: 15% annually
Cloud Cost Growth: 20% annually (before optimization)
Tool License Inflation: 8-10% annually
Salary Inflation: 4-6% annually
Contingency Buffer: 10-20% of base budget
```

### Budget Planning Principles
```
1. Zero-Based Budgeting: Justify all expenses annually
2. Quarterly Reviews: Reforecast every quarter
3. Variance Tracking: Monitor actuals vs forecast
4. ROI Linkage: Tie spending to value delivery
5. Risk-Adjusted: Include contingency for unknowns
```

## Variance Tracking

### Monthly Variance Report Template
```
Budget vs Actuals - January 2026

Category          | Budget    | Actual    | Variance  | %    | Notes
------------------|-----------|-----------|-----------|------|------------------
Infrastructure    | $150K     | $165K     | +$15K     | +10% | Unplanned region
Tooling           | $80K      | $75K      | -$5K      | -6%  | Datadog discount
Personnel         | $140K     | $140K     | $0        | 0%   | On target
Training          | $20K      | $12K      | -$8K      | -40% | Course delayed
------------------|-----------|-----------|-----------|------|------------------
TOTAL             | $390K     | $392K     | +$2K      | +1%  | Acceptable

Actions Required:
⚠ Investigate infrastructure overage
✓ Carry forward training budget to Feb
```

## Integration with Agents

```bash
# Generate budget via Financial Agent
@financial-agent "Create FY2026 budget forecast with quarterly breakdown"

# Agent invokes:
/budget-forecast --fiscal-year FY2026 --period quarterly --format detailed

# Can also link to roadmap:
@strategy-agent "Create roadmap for the budget"
```

## Best Practices

1. **Conservative Estimates**: Budget for worst-case on costs, best-case on savings
2. **Quarterly Reviews**: Reforecast every quarter based on actuals
3. **Contingency Buffer**: Always include 10-20% contingency
4. **Track Variance**: Monitor actuals vs forecast monthly
5. **Multi-Year View**: Show 3-year projection even if budgeting for 1 year
6. **Link to Value**: Connect budget to ROI and business outcomes

## Common Pitfalls

❌ **Overly Optimistic**: Underestimating cloud costs or hiring timelines
❌ **Missing OPEX**: Focusing only on CAPEX, forgetting ongoing costs
❌ **No Contingency**: Budget with zero buffer for unknowns
❌ **Annual Only**: Not breaking down into quarters/months
❌ **No Variance Planning**: Single number without best/worst scenarios

## Budget Approval Workflow

```
1. Draft Budget (Program Manager)
   ↓
2. Technical Review (Platform Lead)
   ↓
3. Finance Review (FP&A)
   ↓
4. Executive Approval (CTO, CFO)
   ↓
5. Board Approval (if >$5M)
   ↓
6. Budget Allocation & Tracking
```

## Related Skills
- `/calculate-roi` - Link budget to expected returns
- `/vendor-analysis` - Detailed vendor cost comparison
- `/create-roadmap` - Align budget to roadmap phases

## Related Agents
- `@financial-agent` - Complex budget questions
- `@strategy-agent` - Align budget to strategy
- `@governance-agent` - Executive budget reporting

## Implementation Notes

This skill uses:
- Industry benchmarks for platform team sizing and costs
- Cloud cost models from AWS, Azure, GCP
- Fully-loaded personnel cost multipliers (1.3-1.5x base salary)
- Standard vendor pricing (with volume discounts)

For organization-specific budgets, provide your current spend and team size for more accurate forecasting.
