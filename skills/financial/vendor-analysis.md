# Skill: Vendor Analysis

## Description
Compare vendor options with Total Cost of Ownership (TCO) analysis, feature comparison, and strategic recommendation.

## Usage
```bash
/vendor-analysis --category cicd --vendors "github-actions,gitlab-ci,jenkins" --teams 100
```

## Parameters

### Required
- `--category` (string): Platform category: "cicd", "observability", "security", "cloud", "container-platform", "secrets", "artifact-registry"
- `--vendors` (string): Comma-separated vendor names to compare (2-5 vendors)

### Optional
- `--teams` (number): Number of development teams (default: 50)
- `--developers` (number): Number of developers (default: calculated from teams × 4)
- `--timeline` (string): Evaluation timeline: "1-year", "3-year", "5-year" (default: "3-year")
- `--priorities` (string): Decision priorities: "cost", "features", "support", "integration", "security" (comma-separated, default: "cost,features")
- `--current-vendor` (string): Current vendor for migration cost analysis
- `--format` (string): Output format: "comparison", "recommendation", "scorecard", "tco" (default: "comparison")
- `--include-migration` (boolean): Include migration cost and effort (default: false)

## Output Formats

### Comparison Format
```
===========================================
VENDOR COMPARISON: CI/CD PLATFORM
===========================================
Evaluation Date: January 2026
Teams: 100 teams, 400 developers
Timeline: 3-year TCO analysis

────────────────────────────────────────
VENDOR OVERVIEW
────────────────────────────────────────

Option 1: GitHub Actions
  Pricing Model: Per-minute compute (Actions minutes)
  Deployment: Cloud (GitHub-hosted) or self-hosted
  Market Position: Leader in developer experience
  Best For: Teams already using GitHub

Option 2: GitLab CI
  Pricing Model: Per-user licensing + compute
  Deployment: SaaS or self-managed
  Market Position: All-in-one DevOps platform
  Best For: Organizations wanting unified platform

Option 3: Jenkins
  Pricing Model: Open source (infrastructure costs only)
  Deployment: Self-hosted only
  Market Position: Legacy incumbent, declining
  Best For: Cost-sensitive with strong DevOps expertise

────────────────────────────────────────
COST COMPARISON (3-Year TCO)
────────────────────────────────────────

┌─────────────────┬──────────────┬──────────────┬──────────────┐
│ Cost Category   │ GitHub       │ GitLab       │ Jenkins      │
├─────────────────┼──────────────┼──────────────┼──────────────┤
│ Licensing       │   $150,000   │   $360,000   │      $0      │
│ Compute         │   $420,000   │   $300,000   │   $480,000   │
│ Infrastructure  │    $60,000   │   $120,000   │   $360,000   │
│ Support         │   $120,000   │   $180,000   │       $0     │
│ Personnel (Ops) │   $180,000   │   $240,000   │   $600,000   │
│ Migration       │    $80,000   │   $120,000   │   $100,000   │
├─────────────────┼──────────────┼──────────────┼──────────────┤
│ TOTAL (3-Year)  │ $1,010,000   │ $1,320,000   │ $1,540,000   │
│ Annual Avg      │   $337,000   │   $440,000   │   $513,000   │
└─────────────────┴──────────────┴──────────────┴──────────────┘

Winner (Cost): GitHub Actions (-23% vs GitLab, -34% vs Jenkins)

────────────────────────────────────────
FEATURE COMPARISON
────────────────────────────────────────

┌──────────────────────┬─────────┬─────────┬─────────┐
│ Feature              │ GitHub  │ GitLab  │ Jenkins │
├──────────────────────┼─────────┼─────────┼─────────┤
│ Ease of Use          │   ★★★★★ │   ★★★★☆ │   ★★☆☆☆ │
│ CI/CD Capabilities   │   ★★★★☆ │   ★★★★★ │   ★★★★☆ │
│ Security Scanning    │   ★★★★★ │   ★★★★★ │   ★★☆☆☆ │
│ Container Support    │   ★★★★★ │   ★★★★★ │   ★★★☆☆ │
│ Marketplace/Plugins  │   ★★★★★ │   ★★★☆☆ │   ★★★★★ │
│ Scalability          │   ★★★★★ │   ★★★★☆ │   ★★★☆☆ │
│ Developer Experience │   ★★★★★ │   ★★★★☆ │   ★★☆☆☆ │
│ Support Quality      │   ★★★★☆ │   ★★★★★ │   ★☆☆☆☆ │
│ Integration Ease     │   ★★★★★ │   ★★★★☆ │   ★★★☆☆ │
│ GitOps Support       │   ★★★★☆ │   ★★★★★ │   ★★☆☆☆ │
└──────────────────────┴─────────┴─────────┴─────────┘

Winner (Features): Tie - GitHub (DX) vs GitLab (All-in-One)

────────────────────────────────────────
DECISION MATRIX
────────────────────────────────────────

Weighted Scorecard (0-100):

Priority: Cost (30%), Features (30%), Integration (20%), Support (20%)

GitHub Actions:   88/100 ⭐ RECOMMENDED
├─ Cost:          95/100 (lowest TCO)
├─ Features:      85/100 (strong CI/CD, excellent DX)
├─ Integration:   95/100 (native GitHub integration)
└─ Support:       75/100 (good, but not 24/7 phone)

GitLab CI:        78/100
├─ Cost:          75/100 (mid-range)
├─ Features:      95/100 (comprehensive DevOps platform)
├─ Integration:   70/100 (requires GitLab adoption)
└─ Support:       90/100 (excellent enterprise support)

Jenkins:          52/100
├─ Cost:          60/100 (hidden infrastructure costs)
├─ Features:      70/100 (powerful but dated)
├─ Integration:   45/100 (requires extensive configuration)
└─ Support:       30/100 (community only)

────────────────────────────────────────
STRATEGIC RECOMMENDATION
────────────────────────────────────────

RECOMMENDED: GitHub Actions

Rationale:
✓ Lowest 3-year TCO ($1.01M vs $1.32M GitLab, $1.54M Jenkins)
✓ Best developer experience (critical for adoption)
✓ Native integration with existing GitHub repos
✓ Minimal operational overhead
✓ Strong ecosystem and marketplace
✓ Future-proof (growing market share)

Migration Path:
1. Pilot with 5 teams (Month 1-2)
2. Rollout to 50% teams (Month 3-6)
3. Full migration (Month 7-12)
4. Jenkins decommission (Month 12)

Total Migration Cost: $80K
Expected Savings: $200K/year vs current Jenkins setup

Key Risks:
⚠ Vendor lock-in to GitHub ecosystem
⚠ Pricing changes (mitigate with 3-year contract)
⚠ Feature gaps vs GitLab (acceptable for current needs)
```

