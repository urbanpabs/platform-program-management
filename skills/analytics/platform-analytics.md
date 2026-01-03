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
- Backend: Flask/Python FastAPI/Node.js Express
- Database: PostgreSQL + TimescaleDB extension
- Cache: Redis
- Message Queue: Kafka
- Visualization: Grafana + custom React dashboards
- API: REST (Express/Flask) + GraphQL (Apollo Server)

**Data Sources**:
- GitHub API (commits, PRs, builds)
- Harness CD API (deployments, pipelines)
- Nexus API (artifact metrics)
- Fortify/Sonatype APIs (security scans)
- Wiz API (cloud security)
- Custom instrumentation (OpenTelemetry)

---

## Flask Backend Implementation

### Flask REST API Server

**Project Structure**:
```
platform-analytics-api/
├── app/
│   ├── __init__.py
│   ├── config.py
│   ├── models/
│   │   ├── __init__.py
│   │   ├── platform_stack.py
│   │   ├── pipeline_metrics.py
│   │   ├── developer_experience.py
│   │   └── revenue_impact.py
│   ├── routes/
│   │   ├── __init__.py
│   │   ├── analytics.py
│   │   ├── platform_stack.py
│   │   ├── pipeline_metrics.py
│   │   ├── developer_experience.py
│   │   ├── cost_analytics.py
│   │   └── revenue_impact.py
│   ├── services/
│   │   ├── __init__.py
│   │   ├── data_collector.py
│   │   ├── aggregator.py
│   │   └── forecaster.py
│   └── utils/
│       ├── __init__.py
│       ├── auth.py
│       └── validators.py
├── tests/
│   ├── test_analytics.py
│   └── test_pipeline_metrics.py
├── requirements.txt
├── wsgi.py
└── README.md
```

**Core Flask Application (`app/__init__.py`)**:
```python
from flask import Flask
from flask_cors import CORS
from flask_sqlalchemy import SQLAlchemy
from flask_caching import Cache
from flask_limiter import Limiter
from flask_limiter.util import get_remote_address

db = SQLAlchemy()
cache = Cache()
limiter = Limiter(
    key_func=get_remote_address,
    default_limits=["1000 per hour"]
)

def create_app(config_name='development'):
    app = Flask(__name__)
    app.config.from_object(f'app.config.{config_name}')

    # Enable CORS for React/Vite frontend
    CORS(app, resources={
        r"/api/*": {
            "origins": [
                "http://localhost:5173",  # Vite default
                "http://localhost:3000",  # React default
                "http://localhost:4200",  # Angular default
                "http://localhost:8080"   # Vue default
            ]
        }
    })

    # Initialize extensions
    db.init_app(app)
    cache.init_app(app)
    limiter.init_app(app)

    # Register blueprints
    from app.routes.analytics import analytics_bp
    from app.routes.platform_stack import platform_stack_bp
    from app.routes.pipeline_metrics import pipeline_metrics_bp
    from app.routes.developer_experience import dx_bp
    from app.routes.cost_analytics import cost_bp
    from app.routes.revenue_impact import revenue_bp

    app.register_blueprint(analytics_bp, url_prefix='/api/v1')
    app.register_blueprint(platform_stack_bp, url_prefix='/api/v1')
    app.register_blueprint(pipeline_metrics_bp, url_prefix='/api/v1')
    app.register_blueprint(dx_bp, url_prefix='/api/v1')
    app.register_blueprint(cost_bp, url_prefix='/api/v1')
    app.register_blueprint(revenue_bp, url_prefix='/api/v1')

    return app
```

**Configuration (`app/config.py`)**:
```python
import os
from datetime import timedelta

class Config:
    SECRET_KEY = os.environ.get('SECRET_KEY') or 'dev-secret-key'
    SQLALCHEMY_DATABASE_URI = os.environ.get('DATABASE_URL') or \
        'postgresql://user:password@localhost/platform_analytics'
    SQLALCHEMY_TRACK_MODIFICATIONS = False

    # Cache configuration
    CACHE_TYPE = 'redis'
    CACHE_REDIS_URL = os.environ.get('REDIS_URL') or 'redis://localhost:6379/0'
    CACHE_DEFAULT_TIMEOUT = 300

    # API rate limiting
    RATELIMIT_STORAGE_URL = os.environ.get('REDIS_URL') or 'redis://localhost:6379/1'

    # JWT authentication
    JWT_SECRET_KEY = os.environ.get('JWT_SECRET_KEY') or 'jwt-secret-key'
    JWT_ACCESS_TOKEN_EXPIRES = timedelta(hours=1)

class DevelopmentConfig(Config):
    DEBUG = True

class ProductionConfig(Config):
    DEBUG = False

class TestingConfig(Config):
    TESTING = True
    SQLALCHEMY_DATABASE_URI = 'sqlite:///:memory:'
```

