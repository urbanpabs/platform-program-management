# Skill: Prototype Generator

## Description
Generate 3 divergent functional prototypes from product requirements using OpenSpec/spec-kit standards. Creates working code (not mockups) at appropriate fidelity levels, with built-in user validation frameworks and customer journey mapping.

## Usage
```bash
/prototype-generator --requirement "self-service database provisioning" --fidelity functional
/prototype-generator --requirement "developer portal navigation" --fidelity clickable --variants 3
/prototype-generator --requirement "CI/CD workflow configuration" --include-validation true
```

## Parameters

### Required
- `--requirement` (string): Product feature or capability to prototype (e.g., "self-service provisioning", "developer portal", "deployment workflow")

### Optional
- `--fidelity` (string): Prototype fidelity level: "wireframe", "clickable", "functional" (default: "clickable")
- `--variants` (number): Number of divergent prototypes to generate: 2-5 (default: 3)
- `--tech-stack` (string): Technology stack: "react", "vue", "angular", "svelte", "cli" (default: "react")
- `--include-validation` (boolean): Generate user testing framework (default: true)
- `--include-openspec` (boolean): Generate OpenSpec proposals for each variant (default: true)
- `--timeline` (string): Development timeline: "fast" (1-2 days), "standard" (3-5 days), "comprehensive" (1-2 weeks) (default: "standard")

## Output Structure

```
prototypes/
├── [requirement-name]/
│   ├── variant-a/
│   │   ├── src/                    # Functional prototype code
│   │   ├── README.md               # Setup and run instructions
│   │   ├── openspec-proposal.md    # OpenSpec specification
│   │   └── journey-map.md          # Customer journey for this variant
│   ├── variant-b/
│   │   ├── src/
│   │   ├── README.md
│   │   ├── openspec-proposal.md
│   │   └── journey-map.md
│   ├── variant-c/
│   │   ├── src/
│   │   ├── README.md
│   │   ├── openspec-proposal.md
│   │   └── journey-map.md
│   ├── validation/
│   │   ├── test-script.md          # User testing script
│   │   ├── feedback-rubric.md      # Comparison rubric
│   │   ├── journey-template.md     # Journey mapping template
│   │   └── success-metrics.md      # Validation criteria
│   └── comparison-matrix.md        # Side-by-side comparison
```

## Prototype Fidelity Levels

### Wireframe Prototypes (fidelity: wireframe)

**Output**: Interactive wireframes and flows
**Technology**: Figma/Sketch exports + HTML/CSS
**Timeline**: 1-2 days per variant
**Use Case**: Early concept validation, information architecture testing

**Generated Assets**:
- HTML wireframes with clickable navigation
- Flow diagrams showing user paths
- Basic interaction states
- Lorem ipsum content

**Example Output**:
```html
<!-- variant-a/src/index.html -->
<!DOCTYPE html>
<html>
<head>
  <title>Prototype A: CLI-First Provisioning</title>
  <style>
    .wireframe { border: 2px dashed #ccc; padding: 20px; }
    .terminal { background: #1e1e1e; color: #00ff00; font-family: monospace; }
  </style>
</head>
<body>
  <div class="wireframe">
    <h1>Self-Service Database Provisioning</h1>
    <div class="terminal">
      <p>$ platform db create --type postgres</p>
      <p>✓ Database created: postgres-dev-1a2b3c</p>
      <p>Connection string: postgresql://...</p>
    </div>
    <button onclick="location.href='success.html'">Next Step</button>
  </div>
</body>
</html>
```

---

### Clickable Prototypes (fidelity: clickable)

**Output**: Functional frontend with sample data
**Technology**: React/Vue/Svelte with static data
**Timeline**: 3-5 days per variant
**Use Case**: UX validation, journey mapping, visual design testing

**Generated Assets**:
- Full React/Vue/Svelte application
- Component library matching design system
- Sample data fixtures
- Working interactions and state management
- Basic styling and responsive design

