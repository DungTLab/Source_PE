# Use Case Diagram — Knowledge Base Management System

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["Knowledge Base Manager"]
    actor_Primary2["Technical Author"]
    actor_Primary3["Enterprise Support Staff"]
    actor_Primary4["End User Customer"]

    subgraph SystemBoundary["Knowledge Base Management System"]
        UC01(["Author Knowledge Base Article"])
        UC02(["Review & Publish KB Article"])
        UC03(["Execute AI Semantic KB Search"])
        UC04(["Authenticate User Session"])
        UC05(["Rate Article Helpfulness & Feedback"])
        UC06(["Track Outdated KB Article Expiry"])
        UC07(["Manage Knowledge Taxonomy Categories"])
        UC08(["Link KB Article to Support Ticket"])
        UC09(["Configure Internal vs Public Access"])
        UC10(["Monitor Popular Article View Trends"])
        UC11(["Import Bulk Knowledge Documents"])
        UC12(["Configure Machine Translation Support"])
        UC13(["Generate Deflection Efficiency Reports"])
        UC14(["Export Content Quality Audit Logs"])
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
| 1 | Knowledge Base Manager | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | Technical Author | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | Enterprise Support Staff | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | End User Customer | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Author Knowledge Base Article | Knowledge Base Manager | Supporting System | Handles author knowledge base article operations within system boundary | High |
| 2 | UC02 | Review & Publish KB Article | Technical Author | Supporting System | Handles review & publish kb article operations within system boundary | High |
| 3 | UC03 | Execute AI Semantic KB Search | Enterprise Support Staff | Supporting System | Handles execute ai semantic kb search operations within system boundary | High |
| 4 | UC04 | Authenticate User Session | End User Customer | Supporting System | Handles authenticate user session operations within system boundary | High |
| 5 | UC05 | Rate Article Helpfulness & Feedback | Knowledge Base Manager | Supporting System | Handles rate article helpfulness & feedback operations within system boundary | High |
| 6 | UC06 | Track Outdated KB Article Expiry | Technical Author | Supporting System | Handles track outdated kb article expiry operations within system boundary | High |
| 7 | UC07 | Manage Knowledge Taxonomy Categories | Enterprise Support Staff | Supporting System | Handles manage knowledge taxonomy categories operations within system boundary | Medium |
| 8 | UC08 | Link KB Article to Support Ticket | End User Customer | Supporting System | Handles link kb article to support ticket operations within system boundary | High |
| 9 | UC09 | Configure Internal vs Public Access | Knowledge Base Manager | Supporting System | Handles configure internal vs public access operations within system boundary | High |
| 10 | UC10 | Monitor Popular Article View Trends | Technical Author | Supporting System | Handles monitor popular article view trends operations within system boundary | Medium |
| 11 | UC11 | Import Bulk Knowledge Documents | Enterprise Support Staff | Supporting System | Handles import bulk knowledge documents operations within system boundary | Medium |
| 12 | UC12 | Configure Machine Translation Support | End User Customer | Supporting System | Handles configure machine translation support operations within system boundary | Low |
| 13 | UC13 | Generate Deflection Efficiency Reports | Knowledge Base Manager | Supporting System | Handles generate deflection efficiency reports operations within system boundary | Medium |
| 14 | UC14 | Export Content Quality Audit Logs | Technical Author | Supporting System | Handles export content quality audit logs operations within system boundary | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Author Knowledge Base Article

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Author Knowledge Base Article |
| **Actor(s)** | Primary: Knowledge Base Manager |
| **Description** | Allows primary actors to configure and execute author knowledge base article within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Rate Article Helpfulness & Feedback

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Rate Article Helpfulness & Feedback |
| **Actor(s)** | Primary: Technical Author |
| **Description** | Executes rate article helpfulness & feedback with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Track Outdated KB Article Expiry

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Track Outdated KB Article Expiry |
| **Actor(s)** | Primary: Enterprise Support Staff |
| **Description** | Performs track outdated kb article expiry to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — Manage Knowledge Taxonomy Categories

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | Manage Knowledge Taxonomy Categories |
| **Actor(s)** | Primary: Enterprise Support Staff |
| **Description** | Manages manage knowledge taxonomy categories to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Monitor Popular Article View Trends

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Monitor Popular Article View Trends |
| **Actor(s)** | Primary: End User Customer |
| **Description** | Conducts monitor popular article view trends for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
