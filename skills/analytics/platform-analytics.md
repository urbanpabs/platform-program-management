# Skill: Platform Analytics

## Description
Comprehensive analytics capabilities for platform engineering teams including data collection, visualization, and analysis across DevOps platform health, pipeline metrics, developer experience, throughput, stability, efficiency, quality, cost analytics, and revenue impact tracking.

Supports both REST API and GraphQL interfaces for flexible data access and integration with observability platforms, business intelligence tools, and custom dashboards.

## Usage
```bash
/platform-analytics --metric-type "pipeline-health" --interface rest --format dashboard
/platform-analytics --metric-type "developer-experience" --interface graphql --format report
/platform-analytics --metric-type "cost-breakdown" --aggregation monthly --export csv
```

## Parameters

### Required
- `--metric-type` (string): Type of analytics to collect/analyze
  - `platform-stack`: DevOps platform stack health monitoring
  - `pipeline-metrics`: Pipeline availability, build success, deployment frequency
  - `developer-experience`: DX scores by tech stack
  - `throughput`: Build/deploy throughput by technology
  - `stability`: Uptime, MTBF, MTTR metrics
  - `efficiency`: Lead time, cycle time, throughput metrics
  - `quality`: Success rate, test coverage, code quality
  - `cost-analytics`: License utilization, OPEX, cost per deploy
  - `revenue-impact`: Revenue correlation with deployment velocity
  - `incident-metrics`: Change tickets, incidents, severity breakdown
  - `environment-metrics`: Deployment success by environment (on-prem, cloud, hybrid)
  - `product-lines`: Revenue attribution by product/feature teams

### Optional
- `--interface` (string): API interface type: "rest", "graphql" (default: "rest")
- `--format` (string): Output format: "dashboard", "report", "raw-data", "visualization" (default: "dashboard")
- `--aggregation` (string): Data aggregation: "real-time", "hourly", "daily", "weekly", "monthly" (default: "daily")
- `--tech-stack` (string): Filter by technology: "java", "dotnet", "python", "javascript", "go", "rust", "cpp", "ruby", "all" (default: "all")
- `--time-range` (string): Time window: "1h", "24h", "7d", "30d", "90d", "1y" (default: "7d")
- `--export` (string): Export format: "json", "csv", "xlsx", "pdf" (default: none)
- `--threshold-alerts` (boolean): Enable threshold-based alerting (default: false)
- `--comparison` (string): Comparative analysis: "yoy" (year-over-year), "mom" (month-over-month), "wow" (week-over-week) (default: none)

---

## Analytics Capabilities

### 1. Platform Stack Health Monitoring

**Data Collection**:
- Platform availability and uptime percentages
- Service health status (operational, degraded, down)
- API endpoint response times
- Platform-specific error rates

**Platforms Tracked**:
- GitHub Enterprise
- Nexus Repository
- Harness CD
- Fortify (SAST)
- Sonatype (SCA)
- Nexus Firewall
- Wiz Cloud Security
- Cloud Dev Environments

**REST API Endpoint**:
```http
GET /api/v1/analytics/platform-stack
Query Parameters:
  - platform: string (optional, filter by platform name)
  - time_range: string (default: 24h)
  - aggregation: string (default: hourly)

Response:
{
  "platforms": [
    {
      "name": "GitHub",
      "status": "operational",
      "uptime": 99.9,
      "response_time_p95": 245,
      "error_rate": 0.01,
      "incidents_last_24h": 0
    },
    ...
  ],
  "summary": {
    "total_platforms": 8,
    "operational": 7,
    "degraded": 1,
    "down": 0,
    "average_uptime": 98.9
  }
}
```

**GraphQL Query**:
```graphql
query PlatformStackHealth($timeRange: String!) {
  platformStack(timeRange: $timeRange) {
    platforms {
      name
      status
      uptime
      responseTimeP95
      errorRate
      incidentsLast24h
    }
    summary {
      totalPlatforms
      operational
      degraded
      down
      averageUptime
    }
  }
}
```

---

### 2. Pipeline Metrics Analytics