**Example Output**:
```jsx
// variant-a/src/components/DatabaseProvisioner.jsx
import React, { useState } from 'react';
import { Terminal } from './Terminal';

export const DatabaseProvisioner = () => {
  const [command, setCommand] = useState('');
  const [output, setOutput] = useState([]);

  const handleCommand = (cmd) => {
    // Simulate CLI interaction
    if (cmd.startsWith('platform db create')) {
      setOutput([
        ...output,
        `$ ${cmd}`,
        '⏳ Creating PostgreSQL database...',
        '✓ Database created: postgres-dev-1a2b3c',
        'Connection: postgresql://user:pass@host:5432/db',
        '✓ Credentials saved to ~/.platform/credentials'
      ]);
    }
  };

  return (
    <div className="provisioner">
      <h1>CLI-First Provisioning</h1>
      <Terminal
        output={output}
        onCommand={handleCommand}
        placeholder="platform db create --type postgres"
      />
      <div className="help-panel">
        <h3>Common Commands</h3>
        <code>platform db create --type [postgres|mysql|mongodb]</code>
        <code>platform db list</code>
        <code>platform db info [name]</code>
      </div>
    </div>
  );
};
```

---

### Functional Prototypes (fidelity: functional)

**Output**: Full-stack implementation with real APIs
**Technology**: React/Vue + Flask/Express backend
**Timeline**: 1-2 weeks per variant
**Use Case**: Complete validation including technical feasibility

**Generated Assets**:
- Full frontend application
- Backend API implementation
- Database schema and migrations
- Authentication and authorization
- Real data integration
- Production-ready code quality

**Example Output**:

**Frontend (variant-a/src/components/DatabaseProvisioner.jsx)**:
```jsx
import React, { useState } from 'react';
import { useProvisionDatabase } from '../hooks/useProvisionDatabase';

export const DatabaseProvisioner = () => {
  const [config, setConfig] = useState({
    type: 'postgres',
    size: 'medium',
    environment: 'dev'
  });

  const { provision, loading, error, result } = useProvisionDatabase();

  const handleProvision = async () => {
    const database = await provision(config);
    console.log('Database created:', database);
  };

  return (
    <div className="provisioner">
      <h1>CLI-First Provisioning</h1>

      <div className="config-form">
        <label>
          Database Type:
          <select
            value={config.type}
            onChange={(e) => setConfig({ ...config, type: e.target.value })}
          >
            <option value="postgres">PostgreSQL</option>
            <option value="mysql">MySQL</option>
            <option value="mongodb">MongoDB</option>
          </select>
        </label>

        <label>
          Size:
          <select
            value={config.size}
            onChange={(e) => setConfig({ ...config, size: e.target.value })}
          >
            <option value="small">Small (2GB RAM, $50/mo)</option>
            <option value="medium">Medium (4GB RAM, $100/mo)</option>
            <option value="large">Large (8GB RAM, $200/mo)</option>
          </select>
        </label>

        <label>
          Environment:
          <select
            value={config.environment}
            onChange={(e) => setConfig({ ...config, environment: e.target.value })}
          >
            <option value="dev">Development</option>
            <option value="staging">Staging</option>
            <option value="prod">Production</option>
          </select>
        </label>

        <button onClick={handleProvision} disabled={loading}>
          {loading ? 'Provisioning...' : 'Provision Database'}
        </button>
      </div>

      {error && <div className="error">{error}</div>}

      {result && (
        <div className="result">
          <h3>Database Created Successfully</h3>
          <code>
            Name: {result.name}<br/>
            Type: {result.type}<br/>
            Connection: {result.connection_string}<br/>
            Cost: ${result.monthly_cost}/month
          </code>
        </div>
      )}
    </div>
  );
};
```

