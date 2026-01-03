# Skill: Policy Generator (OPA Rego)

## Description
Generate, analyze, and validate OPA (Open Policy Agent) Rego policies from plain English requirements. Converts business rules and compliance requirements into executable policy-as-code with comprehensive test coverage.

## Usage
```bash
/policy-generator --requirement "Container images must come from approved registries" --type kubernetes --format rego
/policy-generator --analyze deployment.yaml --framework soc2
/policy-generator --validate policy.rego --test-cases test-input.json
```

## Parameters

### Required
- `--requirement` OR `--analyze`: Policy requirement in plain English OR path to config file to analyze
- `--type`: Policy enforcement point
  - `kubernetes`: Kubernetes admission control
  - `terraform`: Terraform/IaC validation
  - `cicd`: CI/CD pipeline gates
  - `api`: API request validation
  - `cloud`: Cloud resource policies (AWS/Azure/GCP)

### Optional
- `--format` (string): Output format: "rego", "plain-english", "both" (default: "both")
- `--framework` (string): Compliance framework: "soc2", "iso27001", "gdpr", "hipaa", "pci-dss", "nist"
- `--severity` (string): Violation severity: "critical", "high", "medium", "low" (default: "high")
- `--test-cases` (boolean): Generate test cases (default: true)
- `--namespace` (string): Rego package namespace (default: "platform.policy")
- `--validate` (string): Path to Rego file to validate
- `--exceptions` (array): List of exceptions/exemptions

---

## Policy Generation Workflow

### Step 1: Requirement Analysis

**Input**: Plain English requirement

**Process**:
1. Parse requirement into components
2. Identify enforcement scope
3. Extract conditions and constraints
4. Determine exception scenarios
5. Map to compliance frameworks (if applicable)

**Output**: Structured policy specification

### Step 2: Plain English Policy

**Format**:
```
POLICY SPECIFICATION
════════════════════
Name: [policy-name]
Version: 1.0
Severity: [critical|high|medium|low]

INTENT
──────
[Clear statement of what this policy enforces and why]

SCOPE
─────
Applies To: [resources/objects affected]
Enforcement Point: [where policy is evaluated]
Namespaces: [which namespaces, or "all"]

RULES
─────
1. ALLOW [condition]
2. DENY [condition]
3. REQUIRE [condition]
4. EXEMPT [condition]

VIOLATIONS
──────────
When Violated:
- Action: [deny|warn|log]
- Notification: [who gets notified]
- Remediation: [how to fix]

COMPLIANCE MAPPING
──────────────────
SOC 2: CC6.1 (Logical Access Controls)
ISO 27001: A.9.4.1 (Access Control)
```

### Step 3: OPA Rego Generation

**Template Structure**:
```rego
package platform.policy.[category]

import future.keywords.contains
import future.keywords.if
import future.keywords.in

# Metadata
metadata := {
    "name": "[policy-name]",
    "description": "[policy description]",
    "severity": "[severity]",
    "version": "1.0",
    "compliance": {
        "soc2": ["CC6.1"],
        "iso27001": ["A.9.4.1"]
    }
}

# Main policy decision
deny[msg] {
    [condition]
    msg := sprintf("[violation message]: %v", [[details]])
}

# Helper functions
[helper_functions]

# Test cases
test_[policy_name]_[scenario] if {
    [test logic]
}
```

---

## Pre-Built Policy Templates

### 1. Container Image Registry Policy

**Requirement**: "Only allow container images from approved registries"

**Plain English**:
```
POLICY: Approved Container Registries
═════════════════════════════════════
INTENT: Ensure all container images originate from trusted, approved
        registries to prevent supply chain attacks

SCOPE:
- Resources: Pods, Deployments, StatefulSets, DaemonSets, Jobs
- Enforcement: Kubernetes Admission Controller
- Namespaces: All except kube-system

RULES:
1. ALLOW images from: *.dkr.ecr.us-east-1.amazonaws.com/*
2. ALLOW images from: *.dkr.ecr.us-west-2.amazonaws.com/*
3. ALLOW images from: gcr.io/company-name/*
4. DENY all other registries
5. EXEMPT namespace: kube-system (system components)

VIOLATIONS:
- Action: DENY (block resource creation)
- Notification: Slack #security-alerts
- Remediation: Push image to approved registry and update manifest
```

