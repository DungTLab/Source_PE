# Use Case Diagram — Incident & Problem Management System

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["Incident Commander"]
    actor_Primary2["Major Incident Manager"]
    actor_Primary3["Service Desk Agent"]
    actor_Primary4["Problem Manager"]

    subgraph SystemBoundary["Incident & Problem Management System"]
        UC01(["Log Major Incident Ticket"])
        UC02(["Assign Incident Response Team"])
        UC03(["Convene Emergency War Room Bridge"])
        UC04(["Authenticate Incident Manager Session"])
        UC05(["Apply Temporary Workaround Solution"])
        UC06(["Conduct Root Cause Analysis RCA"])
        UC07(["Log Problem Record from Recurring Incidents"])
        UC08(["Link Incident to CMDB CI Outage"])
        UC09(["Track SLA Response & Resolution Timers"])
        UC10(["Publish Known Error Database KEBD"])
        UC11(["Dispatch Outage Status Page Notification"])
        UC12(["Conduct Post-Incident Review PIR"])
        UC13(["Generate Incident MTTR & MTBF Metrics"])
        UC14(["Export ITIL Incident Audit Records"])
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
| 1 | Incident Commander | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | Major Incident Manager | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | Service Desk Agent | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | Problem Manager | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Log Major Incident Ticket | Incident Commander | Supporting System | Handles log major incident ticket operations within system boundary | High |
| 2 | UC02 | Assign Incident Response Team | Major Incident Manager | Supporting System | Handles assign incident response team operations within system boundary | High |
| 3 | UC03 | Convene Emergency War Room Bridge | Service Desk Agent | Supporting System | Handles convene emergency war room bridge operations within system boundary | High |
| 4 | UC04 | Authenticate Incident Manager Session | Problem Manager | Supporting System | Handles authenticate incident manager session operations within system boundary | High |
| 5 | UC05 | Apply Temporary Workaround Solution | Incident Commander | Supporting System | Handles apply temporary workaround solution operations within system boundary | High |
| 6 | UC06 | Conduct Root Cause Analysis RCA | Major Incident Manager | Supporting System | Handles conduct root cause analysis rca operations within system boundary | High |
| 7 | UC07 | Log Problem Record from Recurring Incidents | Service Desk Agent | Supporting System | Handles log problem record from recurring incidents operations within system boundary | High |
| 8 | UC08 | Link Incident to CMDB CI Outage | Problem Manager | Supporting System | Handles link incident to cmdb ci outage operations within system boundary | High |
| 9 | UC09 | Track SLA Response & Resolution Timers | Incident Commander | Supporting System | Handles track sla response & resolution timers operations within system boundary | High |
| 10 | UC10 | Publish Known Error Database KEBD | Major Incident Manager | Supporting System | Handles publish known error database kebd operations within system boundary | Medium |
| 11 | UC11 | Dispatch Outage Status Page Notification | Service Desk Agent | Supporting System | Handles dispatch outage status page notification operations within system boundary | Medium |
| 12 | UC12 | Conduct Post-Incident Review PIR | Problem Manager | Supporting System | Handles conduct post-incident review pir operations within system boundary | Medium |
| 13 | UC13 | Generate Incident MTTR & MTBF Metrics | Incident Commander | Supporting System | Handles generate incident mttr & mtbf metrics operations within system boundary | Medium |
| 14 | UC14 | Export ITIL Incident Audit Records | Major Incident Manager | Supporting System | Handles export itil incident audit records operations within system boundary | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Log Major Incident Ticket

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Log Major Incident Ticket |
| **Actor(s)** | Primary: Incident Commander |
| **Description** | Allows primary actors to configure and execute log major incident ticket within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Apply Temporary Workaround Solution

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Apply Temporary Workaround Solution |
| **Actor(s)** | Primary: Major Incident Manager |
| **Description** | Executes apply temporary workaround solution with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Conduct Root Cause Analysis RCA

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Conduct Root Cause Analysis RCA |
| **Actor(s)** | Primary: Service Desk Agent |
| **Description** | Performs conduct root cause analysis rca to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — Log Problem Record from Recurring Incidents

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | Log Problem Record from Recurring Incidents |
| **Actor(s)** | Primary: Service Desk Agent |
| **Description** | Manages log problem record from recurring incidents to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Publish Known Error Database KEBD

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Publish Known Error Database KEBD |
| **Actor(s)** | Primary: Problem Manager |
| **Description** | Conducts publish known error database kebd for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