**Backend (variant-a/api/routes/database.py)**:
```python
from flask import Blueprint, request, jsonify
from app.services.database_provisioner import DatabaseProvisioner
from app.utils.auth import require_api_key
from app.models import Database

database_bp = Blueprint('database', __name__)

@database_bp.route('/databases', methods=['POST'])
@require_api_key
def provision_database():
    """
    Provision a new database instance

    Request Body:
        type: string (postgres, mysql, mongodb)
        size: string (small, medium, large)
        environment: string (dev, staging, prod)
    """
    data = request.get_json()

    provisioner = DatabaseProvisioner()

    try:
        database = provisioner.provision(
            db_type=data.get('type'),
            size=data.get('size'),
            environment=data.get('environment'),
            created_by=request.user_id
        )

        return jsonify({
            'id': database.id,
            'name': database.name,
            'type': database.type,
            'size': database.size,
            'connection_string': database.get_connection_string(),
            'monthly_cost': database.monthly_cost,
            'status': 'provisioning'
        }), 201

    except Exception as e:
        return jsonify({'error': str(e)}), 400


@database_bp.route('/databases', methods=['GET'])
@require_api_key
def list_databases():
    """List all databases for the authenticated user"""
    databases = Database.query.filter_by(created_by=request.user_id).all()

    return jsonify([{
        'id': db.id,
        'name': db.name,
        'type': db.type,
        'environment': db.environment,
        'status': db.status,
        'created_at': db.created_at.isoformat()
    } for db in databases]), 200


@database_bp.route('/databases/<db_id>', methods=['GET'])
@require_api_key
def get_database(db_id):
    """Get database details and connection info"""
    database = Database.query.get_or_404(db_id)

    # Check ownership
    if database.created_by != request.user_id:
        return jsonify({'error': 'Unauthorized'}), 403

    return jsonify({
        'id': database.id,
        'name': database.name,
        'type': database.type,
        'size': database.size,
        'environment': database.environment,
        'connection_string': database.get_connection_string(),
        'monthly_cost': database.monthly_cost,
        'status': database.status,
        'health': database.get_health_metrics()
    }), 200
```

---

## Prototype Variant Strategies

The skill generates 3 divergent approaches for each requirement:

### Strategy 1: Optimize for Different User Personas

**Example: Self-Service Provisioning**
- **Variant A**: CLI-first (expert developers, automation-focused)
- **Variant B**: GUI portal (occasional users, discoverability-focused)
- **Variant C**: GitOps (teams, audit-trail-focused)

---

### Strategy 2: Optimize for Different Workflows

**Example: Developer Portal Navigation**
- **Variant A**: Search-first (knows what they want)
- **Variant B**: Catalog-first (browsing and discovering)
- **Variant C**: Workflow-first (guided task completion)

---

### Strategy 3: Optimize for Different Technical Approaches

**Example: CI/CD Configuration**
- **Variant A**: YAML-based (infrastructure-as-code)
- **Variant B**: Visual pipeline builder (drag-and-drop)
- **Variant C**: Template-based wizard (opinionated defaults)

---

## Validation Framework Generation

### User Testing Script

For each prototype set, generate comprehensive testing script:

