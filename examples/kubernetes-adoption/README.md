# Example: Kubernetes Adoption (EC2 → EKS)

This example demonstrates migrating from manually-managed EC2 instances to Amazon EKS (Elastic Kubernetes Service) for a team of 150 developers across 40 teams.

## Scenario Overview

**Challenge**: Manual EC2 infrastructure causing operational overhead and reliability issues
**Solution**: Migrate to EKS with standardized deployment patterns
**Duration**: 12 months
**Investment**: $2.8M
**ROI**: 142% (24-month payback)

## Current State (Before Kubernetes)

### EC2 Environment

**Infrastructure**:
- 450 manually-provisioned EC2 instances
- 120 different services running on EC2
- Manual scaling (resize instances, add capacity)
- No standardization (AMIs, configurations vary widely)
- 3 FTE dedicated to instance management

**Deployment Process**:
- SSH into EC2 instance
- Run deployment script (custom per service)
- Manually restart service
- Hope nothing breaks
- **Average deployment time**: 45 minutes per service

**Pain Points**:
- **Manual Operations**: SSH, restart services, resize instances
- **Slow Scaling**: 20-30 minutes to add capacity (launch new EC2)
- **Reliability Issues**: Services crash, no auto-restart
- **Resource Waste**: Over-provisioned instances (peak capacity always running)
- **Inconsistent Configs**: Every team does it differently
- **Poor Observability**: Logs scattered across instances

**Metrics (Baseline)**:
- Deployment Time: 45 minutes average
- Service Uptime: 97.5% (2.5% downtime per month)
- Scaling Time: 25 minutes to add capacity
- Mean Time to Recovery (MTTR): 2 hours
- Infrastructure Cost: $600K/year (EC2 instances running 24/7)
- Operations Cost: $600K/year (3 FTE @ $200K loaded)

**Total Cost**: $1,200K/year

---

## Target State (After Kubernetes/EKS)

### EKS Environment

**Infrastructure**:
- 2 EKS clusters (staging, production)
- 120 services containerized and running on Kubernetes
- Automated scaling (Horizontal Pod Autoscaler)
- Standardized deployment (Helm charts, manifests)
- 0.5 FTE dedicated to EKS management (AWS manages control plane)

**Deployment Process**:
- `kubectl apply` or GitOps (ArgoCD)
- Kubernetes handles rolling deployment
- Automated health checks and rollback
- **Average deployment time**: 3 minutes per service

**Improvements**:
- **Automated Operations**: Kubernetes self-heals, auto-restarts pods
- **Fast Scaling**: Seconds to add pod capacity, 2 minutes for nodes
- **Reliability**: 99.9% uptime (Kubernetes self-healing)
- **Resource Efficiency**: Autoscaling reduces waste (60% cost savings)
- **Standardization**: Helm charts, consistent patterns
- **Great Observability**: Centralized logging, Prometheus metrics

**Metrics (Target)**:
- Deployment Time: 3 minutes (94% faster)
- Service Uptime: 99.9% (10x improvement)
- Scaling Time: 30 seconds for pods, 2 minutes for nodes
- MTTR: 5 minutes (automated recovery)
- Infrastructure Cost: $240K/year (autoscaling + spot instances)
- Operations Cost: $100K/year (0.5 FTE)

**Total Cost**: $340K/year
**Savings**: $860K/year vs EC2

---

## Migration Strategy

### Phase 1: Foundation (Months 1-3)

**Goal**: EKS infrastructure ready for pilot teams

**Activities**:

**Month 1: EKS Cluster Setup**
- Provision production EKS cluster (3 AZs, HA)
- Provision staging EKS cluster
- Configure VPC networking, security groups
- Setup IAM roles for service accounts (IRSA)
- Install core addons:
  - AWS Load Balancer Controller
  - Cluster Autoscaler
  - Metrics Server
  - EBS CSI Driver

**Month 2: Observability & Security**
- Deploy Datadog agents (monitoring, APM, logs)
- Configure centralized logging (CloudWatch → Datadog)
- Setup Prometheus + Grafana (cluster metrics)
- Integrate Vault for secrets
- Configure network policies (zero-trust)
- Setup RBAC (role-based access control)

