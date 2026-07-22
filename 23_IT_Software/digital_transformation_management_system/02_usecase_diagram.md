# Use Case Diagram — Digital Transformation Management System

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["Chief Digital Officer CDO"]
    actor_Primary2["Digital Transformation Lead"]
    actor_Primary3["Enterprise Architect"]
    actor_Primary4["Business Unit Head"]

    subgraph SystemBoundary["Digital Transformation Management System"]
        UC01(["Create Digital Transformation Roadmap"])
        UC02(["Evaluate Digital Maturity Score"])
        UC03(["Track Digital Project Value Realization"])
        UC04(["Authenticate Executive Session"])
        UC05(["Monitor Digital Adoption Index DAI"])
        UC06(["Manage Legacy System Modernization Plan"])
        UC07(["Track Employee Digital Upskilling KPI"])
        UC08(["Manage Process Automation Initiatives"])
        UC09(["Align Digital Strategy to Business Goals"])
        UC10(["Review Digital Change Management Risks"])
        UC11(["Track Cloud Migration Milestones"])
        UC12(["Configure Digital KPI Weighting Matrix"])
        UC13(["Generate CDO Executive Transformation Report"])
        UC14(["Export Governance & Strategy Audit Logs"])
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
| 1 | Chief Digital Officer CDO | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | Digital Transformation Lead | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | Enterprise Architect | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | Business Unit Head | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Create Digital Transformation Roadmap | Chief Digital Officer CDO | Supporting System | Handles create digital transformation roadmap operations within system boundary | High |
| 2 | UC02 | Evaluate Digital Maturity Score | Digital Transformation Lead | Supporting System | Handles evaluate digital maturity score operations within system boundary | High |
| 3 | UC03 | Track Digital Project Value Realization | Enterprise Architect | Supporting System | Handles track digital project value realization operations within system boundary | High |
| 4 | UC04 | Authenticate Executive Session | Business Unit Head | Supporting System | Handles authenticate executive session operations within system boundary | High |
| 5 | UC05 | Monitor Digital Adoption Index DAI | Chief Digital Officer CDO | Supporting System | Handles monitor digital adoption index dai operations within system boundary | High |
| 6 | UC06 | Manage Legacy System Modernization Plan | Digital Transformation Lead | Supporting System | Handles manage legacy system modernization plan operations within system boundary | High |
| 7 | UC07 | Track Employee Digital Upskilling KPI | Enterprise Architect | Supporting System | Handles track employee digital upskilling kpi operations within system boundary | Medium |
| 8 | UC08 | Manage Process Automation Initiatives | Business Unit Head | Supporting System | Handles manage process automation initiatives operations within system boundary | High |
| 9 | UC09 | Align Digital Strategy to Business Goals | Chief Digital Officer CDO | Supporting System | Handles align digital strategy to business goals operations within system boundary | Medium |
| 10 | UC10 | Review Digital Change Management Risks | Digital Transformation Lead | Supporting System | Handles review digital change management risks operations within system boundary | Medium |
| 11 | UC11 | Track Cloud Migration Milestones | Enterprise Architect | Supporting System | Handles track cloud migration milestones operations within system boundary | Medium |
| 12 | UC12 | Configure Digital KPI Weighting Matrix | Business Unit Head | Supporting System | Handles configure digital kpi weighting matrix operations within system boundary | Low |
| 13 | UC13 | Generate CDO Executive Transformation Report | Chief Digital Officer CDO | Supporting System | Handles generate cdo executive transformation report operations within system boundary | Medium |
| 14 | UC14 | Export Governance & Strategy Audit Logs | Digital Transformation Lead | Supporting System | Handles export governance & strategy audit logs operations within system boundary | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Create Digital Transformation Roadmap

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Create Digital Transformation Roadmap |
| **Actor(s)** | Primary: Chief Digital Officer CDO |
| **Description** | Allows primary actors to configure and execute create digital transformation roadmap within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Monitor Digital Adoption Index DAI

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Monitor Digital Adoption Index DAI |
| **Actor(s)** | Primary: Digital Transformation Lead |
| **Description** | Executes monitor digital adoption index dai with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Manage Legacy System Modernization Plan

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Manage Legacy System Modernization Plan |
| **Actor(s)** | Primary: Enterprise Architect |
| **Description** | Performs manage legacy system modernization plan to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — Track Employee Digital Upskilling KPI

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | Track Employee Digital Upskilling KPI |
| **Actor(s)** | Primary: Enterprise Architect |
| **Description** | Manages track employee digital upskilling kpi to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Review Digital Change Management Risks

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Review Digital Change Management Risks |
| **Actor(s)** | Primary: Business Unit Head |
| **Description** | Conducts review digital change management risks for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