**Platform Stack Analytics Route (`app/routes/platform_stack.py`)**:
```python
from flask import Blueprint, request, jsonify
from app.services.data_collector import PlatformStackCollector
from app.utils.auth import require_api_key
from app import cache

platform_stack_bp = Blueprint('platform_stack', __name__)

@platform_stack_bp.route('/analytics/platform-stack', methods=['GET'])
@require_api_key
@cache.cached(timeout=300, query_string=True)
def get_platform_stack_health():
    """
    Get platform stack health metrics

    Query Parameters:
        - platform: string (optional, filter by platform name)
        - time_range: string (default: 24h)
        - aggregation: string (default: hourly)
    """
    platform = request.args.get('platform')
    time_range = request.args.get('time_range', '24h')
    aggregation = request.args.get('aggregation', 'hourly')

    collector = PlatformStackCollector()
    data = collector.get_health_metrics(
        platform=platform,
        time_range=time_range,
        aggregation=aggregation
    )

    return jsonify(data), 200

@platform_stack_bp.route('/analytics/platform-stack/status', methods=['GET'])
@require_api_key
def get_platform_status():
    """Get real-time platform status"""
    collector = PlatformStackCollector()
    status = collector.get_real_time_status()
    return jsonify(status), 200
```

**Pipeline Metrics Route (`app/routes/pipeline_metrics.py`)**:
```python
from flask import Blueprint, request, jsonify
from app.services.data_collector import PipelineMetricsCollector
from app.utils.auth import require_api_key
from app import cache

pipeline_metrics_bp = Blueprint('pipeline_metrics', __name__)

@pipeline_metrics_bp.route('/analytics/pipeline-metrics', methods=['GET'])
@require_api_key
@cache.cached(timeout=60, query_string=True)
def get_pipeline_metrics():
    """
    Get pipeline performance metrics

    Query Parameters:
        - time_range: string (default: 7d)
        - tech_stack: string (optional)
        - aggregation: string (default: daily)
    """
    time_range = request.args.get('time_range', '7d')
    tech_stack = request.args.get('tech_stack')
    aggregation = request.args.get('aggregation', 'daily')

    collector = PipelineMetricsCollector()
    data = collector.get_metrics(
        time_range=time_range,
        tech_stack=tech_stack,
        aggregation=aggregation
    )

    return jsonify(data), 200

@pipeline_metrics_bp.route('/analytics/pipeline-metrics/real-time', methods=['GET'])
@require_api_key
def get_real_time_pipeline_metrics():
    """Get real-time pipeline metrics (no cache)"""
    collector = PipelineMetricsCollector()
    data = collector.get_real_time_metrics()
    return jsonify(data), 200
```

**Developer Experience Route (`app/routes/developer_experience.py`)**:
```python
from flask import Blueprint, request, jsonify
from app.services.data_collector import DeveloperExperienceCollector
from app.utils.auth import require_api_key
from app import cache

dx_bp = Blueprint('developer_experience', __name__)

@dx_bp.route('/analytics/developer-experience', methods=['GET'])
@require_api_key
@cache.cached(timeout=3600, query_string=True)
def get_developer_experience():
    """
    Get developer experience scores

    Query Parameters:
        - tech_stack: string (optional, filter by tech)
        - time_range: string (default: 30d)
    """
    tech_stack = request.args.get('tech_stack')
    time_range = request.args.get('time_range', '30d')

    collector = DeveloperExperienceCollector()
    data = collector.get_dx_scores(
        tech_stack=tech_stack,
        time_range=time_range
    )

    return jsonify(data), 200
```