**Data Collection**:
- Pipeline availability (uptime of CI/CD system)
- Build success rate (successful builds / total builds)
- Deployment frequency (deploys per day/week)
- Pipeline execution time (p50, p95, p99)
- Cloud Dev Environment health

**Key Performance Indicators**:
- **Pipeline Availability**: Target ≥99%
- **Build Success Rate**: Target ≥90%
- **Deployment Frequency**: Measure velocity (deploys/week)
- **Cloud Dev Env Health**: Target ≥95%

**REST API Endpoint**:
```http
GET /api/v1/analytics/pipeline-metrics
Query Parameters:
  - time_range: string (default: 7d)
  - tech_stack: string (optional)
  - aggregation: string (default: daily)

Response:
{
  "pipeline_availability": {
    "current": 98.5,
    "target": 99.0,
    "trend": "up",
    "change_percent": 1.2
  },
  "build_success_rate": {
    "current": 92.3,
    "target": 90.0,
    "total_builds": 5420,
    "successful_builds": 5004,
    "failed_builds": 416
  },
  "deployment_frequency": {
    "total_deploys_this_week": 247,
    "avg_deploys_per_day": 35.3,
    "change_from_last_week": 12
  },
  "cloud_dev_env_health": {
    "current": 95.2,
    "active_environments": 342,
    "provisioning_time_p95": 180
  }
}
```

**GraphQL Query**:
```graphql
query PipelineMetrics($timeRange: String!, $techStack: String) {
  pipelineMetrics(timeRange: $timeRange, techStack: $techStack) {
    pipelineAvailability {
      current
      target
      trend
      changePercent
    }
    buildSuccessRate {
      current
      target
      totalBuilds
      successfulBuilds
      failedBuilds
    }
    deploymentFrequency {
      totalDeploysThisWeek
      avgDeploysPerDay
      changeFromLastWeek
    }
  }
}
```

**Visualization (Dashboard)**:
```
┌─────────────────────────────────────────────────────────┐
│ PIPELINE METRICS DASHBOARD                              │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  Pipeline Availability: 98.5% [████████████████░░] 99%  │
│  Build Success Rate:    92.3% [████████████████░░] 90%  │
│  Deployment Frequency:  247   [↑ +12 vs last week]      │
│  Cloud Dev Env Health:  95.2% [████████████████░░] 95%  │
│                                                          │
│  Trend (7 days):                                         │
│  ┌──────────────────────────────────────────────┐       │
│  │   99% ┤                                  ╭╮   │       │
│  │   98% ┤               ╭──╮           ╭──╯╰╮  │       │
│  │   97% ┤          ╭────╯  ╰──╮    ╭──╯     ╰─ │       │
│  │   96% ┤      ╭───╯          ╰────╯           │       │
│  │   95% ┤──────╯                               │       │
│  └──────────────────────────────────────────────┘       │
│      Mon  Tue  Wed  Thu  Fri  Sat  Sun                  │
└─────────────────────────────────────────────────────────┘
```

---

### 3. Developer Experience (DX) Scores

**Data Collection**:
- DX survey scores by tech stack (NPS-style, 0-100)
- Build time satisfaction
- Deployment ease ratings
- Platform usability feedback
- Tooling effectiveness scores

**Tracked by Technology**:
- Java: Enterprise applications
- .NET: Cloud applications
- Python: Data engineering
- JavaScript: Full-stack development
- Go: Backend microservices
- Rust: Systems programming
- C++: Performance-critical systems
- Ruby: DevOps automation

**REST API Endpoint**:
```http
GET /api/v1/analytics/developer-experience
Query Parameters:
  - tech_stack: string (optional, filter by tech)
  - time_range: string (default: 30d)

Response:
{
  "overall_dx_score": 82,
  "tech_stacks": [
    {
      "technology": "JavaScript",
      "icon": "⚡",
      "dx_score": 88,
      "developer_count": 127,
      "satisfaction_breakdown": {
        "build_time": 92,
        "deployment_ease": 85,
        "platform_usability": 87,
        "tooling_effectiveness": 89
      },
      "top_pain_points": [
        "Dependency resolution time",
        "Test flakiness"
      ]
    },
    {
      "technology": "Java",
      "icon": "☕",
      "dx_score": 79,
      "developer_count": 76,
      "satisfaction_breakdown": {
        "build_time": 74,
        "deployment_ease": 81,
        "platform_usability": 78,
        "tooling_effectiveness": 83
      },
      "top_pain_points": [
        "Long build times",
        "Complex configuration"
      ]
    }
  ],
  "trends": {
    "improving": ["JavaScript", "Python", "Go"],
    "declining": ["Java"],
    "stable": [".NET", "Rust", "C++", "Ruby"]
  }
}
```

