# Use Case Diagram — Technical Documentation Management System

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["Technical Writer"]
    actor_Primary2["Software Architect"]
    actor_Primary3["Developer Consumer"]
    actor_Primary4["QA Engineer"]

    subgraph SystemBoundary["Technical Documentation Management System"]
        UC01(["Author Technical Markdown Documentation"])
        UC02(["Build Static Docs Site Package"])
        UC03(["Manage Docs Versioning & Branching"])
        UC04(["Authenticate Author Session"])
        UC05(["Execute Full-Text Technical Search"])
        UC06(["Review & Approve Documentation PR"])
        UC07(["Embed Interactive Code Snippet Examples"])
        UC08(["Auto-Generate API Reference Docs"])
        UC09(["Configure Access Permission Scopes"])
        UC10(["Track Broken Hyperlinks in Docs"])
        UC11(["Manage Multilingual Documentation"])
        UC12(["Configure Site Custom Styling Themes"])
        UC13(["Generate Docs Reader Analytics"])
        UC14(["Export Documentation Audit Logs"])
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
| 1 | Technical Writer | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | Software Architect | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | Developer Consumer | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | QA Engineer | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Author Technical Markdown Documentation | Technical Writer | Supporting System | Handles author technical markdown documentation operations within system boundary | High |
| 2 | UC02 | Build Static Docs Site Package | Software Architect | Supporting System | Handles build static docs site package operations within system boundary | High |
| 3 | UC03 | Manage Docs Versioning & Branching | Developer Consumer | Supporting System | Handles manage docs versioning & branching operations within system boundary | High |
| 4 | UC04 | Authenticate Author Session | QA Engineer | Supporting System | Handles authenticate author session operations within system boundary | High |
| 5 | UC05 | Execute Full-Text Technical Search | Technical Writer | Supporting System | Handles execute full-text technical search operations within system boundary | High |
| 6 | UC06 | Review & Approve Documentation PR | Software Architect | Supporting System | Handles review & approve documentation pr operations within system boundary | High |
| 7 | UC07 | Embed Interactive Code Snippet Examples | Developer Consumer | Supporting System | Handles embed interactive code snippet examples operations within system boundary | Medium |
| 8 | UC08 | Auto-Generate API Reference Docs | QA Engineer | Supporting System | Handles auto-generate api reference docs operations within system boundary | High |
| 9 | UC09 | Configure Access Permission Scopes | Technical Writer | Supporting System | Handles configure access permission scopes operations within system boundary | High |
| 10 | UC10 | Track Broken Hyperlinks in Docs | Software Architect | Supporting System | Handles track broken hyperlinks in docs operations within system boundary | Medium |
| 11 | UC11 | Manage Multilingual Documentation | Developer Consumer | Supporting System | Handles manage multilingual documentation operations within system boundary | Low |
| 12 | UC12 | Configure Site Custom Styling Themes | QA Engineer | Supporting System | Handles configure site custom styling themes operations within system boundary | Low |
| 13 | UC13 | Generate Docs Reader Analytics | Technical Writer | Supporting System | Handles generate docs reader analytics operations within system boundary | Medium |
| 14 | UC14 | Export Documentation Audit Logs | Software Architect | Supporting System | Handles export documentation audit logs operations within system boundary | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Author Technical Markdown Documentation

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Author Technical Markdown Documentation |
| **Actor(s)** | Primary: Technical Writer |
| **Description** | Allows primary actors to configure and execute author technical markdown documentation within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Execute Full-Text Technical Search

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Execute Full-Text Technical Search |
| **Actor(s)** | Primary: Software Architect |
| **Description** | Executes execute full-text technical search with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Review & Approve Documentation PR

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Review & Approve Documentation PR |
| **Actor(s)** | Primary: Developer Consumer |
| **Description** | Performs review & approve documentation pr to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — Embed Interactive Code Snippet Examples

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | Embed Interactive Code Snippet Examples |
| **Actor(s)** | Primary: Developer Consumer |
| **Description** | Manages embed interactive code snippet examples to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Track Broken Hyperlinks in Docs

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Track Broken Hyperlinks in Docs |
| **Actor(s)** | Primary: QA Engineer |
| **Description** | Conducts track broken hyperlinks in docs for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