**OPA Rego**:
```rego
package platform.policy.security

import future.keywords.contains
import future.keywords.if
import future.keywords.in

# Metadata
metadata := {
    "name": "approved-container-registries",
    "description": "Restrict container images to approved registries",
    "severity": "high",
    "version": "1.0.0",
    "compliance": {
        "soc2": ["CC6.1", "CC7.2"],
        "iso27001": ["A.12.5.1"]
    }
}

# Approved registries
approved_registries := {
    "123456789.dkr.ecr.us-east-1.amazonaws.com",
    "123456789.dkr.ecr.us-west-2.amazonaws.com",
    "gcr.io/company-name"
}

# Exempt namespaces
exempt_namespaces := {"kube-system", "kube-public"}

# Deny images from unapproved registries
deny[msg] {
    input.request.kind.kind == "Pod"
    not exempt_namespaces[input.request.namespace]

    container := input.request.object.spec.containers[_]
    image := container.image
    not image_from_approved_registry(image)

    msg := sprintf(
        "Container image '%v' is not from an approved registry. Allowed: %v",
        [image, approved_registries]
    )
}

deny[msg] {
    input.request.kind.kind in ["Deployment", "StatefulSet", "DaemonSet"]
    not exempt_namespaces[input.request.namespace]

    container := input.request.object.spec.template.spec.containers[_]
    image := container.image
    not image_from_approved_registry(image)

    msg := sprintf(
        "Container image '%v' is not from an approved registry. Allowed: %v",
        [image, approved_registries]
    )
}

# Helper: Check if image is from approved registry
image_from_approved_registry(image) {
    registry := approved_registries[_]
    startswith(image, registry)
}

# Helper: Extract registry from image
get_registry(image) = registry {
    parts := split(image, "/")
    count(parts) > 1
    registry := parts[0]
}

# Test cases
test_approved_ecr_image_allowed if {
    input := {
        "request": {
            "kind": {"kind": "Pod"},
            "namespace": "production",
            "object": {
                "spec": {
                    "containers": [{
                        "image": "123456789.dkr.ecr.us-east-1.amazonaws.com/app:v1.0"
                    }]
                }
            }
        }
    }
    count(deny) == 0 with input as input
}

test_unapproved_dockerhub_image_denied if {
    input := {
        "request": {
            "kind": {"kind": "Pod"},
            "namespace": "production",
            "object": {
                "spec": {
                    "containers": [{
                        "image": "docker.io/nginx:latest"
                    }]
                }
            }
        }
    }
    count(deny) == 1 with input as input
}

test_system_namespace_exempt if {
    input := {
        "request": {
            "kind": {"kind": "Pod"},
            "namespace": "kube-system",
            "object": {
                "spec": {
                    "containers": [{
                        "image": "k8s.gcr.io/coredns:v1.8.0"
                    }]
                }
            }
        }
    }
    count(deny) == 0 with input as input
}
```

---

### 2. Resource Limits Required Policy

**Requirement**: "All containers must define CPU and memory limits"

**Plain English**:
```
POLICY: Resource Limits Required
═════════════════════════════════
INTENT: Prevent resource exhaustion and ensure fair resource allocation
        across all workloads

SCOPE:
- Resources: Pods, Deployments, StatefulSets, DaemonSets
- Enforcement: Kubernetes Admission Controller
- Namespaces: All production namespaces

RULES:
1. REQUIRE: All containers must define resources.limits.cpu
2. REQUIRE: All containers must define resources.limits.memory
3. REQUIRE: All containers must define resources.requests.cpu
4. REQUIRE: All containers must define resources.requests.memory
5. ENFORCE: requests <= limits (cannot request more than limit)

VIOLATIONS:
- Action: DENY (block resource creation)
- Notification: Developer via deployment failure message
- Remediation: Add resource specifications to container spec
```