**GraphQL Query**:
```graphql
query DeveloperExperience($techStack: String, $timeRange: String!) {
  developerExperience(techStack: $techStack, timeRange: $timeRange) {
    overallDxScore
    techStacks {
      technology
      icon
      dxScore
      developerCount
      satisfactionBreakdown {
        buildTime
        deploymentEase
        platformUsability
        toolingEffectiveness
      }
      topPainPoints
    }
    trends {
      improving
      declining
      stable
    }
  }
}
```

---

### 4. Throughput Analytics by Tech Stack

**Data Collection**:
- Total builds per tech stack
- Total deployments per tech stack
- Build-to-deploy efficiency ratio
- Average build time
- Average deployment time

**REST API Endpoint**:
```http
GET /api/v1/analytics/throughput
Query Parameters:
  - tech_stack: string (optional)
  - time_range: string (default: 30d)
  - aggregation: string (default: monthly)

Response:
{
  "summary": {
    "total_builds": 9131,
    "total_deploys": 6191,
    "overall_efficiency": 90.2
  },
  "tech_stacks": [
    {
      "technology": "JavaScript",
      "icon": "⚡",
      "builds": 2105,
      "deploys": 1654,
      "efficiency": 94,
      "avg_build_time_minutes": 8.2,
      "avg_deploy_time_minutes": 3.4,
      "developer_count": 127
    },
    {
      "technology": "Python",
      "icon": "🐍",
      "builds": 1450,
      "deploys": 1021,
      "efficiency": 87,
      "avg_build_time_minutes": 6.7,
      "avg_deploy_time_minutes": 4.1,
      "developer_count": 89
    }
  ],
  "comparison": {
    "highest_efficiency": "JavaScript (94%)",
    "highest_throughput": "JavaScript (2105 builds)",
    "fastest_build": "Go (5.2 min)",
    "fastest_deploy": "JavaScript (3.4 min)"
  }
}
```

**Visualization (Bar Chart)**:
```
THROUGHPUT BY TECH STACK (Last 30 Days)
─────────────────────────────────────────────────────────────
JavaScript ████████████████████████ 2105 builds | 1654 deploys
Python     ████████████████░░░░░░░░ 1450 builds | 1021 deploys
Java       ██████████████░░░░░░░░░░ 1240 builds |  856 deploys
.NET       ████████████░░░░░░░░░░░░  982 builds |  734 deploys
Go         █████████░░░░░░░░░░░░░░░  743 builds |  612 deploys
C++        ███████░░░░░░░░░░░░░░░░░  621 builds |  502 deploys
Ruby       ██████░░░░░░░░░░░░░░░░░░  534 builds |  423 deploys
Rust       ████░░░░░░░░░░░░░░░░░░░░  456 builds |  389 deploys
─────────────────────────────────────────────────────────────
         0        500      1000     1500     2000     2500
```

---

### 5. Stability, Efficiency & Quality (SEQ) Metrics

**Data Collection**:

**Stability**:
- Uptime percentage
- Mean Time Between Failures (MTBF)
- Mean Time To Recovery (MTTR)

**Efficiency**:
- Lead time (commit to production)
- Cycle time (dev start to complete)
- Throughput (deploys per week)

**Quality**:
- Build success rate
- Test coverage percentage
- Code quality grade (A-F)

