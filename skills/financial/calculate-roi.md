# Skill: Calculate ROI

## Description
Calculate Return on Investment (ROI) for platform transformation initiatives with detailed cost/benefit analysis.

## Usage
```bash
/calculate-roi --investment 2.5M --period 36-months --devs 200 --savings 20%
```

## Parameters

### Required
- `--investment` (string): Total initial investment (CAPEX) with unit (e.g., "2.5M", "500K")
- `--period` (string): Time period for ROI calculation (e.g., "36-months", "3-years")

### Optional
- `--devs` (number): Number of developers impacted (default: 100)
- `--avg-salary` (string): Average developer salary (default: "150K")
- `--time-savings` (number): Percentage of time saved (default: 20)
- `--opex` (string): Annual operational costs (default: calculated as 20% of CAPEX)
- `--infrastructure-savings` (string): Annual infrastructure cost savings (default: "100K")
- `--incident-reduction` (string): Annual savings from reduced incidents (default: "50K")
- `--format` (string): Output format: "report", "summary", "json" (default: "report")

## Output

### Summary Format
```
===========================================
PLATFORM TRANSFORMATION ROI CALCULATION
===========================================

Investment:          $2,500,000 (CAPEX)
Period:              36 months
Annual OPEX:         $500,000
Total 3-Year Cost:   $4,000,000

Benefits:
 Developer Productivity:  $18,000,000
 Infrastructure Savings:  $300,000
 Incident Reduction:      $150,000
 Total Benefits:          $18,450,000

ROI:                 361%
Payback Period:      5 months
NPV (10% discount):  $12,847,000
```

### Full Report Format
Generates a comprehensive markdown report including:
- Executive Summary
- Investment Breakdown (CAPEX/OPEX)
- Benefits Realization by Category
- Year-by-Year Analysis
- ROI Calculation Methodology
- Sensitivity Analysis
- Risks to ROI
- Recommendations

### JSON Format
```json
{
  "investment": {
    "capex": 2500000,
    "annual_opex": 500000,
    "total_3year": 4000000
  },
  "benefits": {
    "developer_productivity": 18000000,
    "infrastructure_savings": 300000,
    "incident_reduction": 150000,
    "total": 18450000
  },
  "roi": {
    "percentage": 361,
    "payback_months": 5,
    "npv": 12847000
  }
}
```

## Calculation Methodology

### Total Cost
```
Total Cost = CAPEX + (OPEX × Years)

Where:
- CAPEX = Initial investment in tools, infrastructure, implementation
- OPEX = Annual operational costs (licensing, support, operations)
```

### Developer Productivity Benefits
```
Annual Productivity Benefit =
  (Number of Developers) ×
  (Average Salary) ×
  (Time Savings Percentage)

Example:
200 devs × $150,000 × 20% = $6,000,000/year
```

### Infrastructure Savings
```
Annual Infrastructure Savings =
  Reduced cloud costs +
  Reduced tooling costs +
  Automation savings
```

### Incident Reduction Savings
```
Annual Incident Savings =
  (Incidents Prevented) ×
  (Average Cost per Incident)
```

### ROI Formula
```
ROI = ((Total Benefits - Total Costs) / Total Costs) × 100%
```

### Payback Period
```
Payback Period = Initial Investment / Monthly Benefit
```

### Net Present Value (NPV)
```
NPV = Σ(Benefits_year / (1 + discount_rate)^year) - Total Investment

Using 10% discount rate by default
```

## Examples

### Example 1: Basic ROI Calculation
```bash
/calculate-roi --investment 2M --period 3-years
```

Output:
```
Investment: $2,000,000
Period: 36 months
ROI: 275%
Payback: 6 months
```

### Example 2: Detailed ROI with Custom Parameters
```bash
/calculate-roi \
  --investment 5M \
  --period 3-years \
  --devs 500 \
  --avg-salary 175K \
  --time-savings 25 \
  --opex 1.2M \
  --infrastructure-savings 500K \
  --format report
```

Output: Full detailed ROI report with sensitivity analysis

### Example 3: Quick JSON for Dashboards
```bash
/calculate-roi --investment 1.5M --period 2-years --format json
```

Output: JSON data for integration with dashboards or reporting tools

## Sensitivity Analysis

The full report includes sensitivity analysis showing ROI impact of:
- ±25% variance in time savings assumption
- ±20% variance in OPEX costs
- Different adoption rates (50%, 75%, 100%)

Example:
```
Sensitivity Analysis:
┌─────────────────────┬──────┐
│ Scenario            │  ROI │
├─────────────────────┼──────┤
│ Base Case           │ 361% │
│ Conservative (15%)  │ 241% │
│ Optimistic (25%)    │ 481% │
│ 50% Adoption        │ 180% │
│ OPEX +20%           │ 321% │
└─────────────────────┴──────┘
```

## Integration with Agents

This skill is designed to work with the `@financial-agent`:

```bash
# Ask the agent to use the skill
@financial-agent "Calculate ROI for our $3M platform investment over 3 years with 300 developers"

# The agent will invoke:
/calculate-roi --investment 3M --period 3-years --devs 300
```

## Best Practices

1. **Use Conservative Estimates**: Start with lower time savings (15-20%) rather than optimistic (30%+)
2. **Include All Costs**: Don't forget training, change management, and integration costs
3. **Update Regularly**: Recalculate ROI quarterly as actuals come in
4. **Show Sensitivity**: Always include sensitivity analysis for executives
5. **Track Assumptions**: Document all assumptions for future reference

## Common Pitfalls

❌ **Overly Optimistic Savings**: 30%+ time savings is rarely realistic
❌ **Ignoring OPEX**: Don't forget ongoing operational costs
❌ **Single Scenario**: Always show best/worst/likely cases
❌ **Vanity Metrics**: Time saved ≠ value unless converted to business outcomes

## Output Templates

### Executive Summary Template
```
The proposed platform transformation requires an investment of $[X]M over [Y] years.
Based on conservative assumptions, we project a [Z]% ROI with payback in [N] months.

Key Drivers:
- Developer productivity improvements: $[X]M
- Infrastructure optimization: $[Y]K
- Reduced operational incidents: $[Z]K

We recommend proceeding with the investment.
```

## Related Skills
- `/budget-forecast` - Forecast detailed budget needs
- `/vendor-analysis` - Compare vendor costs
- `/tco-analysis` - Calculate total cost of ownership

## Related Agents
- `@financial-agent` - Ask complex financial questions
- `@strategy-agent` - Link ROI to strategic roadmap

## Implementation Notes

This skill uses the financial models defined in the Financial Agent documentation.
For custom ROI models or industry-specific calculations, extend the base calculation
with additional parameters.
