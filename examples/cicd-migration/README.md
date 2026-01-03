# Example: CI/CD Migration (Jenkins → GitHub Actions)

This example demonstrates migrating from legacy Jenkins to GitHub Actions for a team of 200 developers across 50 teams.

## Scenario Overview

**Challenge**: Fragmented Jenkins infrastructure causing productivity bottlenecks
**Solution**: Migrate to GitHub Actions with standardized workflows
**Duration**: 9 months
**Investment**: $850K
**ROI**: 215% (18-month payback)

## Current State (Before Migration)

### Jenkins Environment

**Infrastructure**:
- 3 separate Jenkins instances (East Coast, West Coast, Europe)
- 150+ Jenkins jobs (manually configured)
- No standardization across teams
- 12 different plugin versions
- 2 FTE dedicated to Jenkins operations

**Pain Points**:
- **Inconsistent Pipelines**: Every team has different approach
- **Slow Execution**: 25-minute average pipeline time
- **Brittle**: Frequent plugin conflicts and breakages
- **No Self-Service**: Ops team required for new pipelines
- **Poor Developer Experience**: Arcane Groovy syntax
- **Security Gaps**: Secrets in job configurations

**Metrics (Baseline)**:
- Deployment Frequency: 2/week per team
- Pipeline Execution Time: 25 minutes (p95)
- Pipeline Failure Rate: 18% (often Jenkins issues, not code)
- Time to Create New Pipeline: 3 days (with Ops ticket)
- Developer Satisfaction: NPS -15 (frustration with Jenkins)

**Costs**:
- Jenkins Infrastructure: $180K/year (EC2, storage, ops)
- Jenkins Operations: $400K/year (2 FTE @ $200K loaded)
- **Total**: $580K/year

## Target State (After Migration)

### GitHub Actions Environment

**Infrastructure**:
- GitHub-hosted runners (managed service)
- Standardized workflow templates (3 languages)
- Self-service pipeline creation
- Automated secret rotation (Vault integration)
- Zero dedicated operations team

**Improvements**:
- **Standardization**: 3 golden path templates (Node, Python, Go)
- **Fast Execution**: 8-minute average pipeline time (3x faster)
- **Reliable**: 95% success rate (only real failures)
- **Self-Service**: Developers create pipelines in 10 minutes
- **Great DX**: YAML syntax, GitHub-native
- **Secure**: Secrets in Vault, OIDC authentication

**Metrics (Target)**:
- Deployment Frequency: 5/day per team (25x increase)
- Pipeline Execution Time: 8 minutes (p95) - 68% faster
- Pipeline Failure Rate: 5% (actual code issues)
- Time to Create New Pipeline: 10 minutes (self-service)
- Developer Satisfaction: NPS +50

**Costs**:
- GitHub Actions Compute: $240K/year
- Platform Team Support: $100K/year (0.5 FTE)
- **Total**: $340K/year
- **Savings**: $240K/year vs Jenkins

## Migration Strategy

### Phase 1: Pilot (Months 1-3)

**Goal**: Validate approach with 5 pilot teams

**Activities**:
1. **Month 1**: Create golden path templates
   - Node.js/TypeScript template (Express)
   - Python template (FastAPI)
   - Go template
   - Standard stages: build → test → scan → deploy

2. **Month 2**: Pilot team migration
   - Select 5 early adopter teams
   - Migrate 15 services total
   - Hands-on "concierge" support

3. **Month 3**: Validate and iterate
   - Collect pilot team feedback
   - Refine templates based on learnings
   - Measure metrics vs Jenkins baseline

**Success Criteria**:
- [ ] 15 services migrated successfully
- [ ] Pilot team NPS ≥40
- [ ] Pipeline execution time ≤10 minutes
- [ ] Zero P1 production incidents due to CI/CD

**Investment**: $150K
- Platform engineer time: $100K
- GitHub Actions compute: $20K
- Training and support: $30K

---

### Phase 2: Scale (Months 4-6)

**Goal**: Migrate 50% of teams (25 teams, ~125 services)

**Activities**:
1. **Batch Migration**: 8-10 teams per month
2. **Self-Service Enablement**:
   - Migration documentation
   - Self-service migration script
   - Office hours (2x/week)
3. **Legacy Jenkins Freeze**: No new pipelines on Jenkins

