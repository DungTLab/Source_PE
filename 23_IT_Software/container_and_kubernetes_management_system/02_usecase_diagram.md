# Use Case Diagram — Container & Kubernetes Management System

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["Kubernetes Administrator"]
    actor_Primary2["DevOps Engineer"]
    actor_Primary3["Cloud Architect"]
    actor_Primary4["Security Auditor"]

    subgraph SystemBoundary["Container & Kubernetes Management System"]
        UC01(["Provision Kubernetes Cluster Node Pool"])
        UC02(["Deploy Helm Chart Manifest Package"])
        UC03(["Configure Horizontal Pod Autoscaler HPA"])
        UC04(["Authenticate K8s Admin Session"])
        UC05(["Monitor Real-Time Pod Resource Metrics"])
        UC06(["Configure Namespace RBAC Access Rules"])
        UC07(["Execute Rolling Deployment Update"])
        UC08(["Manage Ingress Controller Routing"])
        UC09(["Enforce Pod Security Standards PSS"])
        UC10(["Troubleshoot CrashLoopBackOff Pod Logs"])
        UC11(["Configure Persistent Volume Claims PVC"])
        UC12(["Execute Cluster Node Upgrade Drain"])
        UC13(["Generate Cluster Resource Utilization Metrics"])
        UC14(["Export Kubernetes Security Audit Trail"])
    end

    actor_Primary1 --> UC01
    actor_Primary1 --> UC02
    actor_Primary1 --> UC03

    UC05 -.->|"<<include>>"| UC04
    UC06 -.->|"<<extend>>"| UC05

    actor_Primary2 --> UC05
    actor_Primary2 --> UC06

    actor_Primary3 --> UC07
    actor_Primary3 --> UC08

    actor_Primary4 --> UC10
    actor_Primary4 --> UC13
    actor_Primary4 --> UC14
```

## Actor Table | Bảng Actor

| # | Actor | Actor Type | Role Description | Related Use Cases |
|---|-------|------------|------------------|-------------------|
| 1 | Kubernetes Administrator | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | DevOps Engineer | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | Cloud Architect | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | Security Auditor | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Provision Kubernetes Cluster Node Pool | Kubernetes Administrator | Supporting System | Handles provision kubernetes cluster node pool operations within system boundary | High |
| 2 | UC02 | Deploy Helm Chart Manifest Package | DevOps Engineer | Supporting System | Handles deploy helm chart manifest package operations within system boundary | High |
| 3 | UC03 | Configure Horizontal Pod Autoscaler HPA | Cloud Architect | Supporting System | Handles configure horizontal pod autoscaler hpa operations within system boundary | High |
| 4 | UC04 | Authenticate K8s Admin Session | Security Auditor | Supporting System | Handles authenticate k8s admin session operations within system boundary | High |
| 5 | UC05 | Monitor Real-Time Pod Resource Metrics | Kubernetes Administrator | Supporting System | Handles monitor real-time pod resource metrics operations within system boundary | High |
| 6 | UC06 | Configure Namespace RBAC Access Rules | DevOps Engineer | Supporting System | Handles configure namespace rbac access rules operations within system boundary | High |
| 7 | UC07 | Execute Rolling Deployment Update | Cloud Architect | Supporting System | Handles execute rolling deployment update operations within system boundary | High |
| 8 | UC08 | Manage Ingress Controller Routing | Security Auditor | Supporting System | Handles manage ingress controller routing operations within system boundary | Medium |
| 9 | UC09 | Enforce Pod Security Standards PSS | Kubernetes Administrator | Supporting System | Handles enforce pod security standards pss operations within system boundary | High |
| 10 | UC10 | Troubleshoot CrashLoopBackOff Pod Logs | DevOps Engineer | Supporting System | Handles troubleshoot crashloopbackoff pod logs operations within system boundary | High |
| 11 | UC11 | Configure Persistent Volume Claims PVC | Cloud Architect | Supporting System | Handles configure persistent volume claims pvc operations within system boundary | Medium |
| 12 | UC12 | Execute Cluster Node Upgrade Drain | Security Auditor | Supporting System | Handles execute cluster node upgrade drain operations within system boundary | Medium |
| 13 | UC13 | Generate Cluster Resource Utilization Metrics | Kubernetes Administrator | Supporting System | Handles generate cluster resource utilization metrics operations within system boundary | Medium |
| 14 | UC14 | Export Kubernetes Security Audit Trail | DevOps Engineer | Supporting System | Handles export kubernetes security audit trail operations within system boundary | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Provision Kubernetes Cluster Node Pool

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Provision Kubernetes Cluster Node Pool |
| **Actor(s)** | Primary: Kubernetes Administrator |
| **Description** | Allows primary actors to configure and execute provision kubernetes cluster node pool within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Monitor Real-Time Pod Resource Metrics

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Monitor Real-Time Pod Resource Metrics |
| **Actor(s)** | Primary: DevOps Engineer |
| **Description** | Executes monitor real-time pod resource metrics with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Configure Namespace RBAC Access Rules

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Configure Namespace RBAC Access Rules |
| **Actor(s)** | Primary: Cloud Architect |
| **Description** | Performs configure namespace rbac access rules to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — Execute Rolling Deployment Update

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | Execute Rolling Deployment Update |
| **Actor(s)** | Primary: Cloud Architect |
| **Description** | Manages execute rolling deployment update to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Troubleshoot CrashLoopBackOff Pod Logs

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Troubleshoot CrashLoopBackOff Pod Logs |
| **Actor(s)** | Primary: Security Auditor |
| **Description** | Conducts troubleshoot crashloopbackoff pod logs for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