**REST API Endpoint**:
```http
GET /api/v1/analytics/seq-metrics
Query Parameters:
  - dimension: string (optional: stability, efficiency, quality)
  - time_range: string (default: 30d)

Response:
{
  "stability": {
    "score": 94.2,
    "uptime": 99.1,
    "mtbf_hours": 168,
    "mttr_minutes": 23,
    "incidents_last_month": 12,
    "p1_incidents": 2
  },
  "efficiency": {
    "score": 89.7,
    "lead_time_hours": 4.2,
    "cycle_time_hours": 2.8,
    "throughput_per_week": 247,
    "deployment_frequency": "multiple per day",
    "change_failure_rate": 5.3
  },
  "quality": {
    "score": 92.3,
    "success_rate": 92.3,
    "test_coverage": 87,
    "code_quality_grade": "A",
    "critical_bugs_open": 3,
    "technical_debt_hours": 145
  },
  "composite_score": 92.1,
  "trends": {
    "stability": "improving",
    "efficiency": "stable",
    "quality": "improving"
  }
}
```

**GraphQL Query**:
```graphql
query SEQMetrics($dimension: String, $timeRange: String!) {
  seqMetrics(dimension: $dimension, timeRange: $timeRange) {
    stability {
      score
      uptime
      mtbfHours
      mttrMinutes
      incidentsLastMonth
      p1Incidents
    }
    efficiency {
      score
      leadTimeHours
      cycleTimeHours
      throughputPerWeek
      deploymentFrequency
      changeFailureRate
    }
    quality {
      score
      successRate
      testCoverage
      codeQualityGrade
      criticalBugsOpen
      technicalDebtHours
    }
    compositeScore
    trends {
      stability
      efficiency
      quality
    }
  }
}
```

**Visualization (Radar Chart)**:
```
     SEQ METRICS COMPOSITE VIEW

           Uptime
              ▲
              │
              │   ●
              │  ╱ ╲
              │ ╱   ╲
              │╱     ╲
   MTTR ◄─────●───────● Lead Time
              │╲     ╱
              │ ╲   ╱
              │  ╲ ╱
              │   ●
              │
              ▼
         Success Rate

Score: 94.2 (Stability) | 89.7 (Efficiency) | 92.3 (Quality)
Composite: 92.1 / 100
```

---

### 6. Cost Analytics

**Data Collection**:
- Total license count and utilization
- Monthly OPEX (operating expenses)
- Cost per deployment
- Cost breakdown by platform/tool
- License waste (unused seats)

**REST API Endpoint**:
```http
GET /api/v1/analytics/cost-analytics
Query Parameters:
  - time_range: string (default: 30d)
  - breakdown_by: string (platform, team, project)

Response:
{
  "summary": {
    "total_licenses": 1247,
    "license_utilization": 87,
    "unused_licenses": 162,
    "monthly_opex": 142000,
    "cost_per_deploy": 23.40,
    "annual_run_rate": 1704000
  },
  "platform_breakdown": [
    {
      "platform": "GitHub Enterprise",
      "monthly_cost": 42000,
      "percent_of_total": 29.6,
      "licenses": 450,
      "utilization": 92,
      "cost_per_license": 93.33
    },
    {
      "platform": "Harness CD",
      "monthly_cost": 38000,
      "percent_of_total": 26.8,
      "licenses": 200,
      "utilization": 85,
      "cost_per_license": 190.00
    },
    {
      "platform": "Fortify + Sonatype",
      "monthly_cost": 28000,
      "percent_of_total": 19.7,
      "licenses": 300,
      "utilization": 78,
      "cost_per_license": 93.33
    }
  ],
  "optimization_opportunities": [
    {
      "area": "Unused GitHub licenses",
      "potential_savings_monthly": 7466,
      "recommendation": "Reclaim 80 unused seats"
    },
    {
      "area": "Harness license tier",
      "potential_savings_monthly": 5000,
      "recommendation": "Downgrade 30 power users to basic"
    }
  ]
}
```