**Authentication Utility (`app/utils/auth.py`)**:
```python
from functools import wraps
from flask import request, jsonify
import os

def require_api_key(f):
    @wraps(f)
    def decorated_function(*args, **kwargs):
        api_key = request.headers.get('X-API-Key')

        if not api_key:
            return jsonify({'error': 'API key required'}), 401

        # Validate API key (in production, check against database)
        valid_api_keys = os.environ.get('VALID_API_KEYS', '').split(',')
        if api_key not in valid_api_keys:
            return jsonify({'error': 'Invalid API key'}), 403

        return f(*args, **kwargs)

    return decorated_function
```

**Requirements (`requirements.txt`)**:
```txt
Flask==3.0.0
Flask-CORS==4.0.0
Flask-SQLAlchemy==3.1.1
Flask-Caching==2.1.0
Flask-Limiter==3.5.0
psycopg2-binary==2.9.9
redis==5.0.1
requests==2.31.0
python-dotenv==1.0.0
gunicorn==21.2.0
```

**WSGI Entry Point (`wsgi.py`)**:
```python
from app import create_app
import os

app = create_app(os.environ.get('FLASK_ENV', 'production'))

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)
```

---

## React/Vite Frontend Integration

### Vite React Dashboard

**Project Structure**:
```
platform-analytics-dashboard/
├── src/
│   ├── components/
│   │   ├── PlatformStackHealth.jsx
│   │   ├── PipelineMetrics.jsx
│   │   ├── DeveloperExperience.jsx
│   │   ├── ThroughputChart.jsx
│   │   ├── CostAnalytics.jsx
│   │   └── RevenueImpact.jsx
│   ├── services/
│   │   └── analyticsApi.js
│   ├── hooks/
│   │   └── useAnalytics.js
│   ├── App.jsx
│   ├── main.jsx
│   └── index.css
├── package.json
├── vite.config.js
└── README.md
```

**Analytics API Service (`src/services/analyticsApi.js`)**:
```javascript
import axios from 'axios';

const API_BASE_URL = import.meta.env.VITE_API_BASE_URL || 'http://localhost:5000/api/v1';
const API_KEY = import.meta.env.VITE_API_KEY;

const apiClient = axios.create({
  baseURL: API_BASE_URL,
  headers: {
    'Content-Type': 'application/json',
    'X-API-Key': API_KEY,
  },
});

export const analyticsApi = {
  // Platform Stack Health
  getPlatformStackHealth: (params = {}) =>
    apiClient.get('/analytics/platform-stack', { params }),

  getPlatformStatus: () =>
    apiClient.get('/analytics/platform-stack/status'),

  // Pipeline Metrics
  getPipelineMetrics: (params = {}) =>
    apiClient.get('/analytics/pipeline-metrics', { params }),

  getRealTimePipelineMetrics: () =>
    apiClient.get('/analytics/pipeline-metrics/real-time'),

  // Developer Experience
  getDeveloperExperience: (params = {}) =>
    apiClient.get('/analytics/developer-experience', { params }),

  // Throughput
  getThroughput: (params = {}) =>
    apiClient.get('/analytics/throughput', { params }),

  // SEQ Metrics
  getSEQMetrics: (params = {}) =>
    apiClient.get('/analytics/seq-metrics', { params }),

  // Cost Analytics
  getCostAnalytics: (params = {}) =>
    apiClient.get('/analytics/cost-analytics', { params }),

  // Revenue Impact
  getRevenueImpact: (params = {}) =>
    apiClient.get('/analytics/revenue-impact', { params }),
};
```

**Custom React Hook (`src/hooks/useAnalytics.js`)**:
```javascript
import { useState, useEffect } from 'react';
import { analyticsApi } from '../services/analyticsApi';

export const useAnalytics = (metricType, params = {}, refreshInterval = null) => {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  const fetchData = async () => {
    try {
      setLoading(true);
      let response;

      switch (metricType) {
        case 'platform-stack':
          response = await analyticsApi.getPlatformStackHealth(params);
          break;
        case 'pipeline-metrics':
          response = await analyticsApi.getPipelineMetrics(params);
          break;
        case 'developer-experience':
          response = await analyticsApi.getDeveloperExperience(params);
          break;
        case 'throughput':
          response = await analyticsApi.getThroughput(params);
          break;
        case 'seq-metrics':
          response = await analyticsApi.getSEQMetrics(params);
          break;
        case 'cost-analytics':
          response = await analyticsApi.getCostAnalytics(params);
          break;
        case 'revenue-impact':
          response = await analyticsApi.getRevenueImpact(params);
          break;
        default:
          throw new Error(`Unknown metric type: ${metricType}`);
      }

      setData(response.data);
      setError(null);
    } catch (err) {
      setError(err.message);
    } finally {
      setLoading(false);
    }
  };

  useEffect(() => {
    fetchData();

    // Auto-refresh if interval specified
    if (refreshInterval) {
      const interval = setInterval(fetchData, refreshInterval);
      return () => clearInterval(interval);
    }
  }, [metricType, JSON.stringify(params), refreshInterval]);

  return { data, loading, error, refetch: fetchData };
};
```