**Migration Approach**:
- **Week 1**: Team kickoff, template review
- **Week 2**: Team migrates 1-2 services (practice)
- **Week 3**: Team migrates remaining services
- **Week 4**: Validate, decommission Jenkins jobs

**Success Criteria**:
- [ ] 25 teams migrated (50% of total)
- [ ] 125 services on GitHub Actions
- [ ] <5% rollback to Jenkins
- [ ] Developer NPS ≥30

**Investment**: $300K
- Platform team: $180K (0.5 FTE for 3 months)
- GitHub Actions compute: $90K
- Training: $30K

---

### Phase 3: Complete (Months 7-9)

**Goal**: Migrate remaining 50% of teams, decommission Jenkins

**Activities**:
1. **Final Migration Wave**: Remaining 25 teams
2. **Holdout Support**: Extra support for resistant teams
3. **Jenkins Decommission**:
   - Archive historical build data
   - Shut down Jenkins instances
   - Reclaim infrastructure costs

**Success Criteria**:
- [ ] 100% of teams on GitHub Actions
- [ ] Jenkins fully decommissioned
- [ ] Full infrastructure cost savings realized
- [ ] Developer NPS ≥50

**Investment**: $400K
- Platform team: $250K
- GitHub Actions compute: $130K
- Training and support: $20K

---

## Technical Implementation

### GitHub Actions Workflow Templates

#### Node.js/TypeScript Template

```yaml
# .github/workflows/template-nodejs.yml
name: Node.js CI/CD Pipeline

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]

jobs:
  build-test:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v3

      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '18'
          cache: 'npm'

      - name: Install dependencies
        run: npm ci

      - name: Lint
        run: npm run lint

      - name: Test with coverage
        run: npm run test:coverage

      - name: Build
        run: npm run build

      - name: Security scan (Snyk)
        uses: snyk/actions/node@master
        env:
          SNYK_TOKEN: ${{ secrets.SNYK_TOKEN }}

      - name: Build Docker image
        run: docker build -t ${{ github.repository }}:${{ github.sha }} .

      - name: Scan Docker image
        uses: aquasecurity/trivy-action@master
        with:
          image-ref: ${{ github.repository }}:${{ github.sha }}
          severity: 'CRITICAL,HIGH'

  deploy-staging:
    needs: build-test
    if: github.ref == 'refs/heads/develop'
    runs-on: ubuntu-latest
    environment: staging

    steps:
      - name: Deploy to EKS Staging
        uses: azure/k8s-deploy@v4
        with:
          manifests: k8s/staging/
          images: ${{ github.repository }}:${{ github.sha }}

  deploy-production:
    needs: build-test
    if: github.ref == 'refs/heads/main'
    runs-on: ubuntu-latest
    environment: production

    steps:
      - name: Deploy to EKS Production
        uses: azure/k8s-deploy@v4
        with:
          manifests: k8s/production/
          images: ${{ github.repository }}:${{ github.sha }}
```

**Features**:
- ✅ Automated testing with coverage
- ✅ Linting and code quality checks
- ✅ Security scanning (Snyk, Trivy)
- ✅ Docker image build
- ✅ Automated staging deployment
- ✅ Manual approval for production

---

### Migration Scripts

#### Automated Jenkins Job Converter

```bash
#!/bin/bash
# migrate-jenkins-job.sh
# Converts Jenkins job config to GitHub Actions workflow

JENKINS_JOB_NAME=$1
REPO_NAME=$2

echo "Migrating Jenkins job: $JENKINS_JOB_NAME to GitHub Actions"

# 1. Export Jenkins job config
jenkins-cli.jar -s http://jenkins.local get-job "$JENKINS_JOB_NAME" > jenkins-job.xml

# 2. Parse build steps (simplified - actual implementation more complex)
# Extract:
# - Language/runtime
# - Build commands
# - Test commands
# - Deploy commands

# 3. Generate GitHub Actions workflow
cat > .github/workflows/ci.yml <<EOF
# Auto-generated from Jenkins job: $JENKINS_JOB_NAME
# Review and customize as needed

name: CI/CD Pipeline

on:
  push:
    branches: [main, develop]
  pull_request:

jobs:
  # Generated jobs here
EOF

echo "✅ Migration complete. Review .github/workflows/ci.yml"
echo "⚠️  Manual review required for:"
echo "   - Secret references"
echo "   - Deployment targets"
echo "   - Custom plugins"
```