**Month 3: Golden Path Templates**
- Create Helm chart templates (Node.js, Python, Go)
- Standardized Deployment manifests
- HorizontalPodAutoscaler configurations
- Ingress/Service configurations
- Resource quotas and limits

**Success Criteria**:
- [ ] EKS clusters operational (99.9% uptime)
- [ ] Observability stack functional
- [ ] 3 golden path Helm charts ready
- [ ] Security baseline validated by CISO

**Investment**: $400K
- Platform engineers: $300K (3 FTE @ $100K for 1 month)
- EKS infrastructure: $60K
- Tooling (Datadog, etc.): $40K

---

### Phase 2: Pilot Migration (Months 4-6)

**Goal**: Migrate 10 pilot services, validate approach

**Pilot Service Selection Criteria**:
- Low-risk (not critical path)
- Willing early adopter team
- Stateless (easier to containerize)
- Moderately complex (not too simple, not too complex)

**Migration Process per Service**:

**Week 1: Containerization**
- Create Dockerfile
- Build container image
- Test locally with Docker
- Push to ECR (Elastic Container Registry)

**Week 2: Kubernetes Manifests**
- Create Deployment manifest
- Create Service + Ingress
- Configure autoscaling (HPA)
- Add monitoring (Datadog annotations)

**Week 3: Staging Deployment**
- Deploy to EKS staging
- Smoke test functionality
- Load test (validate autoscaling)
- Monitor for 1 week

**Week 4: Production Cutover**
- Deploy to EKS production (blue/green)
- Shift traffic gradually (10% → 50% → 100%)
- Monitor metrics closely
- Decommission EC2 instance

**Pilot Services** (Examples):
1. User Service (Node.js API)
2. Product Catalog (Python FastAPI)
3. Image Resize Worker (Go)
4. Email Service (Node.js)
5. Analytics API (Python)

**Success Criteria**:
- [ ] 10 services migrated successfully
- [ ] Uptime ≥99.5% on EKS
- [ ] Deployment time ≤5 minutes
- [ ] Zero rollbacks due to EKS issues
- [ ] Pilot team satisfaction ≥8/10

**Investment**: $500K
- Platform engineers: $300K
- Developer time (pilot teams): $150K
- EKS compute: $50K

---

### Phase 3: Scale Migration (Months 7-10)

**Goal**: Migrate 80% of services (95 services)

**Batch Migration Approach**:
- Migrate 10 services per week (2 services per day)
- Prioritize by:
  - Team readiness
  - Service complexity (simple first)
  - Business criticality (non-critical first)

**Migration Patterns by Service Type**:

**Stateless Services** (80% of services):
- Straightforward containerization
- Standard Deployment + Service + Ingress
- HPA for autoscaling
- **Migration time**: 2-3 days per service

**Stateful Services** (15% of services):
- Requires StatefulSet (not Deployment)
- Persistent volumes (EBS via PVC)
- Careful data migration planning
- **Migration time**: 1-2 weeks per service

**Background Workers** (5% of services):
- CronJob or Job manifests
- No Ingress needed
- Simple containerization
- **Migration time**: 1-2 days per service