### Recommendation Format
```
===========================================
EXECUTIVE RECOMMENDATION
===========================================

TO: CTO, VP Engineering
FROM: Platform Program Office
RE: CI/CD Platform Vendor Selection

RECOMMENDATION: GitHub Actions

Bottom Line:
GitHub Actions provides the best combination of cost ($1M 3-year TCO),
developer experience, and strategic fit for our organization. We
recommend migrating from Jenkins over 12 months with expected
$200K/year operational savings.

Why GitHub Actions:
• 34% lower TCO than Jenkins over 3 years
• Best-in-class developer experience (critical for adoption)
• Native integration with existing GitHub repos (zero friction)
• Minimal operational overhead (vs Jenkins' 2 FTE requirement)

Why Not GitLab:
• 30% higher cost than GitHub
• Requires migrating source control (high friction)
• All-in-one platform doesn't align with best-of-breed strategy

Why Not Jenkins:
• Highest TCO due to infrastructure and personnel costs
• Poor developer experience (adoption risk)
• Declining market share and community support

Next Steps:
1. Initiate 3-month pilot with 5 teams (Budget: $15K)
2. Negotiate enterprise contract (Target: 10% discount)
3. Develop migration plan (Timeline: 12 months)
4. Allocate $80K migration budget

Approval Requested By: February 1, 2026
```