---

## Migration Playbook

### Team Migration Checklist

**Pre-Migration (1 week before)**:
- [ ] Identify all Jenkins jobs for team
- [ ] Review GitHub Actions templates
- [ ] Schedule kickoff meeting
- [ ] Assign migration owner from team

**Week 1: Preparation**:
- [ ] Attend migration kickoff (1 hour)
- [ ] Review template for your language
- [ ] Identify custom Jenkins logic (if any)
- [ ] Test GitHub Actions in sandbox repo

**Week 2: Pilot Migration**:
- [ ] Migrate 1-2 low-risk services
- [ ] Validate pipeline works end-to-end
- [ ] Compare metrics (execution time, reliability)
- [ ] Document any issues

**Week 3: Full Migration**:
- [ ] Migrate all remaining services
- [ ] Update team documentation
- [ ] Train team members on GitHub Actions
- [ ] Monitor for issues

**Week 4: Validation & Cleanup**:
- [ ] Verify all services building successfully
- [ ] Decommission Jenkins jobs
- [ ] Celebrate migration complete!
- [ ] Provide feedback to platform team

---

## Results & Metrics

### Productivity Improvements

| Metric | Before (Jenkins) | After (GitHub Actions) | Improvement |
|--------|-----------------|----------------------|-------------|
| **Deployment Frequency** | 2/week | 5/day | **+1,150%** |
| **Pipeline Execution Time** | 25 min | 8 min | **-68%** |
| **Pipeline Failure Rate** | 18% | 5% | **-72%** |
| **Time to New Pipeline** | 3 days | 10 min | **-99.7%** |
| **Developer NPS** | -15 | +50 | **+65 points** |

---

### Financial Impact

**Investment**: $850K over 9 months

**Annual Savings**:
- Jenkins infrastructure: $180K
- Jenkins operations: $400K (2 FTE → 0.5 FTE)
- Developer productivity: $1,200K (time savings)
- **Total Benefits**: $1,780K/year

**ROI Calculation**:
```
ROI = (Benefits - Costs) / Costs × 100%
    = ($1,780K - $850K) / $850K × 100%
    = 109% in Year 1
    = 215% over 3 years

Payback Period = $850K / ($1,780K/12) = 5.7 months
```

---

## Lessons Learned

### What Worked Well

1. **Golden Path Templates**: 80% of teams used templates as-is
2. **Pilot Teams**: Early wins built momentum and credibility
3. **Self-Service**: Developers loved not waiting for Ops tickets
4. **Concierge Support**: Hands-on help for first migration reduced anxiety
5. **Migration Scripts**: Automated converter saved 60% of migration effort

### Challenges & Solutions

**Challenge 1: Custom Jenkins Plugins**
- **Impact**: 15% of teams had custom Jenkins plugins
- **Solution**: Re-implemented as GitHub Actions or external services
- **Lesson**: Most "custom" logic wasn't actually needed

**Challenge 2: Secret Migration**
- **Impact**: 300+ secrets stored in Jenkins
- **Solution**: Automated migration to Vault + GitHub Secrets
- **Lesson**: Great opportunity to clean up unused secrets

**Challenge 3: Resistant Teams**
- **Impact**: 3 teams strongly preferred Jenkins
- **Solution**: Voluntary migration, but Jenkins support ended Month 9
- **Lesson**: Eventually they migrated when Jenkins was shut down

**Challenge 4: Pipeline Execution Time**
- **Impact**: Some pipelines initially slower on GitHub Actions
- **Solution**: Optimized with caching and parallel jobs
- **Lesson**: GitHub Actions different from Jenkins, requires different optimizations

### What We'd Do Differently

1. **Start with FinOps**: GitHub Actions costs spiked initially (heavy usage)
2. **Better Change Management**: More communication to reduce resistance
3. **Template Iteration**: Should have iterated templates faster based on feedback
4. **Metrics Baseline**: Wish we'd had better Jenkins metrics for comparison

---

## Related Resources

- [Complete Transformation Example](../complete-transformation/) - Full platform transformation
- [Kubernetes Adoption Example](../kubernetes-adoption/) - Container platform migration
- GitHub Actions Templates: See `/templates` directory
- Migration Scripts: See `/scripts` directory

---

**Example Status**: Realistic scenario based on actual Jenkins → GitHub Actions migrations
**Last Updated**: January 2026