**Pipeline Metrics Component (`src/components/PipelineMetrics.jsx`)**:
```jsx
import React from 'react';
import { useAnalytics } from '../hooks/useAnalytics';

export const PipelineMetrics = ({ timeRange = '7d', techStack = null }) => {
  const { data, loading, error } = useAnalytics('pipeline-metrics',
    { time_range: timeRange, tech_stack: techStack },
    60000 // Refresh every 60 seconds
  );

  if (loading) return <div className="loading">Loading pipeline metrics...</div>;
  if (error) return <div className="error">Error: {error}</div>;
  if (!data) return null;

  return (
    <div className="pipeline-metrics">
      <h2>Pipeline Metrics</h2>

      <div className="metrics-grid">
        <div className="metric-card">
          <h3>Pipeline Availability</h3>
          <div className="metric-value">{data.pipeline_availability.current}%</div>
          <div className="metric-target">Target: {data.pipeline_availability.target}%</div>
          <div className="progress-bar">
            <div
              className="progress-fill"
              style={{ width: `${data.pipeline_availability.current}%` }}
            />
          </div>
        </div>

        <div className="metric-card">
          <h3>Build Success Rate</h3>
          <div className="metric-value">{data.build_success_rate.current}%</div>
          <div className="metric-details">
            {data.build_success_rate.successful_builds} / {data.build_success_rate.total_builds}
          </div>
          <div className="progress-bar">
            <div
              className="progress-fill success"
              style={{ width: `${data.build_success_rate.current}%` }}
            />
          </div>
        </div>

        <div className="metric-card">
          <h3>Deployment Frequency</h3>
          <div className="metric-value">{data.deployment_frequency.total_deploys_this_week}</div>
          <div className="metric-sublabel">deploys this week</div>
          <div className="metric-change">
            {data.deployment_frequency.change_from_last_week > 0 ? '↑' : '↓'}
            {Math.abs(data.deployment_frequency.change_from_last_week)} vs last week
          </div>
        </div>

        <div className="metric-card">
          <h3>Cloud Dev Env Health</h3>
          <div className="metric-value">{data.cloud_dev_env_health.current}%</div>
          <div className="metric-details">
            {data.cloud_dev_env_health.active_environments} active environments
          </div>
          <div className="progress-bar">
            <div
              className="progress-fill"
              style={{ width: `${data.cloud_dev_env_health.current}%` }}
            />
          </div>
        </div>
      </div>
    </div>
  );
};
```

**Developer Experience Component (`src/components/DeveloperExperience.jsx`)**:
```jsx
import React from 'react';
import { useAnalytics } from '../hooks/useAnalytics';

export const DeveloperExperience = ({ techStack = null }) => {
  const { data, loading, error } = useAnalytics('developer-experience',
    { tech_stack: techStack, time_range: '30d' }
  );

  if (loading) return <div className="loading">Loading DX scores...</div>;
  if (error) return <div className="error">Error: {error}</div>;
  if (!data) return null;

  return (
    <div className="developer-experience">
      <h2>Developer Experience Scores</h2>
      <div className="overall-score">
        Overall DX Score: <span className="score">{data.overall_dx_score}/100</span>
      </div>

      <div className="dx-grid">
        {data.tech_stacks.map((stack) => (
          <div key={stack.technology} className="dx-card">
            <div className="dx-header">
              <span className="dx-icon">{stack.icon}</span>
              <span className="dx-tech">{stack.technology}</span>
            </div>

            <div className="dx-score-display">
              <div className="score-value">{stack.dx_score}</div>
              <div className="score-max">/100</div>
            </div>

            <div className="dx-progress">
              <div
                className="dx-bar"
                style={{ width: `${stack.dx_score}%` }}
              />
            </div>

            <div className="dx-details">
              <div className="detail-item">
                <span className="label">Developers:</span>
                <span className="value">{stack.developer_count}</span>
              </div>

              <div className="satisfaction-breakdown">
                <div className="breakdown-item">
                  Build Time: {stack.satisfaction_breakdown.build_time}%
                </div>
                <div className="breakdown-item">
                  Deployment: {stack.satisfaction_breakdown.deployment_ease}%
                </div>
                <div className="breakdown-item">
                  Platform: {stack.satisfaction_breakdown.platform_usability}%
                </div>
                <div className="breakdown-item">
                  Tooling: {stack.satisfaction_breakdown.tooling_effectiveness}%
                </div>
              </div>

              {stack.top_pain_points.length > 0 && (
                <div className="pain-points">
                  <strong>Top Pain Points:</strong>
                  <ul>
                    {stack.top_pain_points.map((point, idx) => (
                      <li key={idx}>{point}</li>
                    ))}
                  </ul>
                </div>
              )}
            </div>
          </div>
        ))}
      </div>
    </div>
  );
};
```