**OPA Rego**:
```rego
package platform.policy.resources

import future.keywords.contains
import future.keywords.if
import future.keywords.in

metadata := {
    "name": "resource-limits-required",
    "description": "Require CPU and memory limits on all containers",
    "severity": "high",
    "version": "1.0.0",
    "compliance": {
        "internal": ["RESOURCE-001"]
    }
}

# Get all containers from a resource
containers[container] {
    input.request.kind.kind == "Pod"
    container := input.request.object.spec.containers[_]
}

containers[container] {
    input.request.kind.kind in ["Deployment", "StatefulSet", "DaemonSet", "Job"]
    container := input.request.object.spec.template.spec.containers[_]
}

# Deny if any container missing CPU limit
deny[msg] {
    container := containers[_]
    not container.resources.limits.cpu

    msg := sprintf(
        "Container '%v' must define resources.limits.cpu",
        [container.name]
    )
}

# Deny if any container missing memory limit
deny[msg] {
    container := containers[_]
    not container.resources.limits.memory

    msg := sprintf(
        "Container '%v' must define resources.limits.memory",
        [container.name]
    )
}

# Deny if any container missing CPU request
deny[msg] {
    container := containers[_]
    not container.resources.requests.cpu

    msg := sprintf(
        "Container '%v' must define resources.requests.cpu",
        [container.name]
    )
}

# Deny if any container missing memory request
deny[msg] {
    container := containers[_]
    not container.resources.requests.memory

    msg := sprintf(
        "Container '%v' must define resources.requests.memory",
        [container.name]
    )
}

# Test: Pod with complete resource specs should pass
test_pod_with_resources_allowed if {
    input := {
        "request": {
            "kind": {"kind": "Pod"},
            "object": {
                "spec": {
                    "containers": [{
                        "name": "app",
                        "image": "app:v1",
                        "resources": {
                            "requests": {
                                "cpu": "100m",
                                "memory": "128Mi"
                            },
                            "limits": {
                                "cpu": "500m",
                                "memory": "512Mi"
                            }
                        }
                    }]
                }
            }
        }
    }
    count(deny) == 0 with input as input
}

# Test: Pod without resource limits should be denied
test_pod_without_limits_denied if {
    input := {
        "request": {
            "kind": {"kind": "Pod"},
            "object": {
                "spec": {
                    "containers": [{
                        "name": "app",
                        "image": "app:v1"
                    }]
                }
            }
        }
    }
    count(deny) == 4 with input as input
}
```

---

### 3. No Privileged Containers Policy

**Requirement**: "Containers must not run in privileged mode"

**Plain English**:
```
POLICY: No Privileged Containers
════════════════════════════════
INTENT: Prevent containers from gaining host-level access, reducing
        attack surface and blast radius of compromised containers

SCOPE:
- Resources: Pods, Deployments, StatefulSets, DaemonSets
- Enforcement: Kubernetes Admission Controller
- Namespaces: All except monitoring (daemonsets need host access)

RULES:
1. DENY: containers with securityContext.privileged = true
2. DENY: containers without explicit privileged = false
3. EXEMPT: namespace "monitoring" (for node-level monitoring agents)

VIOLATIONS:
- Action: DENY (block resource creation)
- Notification: Security team + developer
- Remediation: Remove privileged flag or justify exception
```

**OPA Rego**:
```rego
package platform.policy.security

import future.keywords.if

metadata := {
    "name": "no-privileged-containers",
    "description": "Prevent containers from running in privileged mode",
    "severity": "critical",
    "version": "1.0.0",
    "compliance": {
        "soc2": ["CC6.1", "CC6.6"],
        "iso27001": ["A.12.1.3"],
        "cis": ["5.2.1"]
    }
}

exempt_namespaces := {"monitoring", "kube-system"}

# Get all containers
containers[container] {
    input.request.kind.kind == "Pod"
    container := input.request.object.spec.containers[_]
}

containers[container] {
    input.request.kind.kind in ["Deployment", "StatefulSet", "DaemonSet"]
    container := input.request.object.spec.template.spec.containers[_]
}

# Deny privileged containers
deny[msg] {
    not exempt_namespaces[input.request.namespace]
    container := containers[_]
    container.securityContext.privileged == true

    msg := sprintf(
        "Container '%v' is running in privileged mode. This is not allowed for security reasons.",
        [container.name]
    )
}

# Test: Privileged container should be denied
test_privileged_container_denied if {
    input := {
        "request": {
            "kind": {"kind": "Pod"},
            "namespace": "production",
            "object": {
                "spec": {
                    "containers": [{
                        "name": "app",
                        "securityContext": {
                            "privileged": true
                        }
                    }]
                }
            }
        }
    }
    count(deny) == 1 with input as input
}

# Test: Non-privileged container should be allowed
test_non_privileged_container_allowed if {
    input := {
        "request": {
            "kind": {"kind": "Pod"},
            "namespace": "production",
            "object": {
                "spec": {
                    "containers": [{
                        "name": "app",
                        "securityContext": {
                            "privileged": false
                        }
                    }]
                }
            }
        }
    }
    count(deny) == 0 with input as input
}
```

