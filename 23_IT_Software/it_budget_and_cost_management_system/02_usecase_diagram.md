# Use Case Diagram — IT Budget & Cost Management System

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["IT Financial Controller"]
    actor_Primary2["Chief Information Officer CIO"]
    actor_Primary3["IT Department Manager"]
    actor_Primary4["Finance Auditor"]

    subgraph SystemBoundary["IT Budget & Cost Management System"]
        UC01(["Formulate Annual IT OpEx CapEx Budget"])
        UC02(["Allocate Budget to Department Cost Centers"])
        UC03(["Track Actual IT Spend vs Budget Variance"])
        UC04(["Authenticate Financial Controller Session"])
        UC05(["Approve IT Capital Expenditure Request"])
        UC06(["Consolidate Multi-Cloud & Vendor Bills"])
        UC07(["Configure Budget Overrun Alert Triggers"])
        UC08(["Execute IT Cost Center Chargeback"])
        UC09(["Forecast Year-End IT Expenditure"])
        UC10(["Manage IT Software Subscription Costs"])
        UC11(["Analyze Total Cost of Ownership TCO"])
        UC12(["Configure Cost Allocation Categories"])
        UC13(["Generate CIO Executive Financial Dashboard"])
        UC14(["Export IT Financial Compliance Audit Logs"])
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
| 1 | IT Financial Controller | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | Chief Information Officer CIO | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | IT Department Manager | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | Finance Auditor | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Formulate Annual IT OpEx CapEx Budget | IT Financial Controller | Supporting System | Handles formulate annual it opex capex budget operations within system boundary | High |
| 2 | UC02 | Allocate Budget to Department Cost Centers | Chief Information Officer CIO | Supporting System | Handles allocate budget to department cost centers operations within system boundary | High |
| 3 | UC03 | Track Actual IT Spend vs Budget Variance | IT Department Manager | Supporting System | Handles track actual it spend vs budget variance operations within system boundary | High |
| 4 | UC04 | Authenticate Financial Controller Session | Finance Auditor | Supporting System | Handles authenticate financial controller session operations within system boundary | High |
| 5 | UC05 | Approve IT Capital Expenditure Request | IT Financial Controller | Supporting System | Handles approve it capital expenditure request operations within system boundary | High |
| 6 | UC06 | Consolidate Multi-Cloud & Vendor Bills | Chief Information Officer CIO | Supporting System | Handles consolidate multi-cloud & vendor bills operations within system boundary | High |
| 7 | UC07 | Configure Budget Overrun Alert Triggers | IT Department Manager | Supporting System | Handles configure budget overrun alert triggers operations within system boundary | High |
| 8 | UC08 | Execute IT Cost Center Chargeback | Finance Auditor | Supporting System | Handles execute it cost center chargeback operations within system boundary | Medium |
| 9 | UC09 | Forecast Year-End IT Expenditure | IT Financial Controller | Supporting System | Handles forecast year-end it expenditure operations within system boundary | Medium |
| 10 | UC10 | Manage IT Software Subscription Costs | Chief Information Officer CIO | Supporting System | Handles manage it software subscription costs operations within system boundary | High |
| 11 | UC11 | Analyze Total Cost of Ownership TCO | IT Department Manager | Supporting System | Handles analyze total cost of ownership tco operations within system boundary | Medium |
| 12 | UC12 | Configure Cost Allocation Categories | Finance Auditor | Supporting System | Handles configure cost allocation categories operations within system boundary | Low |
| 13 | UC13 | Generate CIO Executive Financial Dashboard | IT Financial Controller | Supporting System | Handles generate cio executive financial dashboard operations within system boundary | Medium |
| 14 | UC14 | Export IT Financial Compliance Audit Logs | Chief Information Officer CIO | Supporting System | Handles export it financial compliance audit logs operations within system boundary | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Formulate Annual IT OpEx CapEx Budget

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Formulate Annual IT OpEx CapEx Budget |
| **Actor(s)** | Primary: IT Financial Controller |
| **Description** | Allows primary actors to configure and execute formulate annual it opex capex budget within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Approve IT Capital Expenditure Request

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Approve IT Capital Expenditure Request |
| **Actor(s)** | Primary: Chief Information Officer CIO |
| **Description** | Executes approve it capital expenditure request with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Consolidate Multi-Cloud & Vendor Bills

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Consolidate Multi-Cloud & Vendor Bills |
| **Actor(s)** | Primary: IT Department Manager |
| **Description** | Performs consolidate multi-cloud & vendor bills to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — Configure Budget Overrun Alert Triggers

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | Configure Budget Overrun Alert Triggers |
| **Actor(s)** | Primary: IT Department Manager |
| **Description** | Manages configure budget overrun alert triggers to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Manage IT Software Subscription Costs

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Manage IT Software Subscription Costs |
| **Actor(s)** | Primary: Finance Auditor |
| **Description** | Conducts manage it software subscription costs for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