**Visualization (Cost Breakdown)**:
```
MONTHLY OPEX: $142K
────────────────────────────────────────────────
GitHub Enterprise    ████████████████░ $42K (29.6%)
Harness CD          ██████████████░░░ $38K (26.8%)
Fortify + Sonatype  ████████████░░░░░ $28K (19.7%)
Nexus Repository    ████████░░░░░░░░░ $18K (12.7%)
Wiz Cloud Security  ██████░░░░░░░░░░░ $12K (8.5%)
Cloud Dev Env       ██░░░░░░░░░░░░░░░  $4K (2.8%)
────────────────────────────────────────────────

License Utilization: 87% [████████████████░░░░] 1247 seats
Cost Per Deploy: $23.40
Optimization Potential: $12.5K/month
```

---

### 7. Revenue Impact Analytics

**Data Collection**:
- Total platform revenue
- Revenue per deployment
- Revenue per developer
- Deployment velocity impact on revenue
- Per-developer productivity to revenue correlation
- Product line revenue attribution

**REST API Endpoint**:
```http
GET /api/v1/analytics/revenue-impact
Query Parameters:
  - time_range: string (default: 1y)
  - breakdown_by: string (tech_stack, product_line, team)

Response:
{
  "summary": {
    "total_platform_revenue": 847000000,
    "revenue_per_deploy": 143000,
    "revenue_per_developer": 2100000,
    "deploy_velocity_impact_yoy": 18,
    "total_deploys_this_year": 5923
  },
  "tech_stack_revenue": [
    {
      "technology": "JavaScript",
      "icon": "⚡",
      "developer_count": 127,
      "deploys_per_month": 1654,
      "revenue_per_dev": 2400000,
      "total_revenue": 304800000,
      "percent_of_total": 36.0
    },
    {
      "technology": "Python",
      "icon": "🐍",
      "developer_count": 89,
      "deploys_per_month": 1021,
      "revenue_per_dev": 2200000,
      "total_revenue": 195800000,
      "percent_of_total": 23.1
    }
  ],
  "product_line_revenue": [
    {
      "product": "Digital Banking Platform",
      "revenue": 287000000,
      "deploys": 1247,
      "growth_yoy": 24,
      "team_count": 8
    },
    {
      "product": "Payment Processing Engine",
      "revenue": 213000000,
      "deploys": 892,
      "growth_yoy": 19,
      "team_count": 6
    }
  ],
  "correlation": {
    "deploy_frequency_to_revenue": 0.87,
    "developer_productivity_to_revenue": 0.92,
    "platform_uptime_to_revenue": 0.76
  }
}
```

**GraphQL Query**:
```graphql
query RevenueImpact($timeRange: String!, $breakdownBy: String) {
  revenueImpact(timeRange: $timeRange, breakdownBy: $breakdownBy) {
    summary {
      totalPlatformRevenue
      revenuePerDeploy
      revenuePerDeveloper
      deployVelocityImpactYoy
      totalDeploysThisYear
    }
    techStackRevenue {
      technology
      icon
      developerCount
      deploysPerMonth
      revenuePerDev
      totalRevenue
      percentOfTotal
    }
    productLineRevenue {
      product
      revenue
      deploys
      growthYoy
      teamCount
    }
    correlation {
      deployFrequencyToRevenue
      developerProductivityToRevenue
      platformUptimeToRevenue
    }
  }
}
```

**Visualization (Revenue Impact)**:
```
REVENUE IMPACT ANALYTICS
═══════════════════════════════════════════════════════════
Total Platform Revenue: $847M ARR

Revenue Drivers:
┌───────────────────────────────────────────────────────┐
│ Revenue per Deploy:     $143K  [↑ +18% YoY]           │
│ Revenue per Developer:  $2.1M  [↑ +12% YoY]           │
│ Deploy Velocity Impact: +18%   [Strong correlation]   │
└───────────────────────────────────────────────────────┘

Top Revenue-Generating Tech Stacks:
JavaScript  ████████████████████████ $304.8M (36.0%)
Python      ██████████████░░░░░░░░░░ $195.8M (23.1%)
Java        ████████████░░░░░░░░░░░░ $159.6M (18.8%)
.NET        █████████░░░░░░░░░░░░░░░ $121.6M (14.4%)

Correlation Analysis:
Deploy Frequency ─────────── Revenue: 0.87 (Strong)
Developer Productivity ───── Revenue: 0.92 (Very Strong)
Platform Uptime ─────────── Revenue: 0.76 (Moderate)
```