### TCO (Total Cost of Ownership) Format
```
===========================================
TOTAL COST OF OWNERSHIP ANALYSIS
===========================================
Vendor: GitHub Actions vs GitLab CI vs Jenkins
Timeline: 3 Years (FY2026-2028)
Scale: 100 teams, 400 developers

────────────────────────────────────────
COST BREAKDOWN: GITHUB ACTIONS
────────────────────────────────────────

Year 1:
├─ Licensing (Enterprise):      $50,000
├─ Compute (Actions minutes):  $140,000
├─ Self-hosted runners:         $20,000
├─ Support (Enterprise):        $40,000
├─ Personnel (0.5 FTE ops):     $60,000
├─ Migration (one-time):        $80,000
└─ Training:                    $15,000
    TOTAL Y1:                  $405,000

Year 2:
├─ Licensing:                   $50,000
├─ Compute:                    $140,000
├─ Infrastructure:              $20,000
├─ Support:                     $40,000
├─ Personnel (0.5 FTE):         $60,000
└─ Training (ongoing):           $5,000
    TOTAL Y2:                  $315,000

Year 3:
├─ [Similar to Y2]             $290,000

3-YEAR TCO:                  $1,010,000

────────────────────────────────────────
COST BREAKDOWN: GITLAB CI
────────────────────────────────────────

Year 1:
├─ Licensing (Ultimate, 400 users): $120,000
├─ Compute (CI/CD minutes):         $100,000
├─ Infrastructure (self-managed):    $40,000
├─ Support (Premium):                $60,000
├─ Personnel (0.75 FTE ops):         $80,000
├─ Migration (repos + CI):          $120,000
└─ Training:                         $30,000
    TOTAL Y1:                       $550,000

Year 2:
├─ [...]                           $390,000

Year 3:
├─ [...]                           $380,000

3-YEAR TCO:                      $1,320,000

────────────────────────────────────────
COST BREAKDOWN: JENKINS
────────────────────────────────────────

Year 1:
├─ Licensing:                         $0
├─ Infrastructure (VMs, storage):  $160,000
├─ Compute (build agents):         $180,000
├─ Support:                            $0
├─ Personnel (2 FTE Jenkins admins): $200,000
├─ Migration (pipeline rewrites):  $100,000
└─ Training:                        $25,000
    TOTAL Y1:                      $665,000

Year 2:
├─ [...]                           $440,000

Year 3:
├─ [...]                           $435,000

3-YEAR TCO:                      $1,540,000

────────────────────────────────────────
TCO SUMMARY & SENSITIVITY
────────────────────────────────────────

Base Case:
GitHub:  $1,010,000 (LOWEST)
GitLab:  $1,320,000 (+31% vs GitHub)
Jenkins: $1,540,000 (+52% vs GitHub)

If Compute Costs +50% (aggressive usage):
GitHub:  $1,220,000
GitLab:  $1,470,000
Jenkins: $1,540,000
→ GitHub still wins

If Personnel Costs +20% (hiring premium):
GitHub:  $1,046,000
GitLab:  $1,368,000
Jenkins: $1,660,000
→ GitHub still wins

Conclusion: GitHub is most cost-effective across all scenarios
```

### Scorecard Format
```
===========================================
VENDOR SCORECARD
===========================================

Evaluation Criteria (Weighted):

Cost (30%):
├─ GitHub Actions:   9/10  → 27 points
├─ GitLab CI:        7/10  → 21 points
└─ Jenkins:          6/10  → 18 points

Features & Capabilities (30%):
├─ GitHub Actions:   8/10  → 24 points
├─ GitLab CI:        9/10  → 27 points
└─ Jenkins:          7/10  → 21 points

Integration & Compatibility (20%):
├─ GitHub Actions:   10/10 → 20 points
├─ GitLab CI:        6/10  → 12 points
└─ Jenkins:          5/10  → 10 points

Support & Maintenance (10%):
├─ GitHub Actions:   7/10  → 7 points
├─ GitLab CI:        9/10  → 9 points
└─ Jenkins:          3/10  → 3 points

Developer Experience (10%):
├─ GitHub Actions:   10/10 → 10 points
├─ GitLab CI:        8/10  → 8 points
└─ Jenkins:          4/10  → 4 points

────────────────────────────────────────
FINAL SCORES
────────────────────────────────────────

1. GitHub Actions: 88/100 ⭐ WINNER
2. GitLab CI:      77/100
3. Jenkins:        56/100

Recommendation: GitHub Actions
Confidence Level: High (8/10)
```

## Vendor Categories

### CI/CD Platforms
```
Common Options:
- GitHub Actions
- GitLab CI
- Jenkins
- CircleCI
- Azure DevOps
- Bitbucket Pipelines
```