```markdown
# User Testing Script: Self-Service Database Provisioning

## Test Overview
- **Duration**: 30 minutes per participant
- **Participants**: 15 developers (5 junior, 5 mid, 5 senior)
- **Prototypes**: 3 variants (CLI-first, Portal-GUI, GitOps)

## Pre-Test Questionnaire
1. How often do you provision databases? (Daily/Weekly/Monthly/Rarely)
2. What tools do you currently use?
3. What's most frustrating about current process?

## Test Scenarios

### Scenario 1: First-Time Database Provision
**Context**: You need a PostgreSQL database for a new microservice you're building.

**Task**: Provision a medium-sized PostgreSQL database in the development environment.

**Observations**:
- [ ] Started without documentation
- [ ] Time to completion: _____
- [ ] Number of errors: _____
- [ ] Asked for help: Yes / No
- [ ] Completed successfully: Yes / No

**Friction Points**:
_________________________________

**Delight Moments**:
_________________________________

**Verbatim Quotes**:
_________________________________

### Scenario 2: Find Existing Database Connection
**Context**: You provisioned a database last week but lost the connection string.

**Task**: Find and retrieve the connection string for your existing database.

**Observations**:
- [ ] Time to completion: _____
- [ ] Navigation path: _____
- [ ] Successful: Yes / No

### Scenario 3: Production Database with Compliance
**Context**: You need a production PostgreSQL database that meets SOC 2 requirements (encryption, backups, audit logs).

**Task**: Provision a production database with required compliance controls.

**Observations**:
- [ ] Found compliance options: Yes / No
- [ ] Understood requirements: Yes / No
- [ ] Time to completion: _____
- [ ] Confidence in compliance: 1-10: _____

## Post-Test Questions

### Satisfaction
1. Rate ease of use (1-10): _____
2. Rate confidence in result (1-10): _____
3. Likelihood to recommend (NPS): _____

### Comparison
4. Which prototype did you prefer? Why?
   _________________________________

5. What did you like most about each?
   - Variant A (CLI): _________________
   - Variant B (GUI): _________________
   - Variant C (GitOps): _________________

6. What was most frustrating about each?
   - Variant A (CLI): _________________
   - Variant B (GUI): _________________
   - Variant C (GitOps): _________________

### Open Feedback
7. What would you change?
   _________________________________

8. What's missing?
   _________________________________

9. Any other feedback?
   _________________________________

## Metrics Summary

| Metric                 | Variant A | Variant B | Variant C |
|------------------------|-----------|-----------|-----------|
| Avg time to completion |           |           |           |
| Success rate           |           |           |           |
| Error rate             |           |           |           |
| NPS                    |           |           |           |
| Preference count       |           |           |           |
```

---

### Feedback Rubric

```markdown
# Prototype Comparison Rubric: Self-Service Database Provisioning

## Evaluation Criteria

### 1. Usability (40% weight)

#### Time to Task Completion (15%)
| Prototype | Avg Time | Score (1-10) | Notes |
|-----------|----------|--------------|-------|
| Variant A |          |              |       |
| Variant B |          |              |       |
| Variant C |          |              |       |

Scoring:
- 10 points: <1 minute
- 7 points: 1-3 minutes
- 4 points: 3-5 minutes
- 1 point: >5 minutes

#### Error Rate (10%)
| Prototype | Errors/User | Score (1-10) | Common Errors |
|-----------|-------------|--------------|---------------|
| Variant A |             |              |               |
| Variant B |             |              |               |
| Variant C |             |              |               |

#### Learnability (10%)
| Prototype | First-Use Success % | Score (1-10) | Learning Curve |
|-----------|---------------------|--------------|----------------|
| Variant A |                     |              |                |
| Variant B |                     |              |                |
| Variant C |                     |              |                |

#### User Satisfaction (5%)
| Prototype | NPS Score | Score (1-10) |
|-----------|-----------|--------------|
| Variant A |           |              |
| Variant B |           |              |
| Variant C |           |              |

---

### 2. Strategic Fit (30% weight)

#### Alignment to Platform Goals (10%)
| Prototype | Self-Service | Developer Velocity | Governance | Score (1-10) |
|-----------|--------------|-------------------|------------|--------------|
| Variant A |              |                   |            |              |
| Variant B |              |                   |            |              |
| Variant C |              |                   |            |              |

#### Developer Adoption Risk (10%)
| Prototype | Learning Curve | Change Impact | Score (1-10) |
|-----------|----------------|---------------|--------------|
| Variant A |                |               |              |
| Variant B |                |               |              |
| Variant C |                |               |              |

#### Technical Scalability (10%)
| Prototype | Multi-Cloud | Auto-Scale | Extensibility | Score (1-10) |
|-----------|-------------|------------|---------------|--------------|
| Variant A |             |            |               |              |
| Variant B |             |            |               |              |
| Variant C |             |            |               |              |

---

### 3. Implementation (30% weight)

#### Development Cost (10%)
| Prototype | Est. Dev Days | Team Size | Score (1-10) |
|-----------|---------------|-----------|--------------|
| Variant A |               |           |              |
| Variant B |               |           |              |
| Variant C |               |           |              |

#### Maintenance Burden (10%)
| Prototype | Complexity | Dependencies | Score (1-10) |
|-----------|------------|--------------|--------------|
| Variant A |            |              |              |
| Variant B |            |              |              |
| Variant C |            |              |              |

#### Time to Production (10%)
| Prototype | Weeks to Beta | Weeks to GA | Score (1-10) |
|-----------|---------------|-------------|--------------|
| Variant A |               |             |              |
| Variant B |               |             |              |
| Variant C |               |             |              |

---

## Weighted Scores

| Prototype | Usability (40%) | Strategic (30%) | Implementation (30%) | Total Score |
|-----------|-----------------|-----------------|----------------------|-------------|
| Variant A |                 |                 |                      |             |
| Variant B |                 |                 |                      |             |
| Variant C |                 |                 |                      |             |

---

## Recommendation

**Winning Prototype**: ___________

**Rationale**:
_________________________________

**Key Strengths**:
- _________________________________
- _________________________________
- _________________________________

**Known Weaknesses**:
- _________________________________
- _________________________________

**Mitigation Plan**:
_________________________________

**Next Steps**:
1. _________________________________
2. _________________________________
3. _________________________________
```