**Main App (`src/App.jsx`)**:
```jsx
import React, { useState } from 'react';
import { PipelineMetrics } from './components/PipelineMetrics';
import { DeveloperExperience } from './components/DeveloperExperience';
import { PlatformStackHealth } from './components/PlatformStackHealth';
import { ThroughputChart } from './components/ThroughputChart';
import { CostAnalytics } from './components/CostAnalytics';
import { RevenueImpact } from './components/RevenueImpact';
import './App.css';

function App() {
  const [activeTab, setActiveTab] = useState('overview');
  const [timeRange, setTimeRange] = useState('7d');

  return (
    <div className="app">
      <header className="app-header">
        <h1>Platform Analytics Dashboard</h1>
        <div className="time-range-selector">
          <select value={timeRange} onChange={(e) => setTimeRange(e.target.value)}>
            <option value="1h">Last Hour</option>
            <option value="24h">Last 24 Hours</option>
            <option value="7d">Last 7 Days</option>
            <option value="30d">Last 30 Days</option>
            <option value="90d">Last 90 Days</option>
          </select>
        </div>
      </header>

      <nav className="tab-navigation">
        <button
          className={activeTab === 'overview' ? 'active' : ''}
          onClick={() => setActiveTab('overview')}
        >
          Overview
        </button>
        <button
          className={activeTab === 'pipeline' ? 'active' : ''}
          onClick={() => setActiveTab('pipeline')}
        >
          Pipeline Metrics
        </button>
        <button
          className={activeTab === 'dx' ? 'active' : ''}
          onClick={() => setActiveTab('dx')}
        >
          Developer Experience
        </button>
        <button
          className={activeTab === 'cost' ? 'active' : ''}
          onClick={() => setActiveTab('cost')}
        >
          Cost Analytics
        </button>
        <button
          className={activeTab === 'revenue' ? 'active' : ''}
          onClick={() => setActiveTab('revenue')}
        >
          Revenue Impact
        </button>
      </nav>

      <main className="app-main">
        {activeTab === 'overview' && (
          <>
            <PlatformStackHealth />
            <PipelineMetrics timeRange={timeRange} />
            <ThroughputChart timeRange={timeRange} />
          </>
        )}
        {activeTab === 'pipeline' && <PipelineMetrics timeRange={timeRange} />}
        {activeTab === 'dx' && <DeveloperExperience />}
        {activeTab === 'cost' && <CostAnalytics timeRange={timeRange} />}
        {activeTab === 'revenue' && <RevenueImpact timeRange={timeRange} />}
      </main>
    </div>
  );
}

export default App;
```

**Vite Configuration (`vite.config.js`)**:
```javascript
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';

export default defineConfig({
  plugins: [react()],
  server: {
    port: 5173,
    proxy: {
      '/api': {
        target: 'http://localhost:5000',
        changeOrigin: true,
      },
    },
  },
});
```

**Package Configuration (`package.json`)**:
```json
{
  "name": "platform-analytics-dashboard",
  "version": "1.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview"
  },
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "axios": "^1.6.2",
    "recharts": "^2.10.3",
    "react-query": "^3.39.3"
  },
  "devDependencies": {
    "@vitejs/plugin-react": "^4.2.1",
    "vite": "^5.0.8"
  }
}
```

---

