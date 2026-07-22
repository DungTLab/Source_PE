# Use Case Diagram — Open Source Contribution Management System

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["Open Source Program Officer OSPO"]
    actor_Primary2["Software Engineer"]
    actor_Primary3["Corporate Legal Counsel"]
    actor_Primary4["Security Compliance Lead"]

    subgraph SystemBoundary["Open Source Contribution Management System"]
        UC01(["Submit Open Source Contribution Request"])
        UC02(["Scan Open Source License Compliance"])
        UC03(["Review & Sign Contributor License Agreement CLA"])
        UC04(["Authenticate Developer Session"])
        UC05(["Approve Open Source Project Release"])
        UC06(["Audit Proprietary Code Leak Risk"])
        UC07(["Manage Approved Open Source Library Catalog"])
        UC08(["Track Corporate Contributor Metrics"])
        UC09(["Review Legal IP Indemnification Rules"])
        UC10(["Sync External Pull Requests Status"])
        UC11(["Flag Incompatible Open Source Licenses"])
        UC12(["Configure Security Vulnerability Thresholds"])
        UC13(["Generate OSPO Program Impact Reports"])
        UC14(["Export Open Source Legal Compliance Audit Logs"])
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
| 1 | Open Source Program Officer OSPO | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | Software Engineer | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | Corporate Legal Counsel | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | Security Compliance Lead | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Submit Open Source Contribution Request | Open Source Program Officer OSPO | Supporting System | Handles submit open source contribution request operations within system boundary | High |
| 2 | UC02 | Scan Open Source License Compliance | Software Engineer | Supporting System | Handles scan open source license compliance operations within system boundary | High |
| 3 | UC03 | Review & Sign Contributor License Agreement CLA | Corporate Legal Counsel | Supporting System | Handles review & sign contributor license agreement cla operations within system boundary | High |
| 4 | UC04 | Authenticate Developer Session | Security Compliance Lead | Supporting System | Handles authenticate developer session operations within system boundary | High |
| 5 | UC05 | Approve Open Source Project Release | Open Source Program Officer OSPO | Supporting System | Handles approve open source project release operations within system boundary | High |
| 6 | UC06 | Audit Proprietary Code Leak Risk | Software Engineer | Supporting System | Handles audit proprietary code leak risk operations within system boundary | High |
| 7 | UC07 | Manage Approved Open Source Library Catalog | Corporate Legal Counsel | Supporting System | Handles manage approved open source library catalog operations within system boundary | Medium |
| 8 | UC08 | Track Corporate Contributor Metrics | Security Compliance Lead | Supporting System | Handles track corporate contributor metrics operations within system boundary | Medium |
| 9 | UC09 | Review Legal IP Indemnification Rules | Open Source Program Officer OSPO | Supporting System | Handles review legal ip indemnification rules operations within system boundary | High |
| 10 | UC10 | Sync External Pull Requests Status | Software Engineer | Supporting System | Handles sync external pull requests status operations within system boundary | Medium |
| 11 | UC11 | Flag Incompatible Open Source Licenses | Corporate Legal Counsel | Supporting System | Handles flag incompatible open source licenses operations within system boundary | High |
| 12 | UC12 | Configure Security Vulnerability Thresholds | Security Compliance Lead | Supporting System | Handles configure security vulnerability thresholds operations within system boundary | Medium |
| 13 | UC13 | Generate OSPO Program Impact Reports | Open Source Program Officer OSPO | Supporting System | Handles generate ospo program impact reports operations within system boundary | Medium |
| 14 | UC14 | Export Open Source Legal Compliance Audit Logs | Software Engineer | Supporting System | Handles export open source legal compliance audit logs operations within system boundary | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Submit Open Source Contribution Request

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Submit Open Source Contribution Request |
| **Actor(s)** | Primary: Open Source Program Officer OSPO |
| **Description** | Allows primary actors to configure and execute submit open source contribution request within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Approve Open Source Project Release

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Approve Open Source Project Release |
| **Actor(s)** | Primary: Software Engineer |
| **Description** | Executes approve open source project release with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Audit Proprietary Code Leak Risk

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Audit Proprietary Code Leak Risk |
| **Actor(s)** | Primary: Corporate Legal Counsel |
| **Description** | Performs audit proprietary code leak risk to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — Manage Approved Open Source Library Catalog

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | Manage Approved Open Source Library Catalog |
| **Actor(s)** | Primary: Corporate Legal Counsel |
| **Description** | Manages manage approved open source library catalog to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Sync External Pull Requests Status

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Sync External Pull Requests Status |
| **Actor(s)** | Primary: Security Compliance Lead |
| **Description** | Conducts sync external pull requests status for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