---

### 4. Required Labels Policy

**Requirement**: "All resources must have owner, team, and environment labels"

**OPA Rego**:
```rego
package platform.policy.governance

import future.keywords.if
import future.keywords.in

metadata := {
    "name": "required-labels",
    "description": "Ensure all resources have mandatory labels for tracking",
    "severity": "medium",
    "version": "1.0.0"
}

required_labels := {"owner", "team", "environment", "cost-center"}

deny[msg] {
    input.request.kind.kind in ["Pod", "Deployment", "StatefulSet", "Service"]
    provided_labels := {label | input.request.object.metadata.labels[label]}

    missing := required_labels - provided_labels
    count(missing) > 0

    msg := sprintf(
        "Resource is missing required labels: %v. Required: %v",
        [missing, required_labels]
    )
}

test_all_required_labels_present if {
    input := {
        "request": {
            "kind": {"kind": "Deployment"},
            "object": {
                "metadata": {
                    "labels": {
                        "owner": "john.doe",
                        "team": "platform",
                        "environment": "production",
                        "cost-center": "engineering"
                    }
                }
            }
        }
    }
    count(deny) == 0 with input as input
}
```

---

### 5. TLS Required for Ingress Policy

**OPA Rego**:
```rego
package platform.policy.security

import future.keywords.if

metadata := {
    "name": "ingress-tls-required",
    "description": "All Ingress resources must use TLS encryption",
    "severity": "high",
    "version": "1.0.0",
    "compliance": {
        "soc2": ["CC6.7"],
        "pci": ["4.1"]
    }
}

deny[msg] {
    input.request.kind.kind == "Ingress"
    not input.request.object.spec.tls

    msg := "Ingress must specify TLS configuration. All external traffic must be encrypted."
}

deny[msg] {
    input.request.kind.kind == "Ingress"
    tls := input.request.object.spec.tls[_]
    not tls.secretName

    msg := sprintf(
        "Ingress TLS configuration for host '%v' must specify secretName",
        [tls.hosts[0]]
    )
}

test_ingress_with_tls_allowed if {
    input := {
        "request": {
            "kind": {"kind": "Ingress"},
            "object": {
                "spec": {
                    "tls": [{
                        "hosts": ["app.example.com"],
                        "secretName": "tls-cert"
                    }]
                }
            }
        }
    }
    count(deny) == 0 with input as input
}
```

---

## Policy Validation & Testing

### Test Structure

**Comprehensive Test Suite**:
```rego
# Positive tests (should ALLOW)
test_[policy]_allowed_[scenario] if {
    input := { ... valid input ... }
    count(deny) == 0 with input as input
}

# Negative tests (should DENY)
test_[policy]_denied_[scenario] if {
    input := { ... invalid input ... }
    count(deny) > 0 with input as input
}

# Edge case tests
test_[policy]_edge_case_[scenario] if {
    input := { ... edge case input ... }
    [assertion]
}

# Exception tests
test_[policy]_exception_[scenario] if {
    input := { ... exempt input ... }
    count(deny) == 0 with input as input
}
```

### Running Tests

**Command Line**:
```bash
# Run all tests
opa test policy.rego -v

# Run specific test
opa test policy.rego -v -r test_approved_image_allowed

# Test with coverage
opa test --coverage policy.rego

# Test against sample data
opa eval -i sample-pod.json -d policy.rego "data.platform.policy.security.deny"
```

---

## Policy Bundle Structure