---

## OpenSpec Proposal Generation

For each prototype variant, generate OpenSpec specification:

```markdown
# Proposal: Self-Service Database Provisioning (CLI-First Variant)

**Status**: Prototype
**Created**: 2026-01-03
**Variant**: A (CLI-First)
**Competing Variants**: B (Portal GUI), C (GitOps)

## Summary
CLI-first self-service database provisioning enabling developers to create, manage,
and connect to databases from the terminal without tickets or approvals.

## Motivation

### Problem
Developers currently wait 3-5 days for database provisioning through ticket systems.
This blocks development velocity and creates frustration.

### Solution
Self-service CLI enabling sub-5-minute provisioning with built-in governance, cost
controls, and compliance guardrails.

### Why CLI-First?
- 67% of platform developers provision infrastructure from terminal (survey data)
- CLI enables scriptable, automatable workflows
- Minimal context switching for developers already in terminal
- Natural fit for CI/CD pipeline integration

## User Journey

### Persona: Mid-level Backend Developer
**Context**: Building new microservice, needs PostgreSQL database

**Current State** (3-5 days):
1. Find database request form (15 minutes searching Confluence)
2. Fill out form with requirements (20 minutes)
3. Submit ticket and wait for approval (1-2 days)
4. DBA provisions database (1 day)
5. Receive connection string via email (0-2 days delay)
6. Manually add credentials to application config

**Proposed State** (<5 minutes):
1. Run: `platform db create --type postgres --size medium --env dev`
2. CLI validates inputs, shows cost estimate ($100/month)
3. Confirm provisioning
4. Database provisioned in ~2 minutes
5. Connection string automatically saved to `~/.platform/credentials`
6. Credentials ready for application use

**Time Saved**: 99% reduction (3-5 days → 5 minutes)

---

## Design

### CLI Commands

#### Create Database
```bash
platform db create [options]

Options:
  --type <type>         Database type: postgres, mysql, mongodb (required)
  --size <size>         Instance size: small, medium, large (default: medium)
  --env <environment>   Environment: dev, staging, prod (default: dev)
  --name <name>         Database name (auto-generated if omitted)
  --config <file>       YAML config file path
  --replicas <count>    Number of replicas (default: 0)
  --backup-retention    Backup retention days (default: 7)
  --tags <tags>         Comma-separated tags

Examples:
  platform db create --type postgres
  platform db create --type mysql --size large --env prod --replicas 2
  platform db create --config ./database.yaml
```

#### List Databases
```bash
platform db list [options]

Options:
  --env <environment>   Filter by environment
  --type <type>         Filter by database type
  --format <format>     Output format: table, json, yaml (default: table)

Examples:
  platform db list
  platform db list --env prod --format json
```

#### Get Database Info
```bash
platform db info <name> [options]

Options:
  --show-credentials    Display connection credentials
  --format <format>     Output format: table, json, yaml

Examples:
  platform db info postgres-dev-1a2b3c
  platform db info postgres-dev-1a2b3c --show-credentials
