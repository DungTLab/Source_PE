# Use Case Diagram — Business Intelligence & Analytics Platform

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["BI Analytics Manager"]
    actor_Primary2["Data Analyst / Scientist"]
    actor_Primary3["Executive Decision Maker"]
    actor_Primary4["Database Administrator"]

    subgraph SystemBoundary["Business Intelligence & Analytics Platform"]
        UC01(["Create Interactive BI Dashboard"])
        UC02(["Connect Data Warehouse Source"])
        UC03(["Design Custom Analytical Metrics"])
        UC04(["Authenticate Analyst Session"])
        UC05(["Execute Ad-Hoc SQL Data Query"])
        UC06(["Schedule Automated Email Report Delivery"])
        UC07(["Configure Row-Level Security RLS"])
        UC08(["Export Dashboard Data to PDF Excel"])
        UC09(["Build Predictive Data Visualizations"])
        UC10(["Manage Shared KPI Workspaces"])
        UC11(["Monitor Dashboard Query Latency"])
        UC12(["Configure In-Memory Data Model Cache"])
        UC13(["Track User Dashboard Consumption Rates"])
        UC14(["Export Data Access Audit Logs"])
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
| 1 | BI Analytics Manager | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | Data Analyst / Scientist | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | Executive Decision Maker | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | Database Administrator | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Create Interactive BI Dashboard | BI Analytics Manager | Supporting System | Handles create interactive bi dashboard operations within system boundary | High |
| 2 | UC02 | Connect Data Warehouse Source | Data Analyst / Scientist | Supporting System | Handles connect data warehouse source operations within system boundary | High |
| 3 | UC03 | Design Custom Analytical Metrics | Executive Decision Maker | Supporting System | Handles design custom analytical metrics operations within system boundary | High |
| 4 | UC04 | Authenticate Analyst Session | Database Administrator | Supporting System | Handles authenticate analyst session operations within system boundary | High |
| 5 | UC05 | Execute Ad-Hoc SQL Data Query | BI Analytics Manager | Supporting System | Handles execute ad-hoc sql data query operations within system boundary | High |
| 6 | UC06 | Schedule Automated Email Report Delivery | Data Analyst / Scientist | Supporting System | Handles schedule automated email report delivery operations within system boundary | High |
| 7 | UC07 | Configure Row-Level Security RLS | Executive Decision Maker | Supporting System | Handles configure row-level security rls operations within system boundary | High |
| 8 | UC08 | Export Dashboard Data to PDF Excel | Database Administrator | Supporting System | Handles export dashboard data to pdf excel operations within system boundary | Medium |
| 9 | UC09 | Build Predictive Data Visualizations | BI Analytics Manager | Supporting System | Handles build predictive data visualizations operations within system boundary | Medium |
| 10 | UC10 | Manage Shared KPI Workspaces | Data Analyst / Scientist | Supporting System | Handles manage shared kpi workspaces operations within system boundary | High |
| 11 | UC11 | Monitor Dashboard Query Latency | Executive Decision Maker | Supporting System | Handles monitor dashboard query latency operations within system boundary | Medium |
| 12 | UC12 | Configure In-Memory Data Model Cache | Database Administrator | Supporting System | Handles configure in-memory data model cache operations within system boundary | Medium |
| 13 | UC13 | Track User Dashboard Consumption Rates | BI Analytics Manager | Supporting System | Handles track user dashboard consumption rates operations within system boundary | Medium |
| 14 | UC14 | Export Data Access Audit Logs | Data Analyst / Scientist | Supporting System | Handles export data access audit logs operations within system boundary | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Create Interactive BI Dashboard

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Create Interactive BI Dashboard |
| **Actor(s)** | Primary: BI Analytics Manager |
| **Description** | Allows primary actors to configure and execute create interactive bi dashboard within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Execute Ad-Hoc SQL Data Query

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Execute Ad-Hoc SQL Data Query |
| **Actor(s)** | Primary: Data Analyst / Scientist |
| **Description** | Executes execute ad-hoc sql data query with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Schedule Automated Email Report Delivery

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Schedule Automated Email Report Delivery |
| **Actor(s)** | Primary: Executive Decision Maker |
| **Description** | Performs schedule automated email report delivery to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — Configure Row-Level Security RLS

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | Configure Row-Level Security RLS |
| **Actor(s)** | Primary: Executive Decision Maker |
| **Description** | Manages configure row-level security rls to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Manage Shared KPI Workspaces

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Manage Shared KPI Workspaces |
| **Actor(s)** | Primary: Database Administrator |
| **Description** | Conducts manage shared kpi workspaces for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