## Integration with Other Frameworks

### Next.js Integration

**API Route (`pages/api/analytics/[...path].js`)**:
```javascript
export default async function handler(req, res) {
  const { path } = req.query;
  const apiPath = path.join('/');

  const response = await fetch(
    `${process.env.ANALYTICS_API_URL}/api/v1/analytics/${apiPath}?${new URLSearchParams(req.query)}`,
    {
      headers: {
        'X-API-Key': process.env.ANALYTICS_API_KEY,
      },
    }
  );

  const data = await response.json();
  res.status(response.status).json(data);
}
```

**Server Component (`app/dashboard/page.jsx`)**:
```jsx
async function getPipelineMetrics() {
  const res = await fetch('http://localhost:3000/api/analytics/pipeline-metrics', {
    cache: 'no-store'
  });
  return res.json();
}

export default async function DashboardPage() {
  const metrics = await getPipelineMetrics();

  return (
    <div>
      <h1>Platform Analytics</h1>
      <PipelineMetricsDisplay data={metrics} />
    </div>
  );
}
```

### Vue.js Integration

**Composable (`composables/useAnalytics.js`)**:
```javascript
import { ref, onMounted, onUnmounted } from 'vue';
import axios from 'axios';

export function useAnalytics(metricType, params = {}, refreshInterval = null) {
  const data = ref(null);
  const loading = ref(true);
  const error = ref(null);

  const fetchData = async () => {
    try {
      loading.value = true;
      const response = await axios.get(
        `${import.meta.env.VITE_API_BASE_URL}/analytics/${metricType}`,
        {
          params,
          headers: {
            'X-API-Key': import.meta.env.VITE_API_KEY,
          },
        }
      );
      data.value = response.data;
      error.value = null;
    } catch (err) {
      error.value = err.message;
    } finally {
      loading.value = false;
    }
  };

  let interval = null;

  onMounted(() => {
    fetchData();
    if (refreshInterval) {
      interval = setInterval(fetchData, refreshInterval);
    }
  });

  onUnmounted(() => {
    if (interval) clearInterval(interval);
  });

  return { data, loading, error, refetch: fetchData };
}
```

**Component (`components/PipelineMetrics.vue`)**:
```vue
<template>
  <div class="pipeline-metrics">
    <h2>Pipeline Metrics</h2>
    <div v-if="loading">Loading...</div>
    <div v-else-if="error">Error: {{ error }}</div>
    <div v-else class="metrics-grid">
      <div class="metric-card">
        <h3>Pipeline Availability</h3>
        <div class="metric-value">{{ data.pipeline_availability.current }}%</div>
      </div>
      <!-- More metrics... -->
    </div>
  </div>
</template>

<script setup>
import { useAnalytics } from '../composables/useAnalytics';

const props = defineProps({
  timeRange: { type: String, default: '7d' }
});

const { data, loading, error } = useAnalytics(
  'pipeline-metrics',
  { time_range: props.timeRange },
  60000
);
</script>
```

### Angular Integration

**Service (`analytics.service.ts`)**:
```typescript
import { Injectable } from '@angular/core';
import { HttpClient, HttpHeaders } from '@angular/common/http';
import { Observable } from 'rxjs';
import { environment } from '../environments/environment';

@Injectable({
  providedIn: 'root'
})
export class AnalyticsService {
  private apiUrl = environment.analyticsApiUrl;
  private apiKey = environment.analyticsApiKey;

  constructor(private http: HttpClient) {}

  private getHeaders(): HttpHeaders {
    return new HttpHeaders({
      'Content-Type': 'application/json',
      'X-API-Key': this.apiKey
    });
  }

  getPipelineMetrics(params: any = {}): Observable<any> {
    return this.http.get(`${this.apiUrl}/analytics/pipeline-metrics`, {
      params,
      headers: this.getHeaders()
    });
  }

  getDeveloperExperience(params: any = {}): Observable<any> {
    return this.http.get(`${this.apiUrl}/analytics/developer-experience`, {
      params,
      headers: this.getHeaders()
    });
  }

  // More methods...
}
```

