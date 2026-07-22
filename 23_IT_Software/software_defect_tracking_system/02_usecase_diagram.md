# Use Case Diagram — Software Defect Tracking System

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["QA Test Lead"]
    actor_Primary2["Software Developer"]
    actor_Primary3["Product Manager"]
    actor_Primary4["Release Lead"]

    subgraph SystemBoundary["Software Defect Tracking System"]
        UC01(["Submit Defect Bug Report"])
        UC02(["Triage Defect Severity & Priority"])
        UC03(["Assign Defect to Developer"])
        UC04(["Authenticate User Session"])
        UC05(["Update Defect Fix Verification Status"])
        UC06(["Link Defect to Git Commit Hash"])
        UC07(["Close Verified Defect Ticket"])
        UC08(["Reopen Unresolved Defect Ticket"])
        UC09(["Manage Defect Component Categories"])
        UC10(["Track Defect Resolution SLA Timers"])
        UC11(["Flag Duplicate Defect Entries"])
        UC12(["Configure Defect Notification Rules"])
        UC13(["Generate Defect Density & Aging Metrics"])
        UC14(["Export Defect Quality Audit Trail"])
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
| 1 | QA Test Lead | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | Software Developer | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | Product Manager | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | Release Lead | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Submit Defect Bug Report | QA Test Lead | Supporting System | Handles submit defect bug report operations within system boundary | High |
| 2 | UC02 | Triage Defect Severity & Priority | Software Developer | Supporting System | Handles triage defect severity & priority operations within system boundary | High |
| 3 | UC03 | Assign Defect to Developer | Product Manager | Supporting System | Handles assign defect to developer operations within system boundary | High |
| 4 | UC04 | Authenticate User Session | Release Lead | Supporting System | Handles authenticate user session operations within system boundary | High |
| 5 | UC05 | Update Defect Fix Verification Status | QA Test Lead | Supporting System | Handles update defect fix verification status operations within system boundary | High |
| 6 | UC06 | Link Defect to Git Commit Hash | Software Developer | Supporting System | Handles link defect to git commit hash operations within system boundary | High |
| 7 | UC07 | Close Verified Defect Ticket | Product Manager | Supporting System | Handles close verified defect ticket operations within system boundary | High |
| 8 | UC08 | Reopen Unresolved Defect Ticket | Release Lead | Supporting System | Handles reopen unresolved defect ticket operations within system boundary | Medium |
| 9 | UC09 | Manage Defect Component Categories | QA Test Lead | Supporting System | Handles manage defect component categories operations within system boundary | Medium |
| 10 | UC10 | Track Defect Resolution SLA Timers | Software Developer | Supporting System | Handles track defect resolution sla timers operations within system boundary | High |
| 11 | UC11 | Flag Duplicate Defect Entries | Product Manager | Supporting System | Handles flag duplicate defect entries operations within system boundary | Medium |
| 12 | UC12 | Configure Defect Notification Rules | Release Lead | Supporting System | Handles configure defect notification rules operations within system boundary | Low |
| 13 | UC13 | Generate Defect Density & Aging Metrics | QA Test Lead | Supporting System | Handles generate defect density & aging metrics operations within system boundary | Medium |
| 14 | UC14 | Export Defect Quality Audit Trail | Software Developer | Supporting System | Handles export defect quality audit trail operations within system boundary | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Submit Defect Bug Report

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Submit Defect Bug Report |
| **Actor(s)** | Primary: QA Test Lead |
| **Description** | Allows primary actors to configure and execute submit defect bug report within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Update Defect Fix Verification Status

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Update Defect Fix Verification Status |
| **Actor(s)** | Primary: Software Developer |
| **Description** | Executes update defect fix verification status with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Link Defect to Git Commit Hash

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Link Defect to Git Commit Hash |
| **Actor(s)** | Primary: Product Manager |
| **Description** | Performs link defect to git commit hash to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — Close Verified Defect Ticket

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | Close Verified Defect Ticket |
| **Actor(s)** | Primary: Product Manager |
| **Description** | Manages close verified defect ticket to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Track Defect Resolution SLA Timers

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Track Defect Resolution SLA Timers |
| **Actor(s)** | Primary: Release Lead |
| **Description** | Conducts track defect resolution sla timers for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