**Directory Layout**:
```
policies/
├── kubernetes/
│   ├── security/
│   │   ├── approved-registries.rego
│   │   ├── no-privileged-containers.rego
│   │   ├── run-as-non-root.rego
│   │   └── tls-required.rego
│   ├── resources/
│   │   ├── resource-limits.rego
│   │   └── pod-disruption-budget.rego
│   └── governance/
│       ├── required-labels.rego
│       └── naming-conventions.rego
├── terraform/
│   ├── aws/
│   │   ├── s3-encryption.rego
│   │   └── iam-mfa-required.rego
│   └── azure/
│       └── network-security.rego
├── cicd/
│   ├── build-policies.rego
│   └── deployment-gates.rego
└── .manifest
```

**Manifest File** (`.manifest`):
```json
{
  "revision": "v1.0.0",
  "roots": ["platform/policy"],
  "metadata": {
    "generated_at": "2026-01-03T10:00:00Z",
    "generator": "policy-generator-skill",
    "compliance_frameworks": ["soc2", "iso27001", "cis"]
  }
}
```

---

## Integration with CI/CD

### GitHub Actions Workflow

```yaml
name: Policy Validation

on:
  pull_request:
    paths:
      - 'k8s/**/*.yaml'
      - 'policies/**/*.rego'

jobs:
  validate-policies:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: Install OPA
        run: |
          curl -L -o opa https://openpolicyagent.org/downloads/latest/opa_linux_amd64
          chmod +x opa
          sudo mv opa /usr/local/bin/

      - name: Test Rego Policies
        run: |
          opa test policies/ -v --coverage

      - name: Validate Kubernetes Manifests
        run: |
          for file in k8s/**/*.yaml; do
            echo "Validating $file"
            opa eval -i "$file" -d policies/ \
              "data.platform.policy.deny" \
              --format pretty
          done
```

---

## Flask Backend Integration

### Policy API Endpoint

**Route** (`app/routes/policy.py`):
```python
from flask import Blueprint, request, jsonify
from app.services.policy_generator import PolicyGenerator
from app.utils.auth import require_api_key

policy_bp = Blueprint('policy', __name__)

@policy_bp.route('/policy/generate', methods=['POST'])
@require_api_key
def generate_policy():
    """
    Generate OPA Rego policy from requirement

    Request Body:
        {
            "requirement": "Only allow images from approved registries",
            "type": "kubernetes",
            "format": "rego",
            "test_cases": true
        }
    """
    data = request.get_json()

    generator = PolicyGenerator()
    policy = generator.generate(
        requirement=data.get('requirement'),
        policy_type=data.get('type'),
        output_format=data.get('format', 'both'),
        generate_tests=data.get('test_cases', True)
    )

    return jsonify(policy), 200

@policy_bp.route('/policy/validate', methods='POST')
@require_api_key
def validate_policy():
    """
    Validate Rego policy syntax and logic

    Request Body:
        {
            "policy": "<rego code>",
            "test_input": { ... }
        }
    """
    data = request.get_json()

    generator = PolicyGenerator()
    validation_result = generator.validate(
        policy_code=data.get('policy'),
        test_input=data.get('test_input')
    )

    return jsonify(validation_result), 200

@policy_bp.route('/policy/analyze', methods=['POST'])
@require_api_key
def analyze_configuration():
    """
    Analyze configuration for policy violations

    Request Body:
        {
            "config": { ... kubernetes manifest ... },
            "policies": ["approved-registries", "resource-limits"]
        }
    """
    data = request.get_json()

    generator = PolicyGenerator()
    violations = generator.analyze(
        config=data.get('config'),
        policies=data.get('policies', 'all')
    )

    return jsonify(violations), 200
```

---

## Related Skills

- `/compliance-mapper` - Map policies to compliance frameworks
- `/risk-assessment` - Assess risks from policy violations
- `/value-narrative` - Communicate policy value to stakeholders

## Related Agents

- `@policy-agent` - Policy analysis and generation
- `@risk-agent` - Risk assessment and mitigation
- `@governance-agent` - Compliance and reporting
- `@security-agent` - Security architecture

---

**Skill Owner**: Platform Program Management Repository
**Last Updated**: January 2026
**Version**: 1.0
