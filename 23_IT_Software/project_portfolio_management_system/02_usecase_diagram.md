# Use Case Diagram — Project Portfolio Management System

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["Portfolio Management Officer"]
    actor_Primary2["Project Manager"]
    actor_Primary3["Resource Manager"]
    actor_Primary4["Finance Director"]

    subgraph SystemBoundary["Project Portfolio Management System"]
        UC01(["Create Project Proposal Charter"])
        UC02(["Evaluate Project Portfolio Ranking"])
        UC03(["Allocate Cross-Project Resources"])
        UC04(["Authenticate User Session"])
        UC05(["Monitor Portfolio Financial Budget"])
        UC06(["Track Project Milestone Progress"])
        UC07(["Manage Portfolio Risk Register"])
        UC08(["Simulate What-If Scenario Capacity"])
        UC09(["Approve Stage-Gate Project Transition"])
        UC10(["Sync Timesheet Actual Costs"])
        UC11(["Resolve Resource Over-allocation Conflicts"])
        UC12(["Configure Portfolio Alignment Strategy"])
        UC13(["Generate Executive Portfolio Summary"])
        UC14(["Export Capital Expense Audit Logs"])
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
| 1 | Portfolio Management Officer | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | Project Manager | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | Resource Manager | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | Finance Director | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Create Project Proposal Charter | Portfolio Management Officer | Supporting System | Handles create project proposal charter operations within system boundary | High |
| 2 | UC02 | Evaluate Project Portfolio Ranking | Project Manager | Supporting System | Handles evaluate project portfolio ranking operations within system boundary | High |
| 3 | UC03 | Allocate Cross-Project Resources | Resource Manager | Supporting System | Handles allocate cross-project resources operations within system boundary | High |
| 4 | UC04 | Authenticate User Session | Finance Director | Supporting System | Handles authenticate user session operations within system boundary | High |
| 5 | UC05 | Monitor Portfolio Financial Budget | Portfolio Management Officer | Supporting System | Handles monitor portfolio financial budget operations within system boundary | High |
| 6 | UC06 | Track Project Milestone Progress | Project Manager | Supporting System | Handles track project milestone progress operations within system boundary | High |
| 7 | UC07 | Manage Portfolio Risk Register | Resource Manager | Supporting System | Handles manage portfolio risk register operations within system boundary | High |
| 8 | UC08 | Simulate What-If Scenario Capacity | Finance Director | Supporting System | Handles simulate what-if scenario capacity operations within system boundary | Medium |
| 9 | UC09 | Approve Stage-Gate Project Transition | Portfolio Management Officer | Supporting System | Handles approve stage-gate project transition operations within system boundary | High |
| 10 | UC10 | Sync Timesheet Actual Costs | Project Manager | Supporting System | Handles sync timesheet actual costs operations within system boundary | Medium |
| 11 | UC11 | Resolve Resource Over-allocation Conflicts | Resource Manager | Supporting System | Handles resolve resource over-allocation conflicts operations within system boundary | Medium |
| 12 | UC12 | Configure Portfolio Alignment Strategy | Finance Director | Supporting System | Handles configure portfolio alignment strategy operations within system boundary | Medium |
| 13 | UC13 | Generate Executive Portfolio Summary | Portfolio Management Officer | Supporting System | Handles generate executive portfolio summary operations within system boundary | Medium |
| 14 | UC14 | Export Capital Expense Audit Logs | Project Manager | Supporting System | Handles export capital expense audit logs operations within system boundary | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Create Project Proposal Charter

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Create Project Proposal Charter |
| **Actor(s)** | Primary: Portfolio Management Officer |
| **Description** | Allows primary actors to configure and execute create project proposal charter within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Monitor Portfolio Financial Budget

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Monitor Portfolio Financial Budget |
| **Actor(s)** | Primary: Project Manager |
| **Description** | Executes monitor portfolio financial budget with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Track Project Milestone Progress

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Track Project Milestone Progress |
| **Actor(s)** | Primary: Resource Manager |
| **Description** | Performs track project milestone progress to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — Manage Portfolio Risk Register

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | Manage Portfolio Risk Register |
| **Actor(s)** | Primary: Resource Manager |
| **Description** | Manages manage portfolio risk register to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Sync Timesheet Actual Costs

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Sync Timesheet Actual Costs |
| **Actor(s)** | Primary: Finance Director |
| **Description** | Conducts sync timesheet actual costs for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
