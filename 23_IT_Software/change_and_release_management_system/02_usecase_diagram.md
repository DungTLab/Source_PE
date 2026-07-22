# Use Case Diagram — Change & Release Management System

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["Change Advisory Board (CAB) Chair"]
    actor_Primary2["Release Manager"]
    actor_Primary3["DevOps Lead"]
    actor_Primary4["Service Manager"]

    subgraph SystemBoundary["Change & Release Management System"]
        UC01(["Submit Request for Change RFC"])
        UC02(["Evaluate Change Risk & Blast Radius"])
        UC03(["Conduct CAB Approval Meeting"])
        UC04(["Authenticate User Session"])
        UC05(["Schedule Release Maintenance Window"])
        UC06(["Trigger Production Release Deployment"])
        UC07(["Execute Emergency Rollback Plan"])
        UC08(["Link RFC to CMDB CIs and Incidents"])
        UC09(["Manage Release Candidate Packages"])
        UC10(["Conduct Post-Implementation Review PIR"])
        UC11(["Track Unauthorized Production Changes"])
        UC12(["Configure Automated Change Approval Rules"])
        UC13(["Generate Release Success Rate Reports"])
        UC14(["Export ITIL Change Audit Evidence"])
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
| 1 | Change Advisory Board (CAB) Chair | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | Release Manager | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | DevOps Lead | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | Service Manager | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Submit Request for Change RFC | Change Advisory Board (CAB) Chair | Supporting System | Handles submit request for change rfc operations within system boundary | High |
| 2 | UC02 | Evaluate Change Risk & Blast Radius | Release Manager | Supporting System | Handles evaluate change risk & blast radius operations within system boundary | High |
| 3 | UC03 | Conduct CAB Approval Meeting | DevOps Lead | Supporting System | Handles conduct cab approval meeting operations within system boundary | High |
| 4 | UC04 | Authenticate User Session | Service Manager | Supporting System | Handles authenticate user session operations within system boundary | High |
| 5 | UC05 | Schedule Release Maintenance Window | Change Advisory Board (CAB) Chair | Supporting System | Handles schedule release maintenance window operations within system boundary | High |
| 6 | UC06 | Trigger Production Release Deployment | Release Manager | Supporting System | Handles trigger production release deployment operations within system boundary | High |
| 7 | UC07 | Execute Emergency Rollback Plan | DevOps Lead | Supporting System | Handles execute emergency rollback plan operations within system boundary | High |
| 8 | UC08 | Link RFC to CMDB CIs and Incidents | Service Manager | Supporting System | Handles link rfc to cmdb cis and incidents operations within system boundary | High |
| 9 | UC09 | Manage Release Candidate Packages | Change Advisory Board (CAB) Chair | Supporting System | Handles manage release candidate packages operations within system boundary | Medium |
| 10 | UC10 | Conduct Post-Implementation Review PIR | Release Manager | Supporting System | Handles conduct post-implementation review pir operations within system boundary | Medium |
| 11 | UC11 | Track Unauthorized Production Changes | DevOps Lead | Supporting System | Handles track unauthorized production changes operations within system boundary | High |
| 12 | UC12 | Configure Automated Change Approval Rules | Service Manager | Supporting System | Handles configure automated change approval rules operations within system boundary | Medium |
| 13 | UC13 | Generate Release Success Rate Reports | Change Advisory Board (CAB) Chair | Supporting System | Handles generate release success rate reports operations within system boundary | Medium |
| 14 | UC14 | Export ITIL Change Audit Evidence | Release Manager | Supporting System | Handles export itil change audit evidence operations within system boundary | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Submit Request for Change RFC

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Submit Request for Change RFC |
| **Actor(s)** | Primary: Change Advisory Board (CAB) Chair |
| **Description** | Allows primary actors to configure and execute submit request for change rfc within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Schedule Release Maintenance Window

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Schedule Release Maintenance Window |
| **Actor(s)** | Primary: Release Manager |
| **Description** | Executes schedule release maintenance window with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Trigger Production Release Deployment

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Trigger Production Release Deployment |
| **Actor(s)** | Primary: DevOps Lead |
| **Description** | Performs trigger production release deployment to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — Execute Emergency Rollback Plan

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | Execute Emergency Rollback Plan |
| **Actor(s)** | Primary: DevOps Lead |
| **Description** | Manages execute emergency rollback plan to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Conduct Post-Implementation Review PIR

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Conduct Post-Implementation Review PIR |
| **Actor(s)** | Primary: Service Manager |
| **Description** | Conducts conduct post-implementation review pir for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
