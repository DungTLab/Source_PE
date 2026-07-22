# Use Case Diagram — IT Vendor & Contract Management System

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["IT Procurement Manager"]
    actor_Primary2["Vendor Relationship Lead"]
    actor_Primary3["Chief Information Officer CIO"]
    actor_Primary4["Legal Counsel"]

    subgraph SystemBoundary["IT Vendor & Contract Management System"]
        UC01(["Register IT Vendor Master Profile"])
        UC02(["Create IT Software & Hardware Contract"])
        UC03(["Evaluate Vendor Performance Scorecard"])
        UC04(["Authenticate Procurement Session"])
        UC05(["Track Contract Renewal Expiration Alerts"])
        UC06(["Manage Vendor Support SLA Agreements"])
        UC07(["Upload Signed Contract E-Signature"])
        UC08(["Conduct Vendor Security Risk Assessment"])
        UC09(["Track IT Vendor Spend vs Budget"])
        UC10(["Negotiate Contract Term Revision"])
        UC11(["Manage Vendor Incident Escalation Contacts"])
        UC12(["Configure Vendor Category Taxonomy"])
        UC13(["Generate Executive IT Vendor Spend Reports"])
        UC14(["Export Vendor Contract Compliance Audit Logs"])
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
| 1 | IT Procurement Manager | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | Vendor Relationship Lead | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | Chief Information Officer CIO | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | Legal Counsel | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Register IT Vendor Master Profile | IT Procurement Manager | Supporting System | Handles register it vendor master profile operations within system boundary | High |
| 2 | UC02 | Create IT Software & Hardware Contract | Vendor Relationship Lead | Supporting System | Handles create it software & hardware contract operations within system boundary | High |
| 3 | UC03 | Evaluate Vendor Performance Scorecard | Chief Information Officer CIO | Supporting System | Handles evaluate vendor performance scorecard operations within system boundary | High |
| 4 | UC04 | Authenticate Procurement Session | Legal Counsel | Supporting System | Handles authenticate procurement session operations within system boundary | High |
| 5 | UC05 | Track Contract Renewal Expiration Alerts | IT Procurement Manager | Supporting System | Handles track contract renewal expiration alerts operations within system boundary | High |
| 6 | UC06 | Manage Vendor Support SLA Agreements | Vendor Relationship Lead | Supporting System | Handles manage vendor support sla agreements operations within system boundary | High |
| 7 | UC07 | Upload Signed Contract E-Signature | Chief Information Officer CIO | Supporting System | Handles upload signed contract e-signature operations within system boundary | High |
| 8 | UC08 | Conduct Vendor Security Risk Assessment | Legal Counsel | Supporting System | Handles conduct vendor security risk assessment operations within system boundary | High |
| 9 | UC09 | Track IT Vendor Spend vs Budget | IT Procurement Manager | Supporting System | Handles track it vendor spend vs budget operations within system boundary | Medium |
| 10 | UC10 | Negotiate Contract Term Revision | Vendor Relationship Lead | Supporting System | Handles negotiate contract term revision operations within system boundary | Medium |
| 11 | UC11 | Manage Vendor Incident Escalation Contacts | Chief Information Officer CIO | Supporting System | Handles manage vendor incident escalation contacts operations within system boundary | Medium |
| 12 | UC12 | Configure Vendor Category Taxonomy | Legal Counsel | Supporting System | Handles configure vendor category taxonomy operations within system boundary | Low |
| 13 | UC13 | Generate Executive IT Vendor Spend Reports | IT Procurement Manager | Supporting System | Handles generate executive it vendor spend reports operations within system boundary | Medium |
| 14 | UC14 | Export Vendor Contract Compliance Audit Logs | Vendor Relationship Lead | Supporting System | Handles export vendor contract compliance audit logs operations within system boundary | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Register IT Vendor Master Profile

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Register IT Vendor Master Profile |
| **Actor(s)** | Primary: IT Procurement Manager |
| **Description** | Allows primary actors to configure and execute register it vendor master profile within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Track Contract Renewal Expiration Alerts

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Track Contract Renewal Expiration Alerts |
| **Actor(s)** | Primary: Vendor Relationship Lead |
| **Description** | Executes track contract renewal expiration alerts with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Manage Vendor Support SLA Agreements

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Manage Vendor Support SLA Agreements |
| **Actor(s)** | Primary: Chief Information Officer CIO |
| **Description** | Performs manage vendor support sla agreements to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — Upload Signed Contract E-Signature

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | Upload Signed Contract E-Signature |
| **Actor(s)** | Primary: Chief Information Officer CIO |
| **Description** | Manages upload signed contract e-signature to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Negotiate Contract Term Revision

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Negotiate Contract Term Revision |
| **Actor(s)** | Primary: Legal Counsel |
| **Description** | Conducts negotiate contract term revision for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