### Observability
```
Common Options:
- Datadog
- New Relic
- Dynatrace
- Splunk
- Elastic (ELK Stack)
- Grafana Cloud
```

### Security Scanning
```
Common Options:
- Snyk
- Checkmarx
- Aqua Security
- Prisma Cloud
- GitHub Advanced Security
- GitLab Security
```

### Cloud Providers
```
Common Options:
- AWS
- Azure
- Google Cloud Platform
- Oracle Cloud
- IBM Cloud
```

### Container Platforms
```
Common Options:
- Amazon EKS
- Google GKE
- Azure AKS
- Red Hat OpenShift
- Rancher
- VMware Tanzu
```

### Secrets Management
```
Common Options:
- HashiCorp Vault
- AWS Secrets Manager
- Azure Key Vault
- CyberArk
- 1Password
```

### Artifact Registry
```
Common Options:
- JFrog Artifactory
- Sonatype Nexus
- GitHub Packages
- AWS CodeArtifact
- Azure Artifacts
```

## Examples

### Example 1: CI/CD Comparison
```bash
/vendor-analysis --category cicd --vendors "github-actions,gitlab-ci,jenkins" --teams 100 --format comparison
```

### Example 2: Observability with Migration Costs
```bash
/vendor-analysis --category observability --vendors "datadog,newrelic,dynatrace" --developers 500 --current-vendor splunk --include-migration true
```

### Example 3: Quick Recommendation
```bash
/vendor-analysis --category security --vendors "snyk,checkmarx" --format recommendation --priorities "security,cost"
```

### Example 4: 5-Year TCO Analysis
```bash
/vendor-analysis --category cloud --vendors "aws,azure,gcp" --timeline 5-year --format tco
```

### Example 5: Scorecard Evaluation
```bash
/vendor-analysis --category secrets --vendors "vault,aws-secrets,azure-keyvault" --format scorecard --priorities "security,integration,cost"
```

## Decision Criteria

### Common Priorities

**Cost-Driven Organizations**:
- Weighting: Cost 50%, Features 30%, Support 20%
- Favor open source or consumption-based pricing

**Feature-Driven Organizations**:
- Weighting: Features 50%, Integration 25%, Cost 25%
- Favor comprehensive platforms

**Enterprise Organizations**:
- Weighting: Support 30%, Security 30%, Features 25%, Cost 15%
- Favor vendors with strong enterprise support and compliance

## Integration with Agents

```bash
# Vendor analysis via Financial Agent
@financial-agent "Compare GitHub Actions vs GitLab CI for 100 teams"

# Agent invokes:
/vendor-analysis --category cicd --vendors "github-actions,gitlab-ci" --teams 100

# Can link to budget:
@financial-agent "Add the recommended vendor to our budget forecast"
```

## Best Practices

1. **3-Year TCO**: Always evaluate over 3+ years to capture full cost
2. **Include Hidden Costs**: Personnel, training, migration, opportunity cost
3. **Weighted Scorecard**: Prioritize criteria based on organizational values
4. **Pilot Before Commit**: Run 3-month pilot with 5-10 teams
5. **Contract Negotiation**: Multi-year contracts often yield 10-20% discounts
6. **Migration Planning**: Budget 10-20% of TCO for migration

## Common Pitfalls

❌ **Sticker Price Only**: Ignoring operational costs (personnel, infrastructure)
❌ **Feature Checklist**: Choosing based on features you'll never use
❌ **Vendor Lock-In**: Not evaluating exit strategy
❌ **No Pilot**: Committing without hands-on validation
❌ **Ignoring DX**: Undervaluing developer experience (drives adoption)

## Related Skills
- `/budget-forecast` - Incorporate vendor costs into budget
- `/calculate-roi` - Calculate ROI of vendor migration
- `/risk-assessment` - Evaluate vendor-related risks

## Related Agents
- `@financial-agent` - Complex vendor questions and TCO analysis
- `@strategy-agent` - Strategic vendor alignment
- `@risk-agent` - Vendor risk assessment

## Implementation Notes

This skill uses:
- Industry pricing benchmarks (e.g., Gartner, Forrester reports)
- Standard TCO models (licensing + compute + personnel + overhead)
- Vendor list pricing (actual pricing may vary with negotiation)
- Fully-loaded personnel costs (1.3-1.5x base salary)

For accurate vendor comparisons, request quotes from vendors directly and provide to the analysis.