**Component (`pipeline-metrics.component.ts`)**:
```typescript
import { Component, OnInit, Input } from '@angular/core';
import { AnalyticsService } from '../services/analytics.service';

@Component({
  selector: 'app-pipeline-metrics',
  templateUrl: './pipeline-metrics.component.html',
  styleUrls: ['./pipeline-metrics.component.css']
})
export class PipelineMetricsComponent implements OnInit {
  @Input() timeRange: string = '7d';

  data: any = null;
  loading: boolean = true;
  error: string | null = null;

  constructor(private analyticsService: AnalyticsService) {}

  ngOnInit(): void {
    this.fetchMetrics();
    setInterval(() => this.fetchMetrics(), 60000); // Refresh every 60s
  }

  fetchMetrics(): void {
    this.loading = true;
    this.analyticsService.getPipelineMetrics({ time_range: this.timeRange })
      .subscribe({
        next: (data) => {
          this.data = data;
          this.loading = false;
        },
        error: (err) => {
          this.error = err.message;
          this.loading = false;
        }
      });
  }
}
```

### Svelte Integration

**Store (`stores/analytics.js`)**:
```javascript
import { writable } from 'svelte/store';
import axios from 'axios';

export function createAnalyticsStore() {
  const { subscribe, set, update } = writable({
    data: null,
    loading: false,
    error: null
  });

  return {
    subscribe,
    fetchMetrics: async (metricType, params = {}) => {
      update(state => ({ ...state, loading: true }));

      try {
        const response = await axios.get(
          `${import.meta.env.VITE_API_BASE_URL}/analytics/${metricType}`,
          {
            params,
            headers: {
              'X-API-Key': import.meta.env.VITE_API_KEY
            }
          }
        );

        set({ data: response.data, loading: false, error: null });
      } catch (err) {
        set({ data: null, loading: false, error: err.message });
      }
    }
  };
}

export const pipelineMetrics = createAnalyticsStore();
```

**Component (`PipelineMetrics.svelte`)**:
```svelte
<script>
  import { onMount } from 'svelte';
  import { pipelineMetrics } from '../stores/analytics';

  export let timeRange = '7d';

  onMount(() => {
    pipelineMetrics.fetchMetrics('pipeline-metrics', { time_range: timeRange });

    const interval = setInterval(() => {
      pipelineMetrics.fetchMetrics('pipeline-metrics', { time_range: timeRange });
    }, 60000);

    return () => clearInterval(interval);
  });
</script>

{#if $pipelineMetrics.loading}
  <div class="loading">Loading...</div>
{:else if $pipelineMetrics.error}
  <div class="error">Error: {$pipelineMetrics.error}</div>
{:else if $pipelineMetrics.data}
  <div class="pipeline-metrics">
    <h2>Pipeline Metrics</h2>
    <div class="metrics-grid">
      <div class="metric-card">
        <h3>Pipeline Availability</h3>
        <div class="metric-value">
          {$pipelineMetrics.data.pipeline_availability.current}%
        </div>
      </div>
      <!-- More metrics... -->
    </div>
  </div>
{/if}
```

---

## Deployment Configurations

### Docker Compose (Flask + React)

**`docker-compose.yml`**:
```yaml
version: '3.8'

services:
  # Flask API Backend
  api:
    build: ./platform-analytics-api
    ports:
      - "5000:5000"
    environment:
      - FLASK_ENV=production
      - DATABASE_URL=postgresql://user:password@db:5432/platform_analytics
      - REDIS_URL=redis://redis:6379/0
      - VALID_API_KEYS=${API_KEYS}
    depends_on:
      - db
      - redis
    restart: unless-stopped

  # React/Vite Frontend
  frontend:
    build: ./platform-analytics-dashboard
    ports:
      - "3000:3000"
    environment:
      - VITE_API_BASE_URL=http://api:5000/api/v1
      - VITE_API_KEY=${API_KEY}
    depends_on:
      - api
    restart: unless-stopped

  # PostgreSQL Database
  db:
    image: timescale/timescaledb:latest-pg15
    ports:
      - "5432:5432"
    environment:
      - POSTGRES_USER=user
      - POSTGRES_PASSWORD=password
      - POSTGRES_DB=platform_analytics
    volumes:
      - postgres_data:/var/lib/postgresql/data
    restart: unless-stopped

  # Redis Cache
  redis:
    image: redis:7-alpine
    ports:
      - "6379:6379"
    restart: unless-stopped

volumes:
  postgres_data:
```

---

**Skill Owner**: Platform Program Management Repository
**Last Updated**: January 2026
**Version**: 1.1