```

#### Delete Database
```bash
platform db delete <name> [options]

Options:
  --force              Skip confirmation prompt
  --backup             Create final backup before deletion

Examples:
  platform db delete postgres-dev-1a2b3c
  platform db delete postgres-dev-1a2b3c --force --backup
```

---

### Configuration File Format

```yaml
# database.yaml
apiVersion: platform.company.com/v1
kind: Database

metadata:
  name: user-service-db
  environment: production
  tags:
    team: backend
    service: user-service
    cost-center: engineering

spec:
  type: postgres
  version: "15"
  size: large

  storage:
    size: 100Gi
    type: ssd

  replication:
    replicas: 2
    sync: true

  backup:
    enabled: true
    retention: 30
    schedule: "0 2 * * *"

  networking:
    vpc: prod-vpc-us-east-1
    allowedCIDRs:
      - 10.0.0.0/16

  compliance:
    encryption: true
    auditLogging: true
    soc2: true
```

---

### Technical Architecture

#### CLI Implementation
- **Language**: Rust (fast, cross-platform, single binary)
- **Config**: TOML for CLI config (`~/.platform/config.toml`)
- **Credentials**: OS-native keychain (macOS Keychain, Windows Credential Manager, Linux Secret Service)
- **API Communication**: HTTP REST API with JWT authentication

#### Backend API
- **Endpoints**:
  - `POST /api/v1/databases` - Provision database
  - `GET /api/v1/databases` - List databases
  - `GET /api/v1/databases/{id}` - Get database details
  - `DELETE /api/v1/databases/{id}` - Delete database

#### Provisioning Workflow
1. CLI sends provision request to API
2. API validates user permissions and quota
3. API checks cost budget and approvals (auto-approved for dev/staging)
4. API calls cloud provider API (AWS RDS, GCP Cloud SQL, etc.)
5. API polls for provision completion
6. API generates credentials and returns to CLI
7. CLI stores credentials in secure keychain

---

## Validation Plan

### Prototype Specs
- **Fidelity**: Level 3 (Functional)
- **Timeline**: 10 days
- **Scope**: Full CLI + backend API + PostgreSQL provisioning

### Test Plan
- **Participants**: 15 developers (5 junior, 5 mid, 5 senior)
- **Scenarios**:
  1. First-time database provisioning
  2. Retrieve existing database credentials
  3. Production database with compliance requirements
  4. Bulk provisioning via YAML config

### Success Metrics
- Time to first successful provision: <5 minutes (target: 2 minutes)
- Error rate: <10% (target: <5%)
- NPS: >40 (target: >50)
- Adoption intent: >70% (target: >80%)

---

## Alternatives Considered

### This is Variant A (CLI-First)

**Strengths**:
- Fastest for expert developers
- Scriptable and automatable
- Minimal context switching
- CI/CD friendly

**Weaknesses**:
- Learning curve for CLI syntax
- Discoverability challenges for new users
- Requires terminal access

---

### Variant B: Portal GUI

**Approach**: Web-based developer portal with visual forms

**Strengths**:
- Discoverable and self-documenting
- Lower learning curve
- Visual feedback and validation

**Weaknesses**:
- Slower for repeated tasks
- Not automatable
- Requires browser context switch

**See**: proposals/db-provisioning-portal-gui.md

---

### Variant C: GitOps

**Approach**: YAML files in git repository trigger provisioning

**Strengths**:
- Full audit trail in git
- Code review for all changes
- Declarative infrastructure-as-code

**Weaknesses**:
- Slower (requires PR approval)
- Overhead for simple dev databases
- Git workflow requirement

**See**: proposals/db-provisioning-gitops.md

---

## Open Questions

1. **Windows support priority?**
   - Windows Subsystem for Linux (WSL) sufficient?
   - Native Windows CLI needed?

2. **Credential storage**:
   - OS keychain vs encrypted file?
   - Team credential sharing mechanism?

3. **Offline mode**:
   - Config validation without API call?
   - Cached templates for autocomplete?

4. **Multi-cloud support**:
   - AWS RDS, GCP Cloud SQL, Azure Database?
   - Unified abstraction vs cloud-specific flags?

---

## Next Steps

1. **Week 1-2**: Build functional prototype
   - Rust CLI with core commands
   - Flask backend API
   - AWS RDS integration
   - Credential storage

2. **Week 3**: User testing
   - 15 developers across experience levels
   - 4 test scenarios
   - Collect quantitative and qualitative feedback

3. **Week 4**: Analysis and iteration
   - Compare against Variants B and C
   - Synthesize feedback
   - Recommend winning approach or hybrid

---

**Proposal Status**: Awaiting prototype validation
**Next Review**: After user testing completion
```