---

### 8. Incident & Change Ticket Analytics

**Data Collection**:
- Total change tickets (emergency, standard, normal)
- Total incidents (P1-critical, P2-high, P3-medium)
- Incident resolution time
- Ticket backlog trends
- MTTR by severity

**REST API Endpoint**:
```http
GET /api/v1/analytics/incident-metrics
Query Parameters:
  - type: string (change_tickets, incidents, all)
  - time_range: string (default: 30d)
  - severity: string (optional)

Response:
{
  "change_tickets": {
    "total_this_month": 127,
    "completed": 94,
    "in_progress": 23,
    "pending": 10,
    "by_priority": {
      "emergency": 12,
      "standard": 89,
      "normal": 26
    },
    "avg_completion_time_hours": 36
  },
  "incidents": {
    "total_this_month": 34,
    "resolved": 28,
    "active": 4,
    "critical": 2,
    "by_severity": {
      "p1_critical": 2,
      "p2_high": 8,
      "p3_medium": 24
    },
    "avg_resolution_time_hours": {
      "p1": 2.3,
      "p2": 8.7,
      "p3": 24.1
    }
  },
  "trends": {
    "change_tickets_mom": -8,
    "incidents_mom": -12,
    "mttr_trend": "improving"
  }
}
```

---

### 9. Environment Deployment Analytics

**Data Collection**:
- Deployment success by environment type
- On-premises data centers
- Private cloud (VMware Tanzu, Orange.OS)
- Public cloud (AWS, Azure, GCP)
- Success rates per environment

**REST API Endpoint**:
```http
GET /api/v1/analytics/environment-metrics
Query Parameters:
  - environment_type: string (on_prem, private_cloud, public_cloud)
  - time_range: string (default: 30d)

Response:
{
  "summary": {
    "total_deployments": 1014,
    "overall_success_rate": 94.7,
    "environments_monitored": 8
  },
  "on_premises": {
    "total_deployments": 270,
    "avg_success_rate": 92.5,
    "environments": [
      {
        "name": "DC-East-01",
        "deployments": 142,
        "success_rate": 94,
        "status": "operational"
      },
      {
        "name": "DC-West-02",
        "deployments": 128,
        "success_rate": 91,
        "status": "operational"
      }
    ]
  },
  "private_cloud": {
    "total_deployments": 156,
    "avg_success_rate": 94.5,
    "environments": [
      {
        "name": "VMware Tanzu",
        "deployments": 89,
        "success_rate": 96,
        "status": "operational"
      },
      {
        "name": "Orange.OS",
        "deployments": 67,
        "success_rate": 93,
        "status": "operational"
      }
    ]
  },
  "public_cloud": {
    "total_deployments": 588,
    "avg_success_rate": 95.3,
    "environments": [
      {
        "name": "AWS",
        "deployments": 234,
        "success_rate": 97,
        "status": "operational"
      },
      {
        "name": "Azure",
        "deployments": 198,
        "success_rate": 95,
        "status": "operational"
      },
      {
        "name": "GCP",
        "deployments": 156,
        "success_rate": 94,
        "status": "operational"
      }
    ]
  }
}
```

---

## Data Visualization Capabilities

### Dashboard Templates

**Executive Dashboard**:
```
┌────────────────────────────────────────────────────────────┐
│ PLATFORM ENGINEERING EXECUTIVE DASHBOARD                   │
├────────────────────────────────────────────────────────────┤
│                                                             │
│ Platform Health:        98.9% ✓    Revenue Impact: $847M   │
│ Pipeline Availability:  98.5% ✓    Deploy Velocity: +18%   │
│ Developer Experience:   82/100      Cost per Deploy: $23.40│
│ Deployment Frequency:   247/week    License Util: 87%      │
│                                                             │
│ ┌─────────── SEQ METRICS ────────────┐                     │
│ │ Stability:  94.2% [████████████░░] │                     │
│ │ Efficiency: 89.7% [███████████░░░] │                     │
│ │ Quality:    92.3% [████████████░░] │                     │
│ └────────────────────────────────────┘                     │
│                                                             │
│ ┌──── TECH STACK THROUGHPUT (30d) ───┐                     │
│ │ JavaScript  2105 ████████████████░░ │                     │
│ │ Python      1450 ████████████░░░░░░ │                     │
│ │ Java        1240 ███████████░░░░░░░ │                     │
│ │ .NET         982 █████████░░░░░░░░░ │                     │
│ └────────────────────────────────────┘                     │
│                                                             │
│ Active Incidents: 4 (2 P1) | Change Tickets: 33 pending    │
└────────────────────────────────────────────────────────────┘
```