**Support Model**:
- Self-service migration (docs + templates)
- Office hours (2x per week, 2 hours)
- Slack support channel (#eks-migration)
- "Concierge" support for complex services

**Success Criteria**:
- [ ] 95 services migrated (80% of total)
- [ ] <5% rollback rate
- [ ] Average migration time ≤3 days
- [ ] Developer NPS ≥30

**Investment**: $1,200K
- Platform engineers: $600K
- Developer time: $500K
- EKS compute: $100K

---

### Phase 4: Complete & Optimize (Months 11-12)

**Goal**: Migrate remaining 20% services, decommission EC2

**Activities**:

**Final Migration Wave**:
- Migrate holdout services (complex, stateful, legacy)
- Extra support for challenging migrations
- Pair programming with teams if needed

**EC2 Decommission**:
- Archive EC2 AMIs for compliance
- Terminate all EC2 instances
- Reclaim infrastructure budget
- Celebrate migration complete!

**Optimization**:
- Right-size pod resource requests/limits
- Enable Cluster Autoscaler (auto-scale nodes)
- Implement pod disruption budgets
- Optimize Helm charts based on learnings

**Documentation**:
- Comprehensive runbooks for operations
- Developer onboarding guide
- Troubleshooting guide
- Best practices documentation

**Success Criteria**:
- [ ] 100% of services on EKS
- [ ] All EC2 instances terminated
- [ ] Full infrastructure cost savings realized
- [ ] Developer NPS ≥50
- [ ] Platform uptime ≥99.9%

**Investment**: $700K
- Platform engineers: $400K
- Developer time: $200K
- EKS compute: $100K

---

## Technical Implementation Details

### EKS Cluster Configuration

```yaml
# eksctl cluster config
apiVersion: eksctl.io/v1alpha5
kind: ClusterConfig

metadata:
  name: production-cluster
  region: us-east-1
  version: "1.28"

vpc:
  cidr: 10.0.0.0/16
  nat:
    gateway: HighlyAvailable

managedNodeGroups:
  - name: general-purpose
    instanceType: m5.xlarge
    minSize: 3
    maxSize: 20
    desiredCapacity: 6
    volumeSize: 100
    ssh:
      allow: false
    labels:
      workload-type: general
    tags:
      Environment: production
      Team: platform
    iam:
      withAddonPolicies:
        autoScaler: true
        cloudWatch: true
        ebs: true
        efs: true

  - name: spot-instances
    instanceTypes: ["m5.large", "m5.xlarge", "m5a.large"]
    spot: true
    minSize: 0
    maxSize: 30
    labels:
      workload-type: batch
    taints:
      - key: workload-type
        value: batch
        effect: NoSchedule

addons:
  - name: vpc-cni
  - name: coredns
  - name: kube-proxy
  - name: aws-ebs-csi-driver

iam:
  withOIDC: true
  serviceAccounts:
    - metadata:
        name: cluster-autoscaler
        namespace: kube-system
      wellKnownPolicies:
        autoScaler: true
```

---

### Sample Helm Chart (Node.js Service)

```yaml
# values.yaml
replicaCount: 3

image:
  repository: 123456789.dkr.ecr.us-east-1.amazonaws.com/user-service
  tag: "v1.2.3"
  pullPolicy: IfNotPresent

service:
  type: ClusterIP
  port: 3000

ingress:
  enabled: true
  className: alb
  annotations:
    alb.ingress.kubernetes.io/scheme: internet-facing
    alb.ingress.kubernetes.io/target-type: ip
    alb.ingress.kubernetes.io/healthcheck-path: /health
  hosts:
    - host: api.example.com
      paths:
        - path: /users
          pathType: Prefix

resources:
  requests:
    cpu: 200m
    memory: 256Mi
  limits:
    cpu: 500m
    memory: 512Mi

autoscaling:
  enabled: true
  minReplicas: 3
  maxReplicas: 20
  targetCPUUtilizationPercentage: 70
  targetMemoryUtilizationPercentage: 80

livenessProbe:
  httpGet:
    path: /health
    port: 3000
  initialDelaySeconds: 30
  periodSeconds: 10

readinessProbe:
  httpGet:
    path: /ready
    port: 3000
  initialDelaySeconds: 5
  periodSeconds: 5

podAnnotations:
  ad.datadoghq.com/user-service.logs: '[{"source":"nodejs","service":"user-service"}]'
  ad.datadoghq.com/user-service.checks: |
    {
      "http_check": {
        "instances": [{"url": "http://%%host%%:3000/health"}]
      }
    }

env:
  - name: NODE_ENV
    value: "production"
  - name: DATABASE_URL
    valueFrom:
      secretKeyRef:
        name: user-service-secrets
        key: database-url
```

---

## Migration Playbook

### Service Migration Checklist

**Pre-Migration (1 week)**:
- [ ] Review Dockerfile best practices
- [ ] Inventory service dependencies (databases, APIs)
- [ ] Identify secrets (migrate to Vault)
- [ ] Review Helm chart template for your language
- [ ] Schedule migration kickoff

**Week 1: Containerization**:
- [ ] Create Dockerfile
- [ ] Build and test container locally
- [ ] Push to ECR
- [ ] Document build process

**Week 2: Kubernetes Manifests**:
- [ ] Create Helm chart (or use template)
- [ ] Define resource requests/limits
- [ ] Configure health checks
- [ ] Setup autoscaling (HPA)
- [ ] Add monitoring annotations

**Week 3: Staging Validation**:
- [ ] Deploy to EKS staging
- [ ] Smoke test all endpoints
- [ ] Load test (validate autoscaling works)
- [ ] Monitor for 3-5 days
- [ ] Fix any issues discovered

**Week 4: Production Cutover**:
- [ ] Deploy to EKS production (parallel to EC2)
- [ ] Gradual traffic shift (10% → 50% → 100%)
- [ ] Monitor metrics closely
- [ ] Validate functionality
- [ ] Terminate EC2 instance
- [ ] Celebrate! 🎉

---

## Results & Metrics

### Reliability Improvements

| Metric | Before (EC2) | After (EKS) | Improvement |
|--------|-------------|------------|-------------|
| **Service Uptime** | 97.5% | 99.9% | **+2.4% (10x better)** |
| **MTTR** | 2 hours | 5 minutes | **-96%** |
| **Deployment Time** | 45 min | 3 min | **-93%** |
| **Scaling Time** | 25 min | 30 sec (pods) | **-98%** |
| **Manual Incidents** | 15/month | 1/month | **-93%** |

---

### Cost Savings

**Before (EC2)**:
- Infrastructure: $600K/year (450 instances, always running)
- Operations: $600K/year (3 FTE)
- **Total**: $1,200K/year

**After (EKS)**:
- EKS Control Plane: $90K/year ($0.10/hour × 2 clusters)
- Worker Nodes: $150K/year (autoscaling, spot instances)
- Operations: $100K/year (0.5 FTE)
- **Total**: $340K/year

**Annual Savings**: $860K/year (72% reduction)

**ROI Calculation**:
```
Investment: $2.8M (one-time)
Annual Savings: $860K
Payback Period: $2.8M / $860K = 3.25 years

3-Year Total Savings: $2.58M
3-Year ROI: ($2.58M - $2.8M) / $2.8M = -8% (breaks even ~Year 3)

BUT: Including productivity gains ($400K/year):
3-Year Total Benefits: $2.58M + $1.2M = $3.78M
3-Year ROI: ($3.78M - $2.8M) / $2.8M = 35%
```

---

## Lessons Learned

### What Worked Well

1. **Pilot Phase**: 10 pilot services validated approach, built confidence
2. **Golden Path Templates**: 85% of services used templates with minimal changes
3. **Gradual Cutover**: Blue/green traffic shifting reduced risk
4. **Office Hours**: Twice-weekly support sessions were highly valued
5. **Autoscaling**: Teams loved not managing capacity manually

### Challenges & Solutions

**Challenge 1: Stateful Service Migration**
- **Impact**: 18 stateful services (databases, caches) were complex
- **Solution**: Used StatefulSets + EBS persistent volumes
- **Lesson**: Stateful services take 3-4x longer to migrate

**Challenge 2: Resource Sizing**
- **Impact**: Initial pod resource limits were wrong (too high or too low)
- **Solution**: Vertical Pod Autoscaler recommendations + iteration
- **Lesson**: Start conservative, optimize based on actual usage

**Challenge 3: Networking Complexity**
- **Impact**: VPC, security groups, ingress rules were confusing
- **Solution**: Standardized network policies + runbooks
- **Lesson**: Kubernetes networking is different from EC2, requires training

**Challenge 4: Cost Spike**
- **Impact**: Initial EKS costs higher than expected
- **Solution**: Spot instances, cluster autoscaler, right-sizing
- **Lesson**: Kubernetes can be expensive if not optimized

### What We'd Do Differently

1. **Start with FinOps**: Enable cost monitoring from Day 1
2. **More Training**: Kubernetes training should have been earlier and deeper
3. **Faster Iteration**: Should have migrated pilot services faster (2 weeks vs 4)
4. **Better Metrics**: Wish we had better EC2 baseline metrics

---

## Related Resources

- [Complete Transformation Example](../complete-transformation/)
- [CI/CD Migration Example](../cicd-migration/)
- [Developer Portal Example](../developer-portal/)
- Helm Chart Templates: See `/templates` directory

---

**Example Status**: Realistic scenario based on actual EC2 → EKS migrations
**Last Updated**: January 2026