---

## Integration with Agents

```bash
# Generate prototypes via Product Prototyping Agent
@product-prototyping-agent "Generate 3 prototypes for self-service database provisioning"

# Or invoke skill directly
/prototype-generator --requirement "self-service database provisioning" --fidelity functional

# Generate with custom parameters
/prototype-generator \
  --requirement "developer portal navigation" \
  --fidelity clickable \
  --variants 3 \
  --tech-stack react \
  --include-validation true \
  --include-openspec true
```

---

## Related Skills

- `/value-narrative` - Create compelling narratives for prototype variants
- `/stakeholder-map` - Identify user communities for validation
- `/mindmap-generator` - Visualize customer journeys and decision trees
- `/policy-generator` - Ensure prototypes meet compliance requirements

---

## Related Agents

- `@product-prototyping-agent` - Orchestrates full prototype-to-validation workflow
- `@strategy-agent` - Align prototypes to platform vision
- `@stakeholder-agent` - Coordinate user validation sessions
- `@delivery-agent` - Plan prototype-to-production transition

---

## Best Practices

### 1. Diverge Before Converging
Generate genuinely different approaches. Don't create 3 variations of the same idea.

❌ **Bad**:
- Variant A: Blue button on left
- Variant B: Green button on center
- Variant C: Red button on right

✅ **Good**:
- Variant A: CLI-first automation
- Variant B: Visual portal workflow
- Variant C: GitOps infrastructure-as-code

---

### 2. Match Fidelity to Question
Use the minimum fidelity needed to answer your validation question.

- **Testing information architecture?** → Wireframe sufficient
- **Testing UX and visual design?** → Clickable prototype
- **Testing technical feasibility?** → Functional prototype

Don't over-invest in fidelity before validation.

---

### 3. Real Code, Real Learning
Clickable and functional prototypes should use production-quality code patterns.

Benefits:
- Reveals technical constraints early
- Code can evolve into production implementation
- Engineers see feasibility, not just design
- Integration challenges surface during prototyping

---

### 4. Measure Everything
Instrument prototypes to collect data, not just opinions.

**Quantitative Metrics**:
- Time to task completion
- Error rates and retry attempts
- Navigation paths taken
- Feature discovery rate

**Qualitative Feedback**:
- Satisfaction (NPS)
- Preference ranking
- Verbatim user quotes
- Observed friction points

---

### 5. Test with Real Users
Don't validate with internal team only. Test with actual user community.

**Diverse Test Pool**:
- Junior, mid, senior experience levels
- Different team contexts
- Varied technical backgrounds
- Edge case scenarios

---

## Common Pitfalls

❌ **Confirmation Bias**: Building prototypes that validate pre-existing preferences
✅ **Solution**: Force divergent approaches. Test with users who don't know your preference.

❌ **Sunk Cost Fallacy**: Sticking with a prototype because of investment
✅ **Solution**: Treat all prototypes as disposable. Follow the evidence.

❌ **Analysis Paralysis**: Over-analyzing instead of building and testing
✅ **Solution**: Set time limits. Ship prototypes imperfectly and learn.

❌ **Premature Convergence**: Picking a winner before user validation
✅ **Solution**: Test all variants. Let users decide through usage, not opinions.

---

**Skill Owner**: Platform Program Management Repository
**Last Updated**: January 2026
**Version**: 1.0