**Operations Dashboard**:
```
┌────────────────────────────────────────────────────────────┐
│ PLATFORM OPERATIONS REAL-TIME DASHBOARD                    │
├────────────────────────────────────────────────────────────┤
│ Platform Stack Status:                                      │
│ ✓ GitHub (99.9%)    ✓ Harness (98.7%)    ⚠ Sonatype (96%)│
│ ✓ Nexus (99.5%)     ✓ Fortify (99.2%)    ✓ Wiz (99.6%)   │
│                                                             │
│ Pipeline Metrics (Last Hour):                               │
│ Builds Started:  127    Builds Completed: 118              │
│ Success Rate:    92.9%  Avg Build Time: 7.2 min            │
│ Deploys:         24     Deploy Success: 95.8%              │
│                                                             │
│ Active Alerts:                                              │
│ 🔴 P1: 2 | 🟡 P2: 5 | 🟢 P3: 12                           │
│                                                             │
│ ┌─── COST TRACKING (MTD) ────────┐                         │
│ │ OPEX Spent:    $98K / $142K     │                         │
│ │ Budget:        69% [██████████] │                         │
│ │ Deploys:       1,842            │                         │
│ │ Cost/Deploy:   $53.20           │                         │
│ └─────────────────────────────────┘                         │
└────────────────────────────────────────────────────────────┘
```

### Chart Types Supported

1. **Time Series Line Charts**: Trend analysis over time
2. **Bar Charts**: Comparative metrics across tech stacks
3. **Pie/Donut Charts**: Distribution breakdowns (cost, revenue)
4. **Radar Charts**: Multi-dimensional SEQ metrics
5. **Heat Maps**: Activity patterns by hour/day/week
6. **Gauge Charts**: Single metric status (uptime, success rate)
7. **Scatter Plots**: Correlation analysis
8. **Funnel Charts**: Conversion metrics (build → deploy → success)

---

## Integration Patterns

### REST API Integration

**Authentication**:
```http
Authorization: Bearer <JWT_TOKEN>
X-API-Key: <API_KEY>
```

**Webhook Support**:
```http
POST /api/v1/webhooks/analytics
{
  "event_type": "threshold_breach",
  "metric": "pipeline_availability",
  "current_value": 97.2,
  "threshold": 98.0,
  "timestamp": "2026-01-03T10:30:00Z"
}
```

### GraphQL Integration

**Subscription Support (Real-time)**:
```graphql
subscription PlatformMetricsLive {
  platformMetricsUpdated {
    pipelineAvailability
    buildSuccessRate
    deploymentFrequency
    timestamp
  }
}
```

**Batch Queries**:
```graphql
query ComprehensiveAnalytics {
  platformStack { ... }
  pipelineMetrics { ... }
  developerExperience { ... }
  costAnalytics { ... }
  revenueImpact { ... }
}
```

---

## Alerting & Threshold Configuration

**Threshold-Based Alerts**:
```json
{
  "alert_rules": [
    {
      "metric": "pipeline_availability",
      "condition": "below",
      "threshold": 98.0,
      "severity": "high",
      "notification_channels": ["slack", "pagerduty"]
    },
    {
      "metric": "build_success_rate",
      "condition": "below",
      "threshold": 90.0,
      "severity": "medium",
      "notification_channels": ["slack"]
    },
    {
      "metric": "cost_per_deploy",
      "condition": "above",
      "threshold": 30.0,
      "severity": "low",
      "notification_channels": ["email"]
    }
  ]
}
```

---

## Export & Reporting

**Scheduled Reports**:
```bash
/platform-analytics \
  --metric-type "all" \
  --time-range "30d" \
  --format "report" \
  --export "pdf" \
  --schedule "weekly" \
  --recipients "leadership@company.com"
```

**CSV Export Example**:
```csv
tech_stack,builds,deploys,efficiency,dx_score,revenue_per_dev
JavaScript,2105,1654,94,88,2400000
Python,1450,1021,87,84,2200000
Java,1240,856,89,79,2100000
```

**PDF Report Sections**:
1. Executive Summary
2. Platform Health Overview
3. Pipeline Performance Trends
4. Developer Experience Insights
5. Cost & ROI Analysis
6. Revenue Impact Correlation
7. Recommendations & Action Items

---

## Advanced Analytics Features

### Predictive Analytics

**Forecast Models**:
- Predict future deployment frequency based on trends
- Forecast cost growth based on usage patterns
- Predict capacity needs based on developer growth

**Example**:
```http
GET /api/v1/analytics/forecast
Query: metric=deployment_frequency&horizon=90d

Response:
{
  "current_weekly_average": 247,
  "forecast_30d": 265,
  "forecast_60d": 278,
  "forecast_90d": 294,
  "confidence_interval": [260, 310],
  "model_accuracy": 0.89
}
```

### Anomaly Detection

**Automated Anomaly Detection**:
```json
{
  "anomalies_detected": [
    {
      "metric": "build_success_rate",
      "timestamp": "2026-01-03T08:15:00Z",
      "expected_value": 92.3,
      "actual_value": 78.4,
      "severity": "high",
      "possible_causes": [
        "Dependency repository outage",
        "Breaking change in toolchain"
      ]
    }
  ]
}
```

---

## Performance Considerations

**API Rate Limits**:
- REST API: 1000 requests/hour per API key
- GraphQL: 500 queries/hour per API key
- Webhook: 100 events/minute

**Data Retention**:
- Real-time metrics: 24 hours
- Hourly aggregations: 90 days
- Daily aggregations: 2 years
- Monthly aggregations: 5 years

**Query Optimization**:
- Use aggregation parameters to reduce data transfer
- Leverage GraphQL field selection to request only needed data
- Use time-range filters to limit dataset size
- Cache frequently accessed metrics (Redis/Memcached)

---

## Related Skills

- `/exec-briefing` - Generate executive reports from analytics data
- `/value-narrative` - Create narratives from platform metrics
- `/calculate-roi` - ROI calculations using platform analytics
- `/risk-assessment` - Risk analysis using stability/quality metrics

---

## Related Agents

- `@governance-agent` - Executive reporting and KPI tracking
- `@financial-agent` - Cost optimization and ROI analysis
- `@delivery-agent` - Pipeline performance and throughput tracking
- `@risk-agent` - Stability and incident trend analysis

---

## Implementation Notes

This skill provides comprehensive analytics across the platform engineering lifecycle:

1. **Data Collection Layer**: REST/GraphQL APIs collect metrics from DevOps platforms
2. **Storage Layer**: Time-series database (InfluxDB, TimescaleDB) for metric storage
3. **Processing Layer**: Stream processing (Kafka, Flink) for real-time aggregation
4. **Visualization Layer**: Dashboard frameworks (Grafana, custom React)
5. **Alert Layer**: Threshold-based alerting (Prometheus Alertmanager)
6. **Export Layer**: Scheduled reports (PDF, CSV, Excel)

**Technology Stack**:
- Backend: Node.js/Python FastAPI
- Database: PostgreSQL + TimescaleDB extension
- Cache: Redis
- Message Queue: Kafka
- Visualization: Grafana + custom React dashboards
- API: REST (Express) + GraphQL (Apollo Server)

**Data Sources**:
- GitHub API (commits, PRs, builds)
- Harness CD API (deployments, pipelines)
- Nexus API (artifact metrics)
- Fortify/Sonatype APIs (security scans)
- Wiz API (cloud security)
- Custom instrumentation (OpenTelemetry)

---

**Skill Owner**: Platform Program Management Repository
**Last Updated**: January 2026
**Version**: 1.0
