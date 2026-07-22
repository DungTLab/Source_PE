# Use Case Diagram — Data Warehouse Management System

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["Data Warehouse Administrator"]
    actor_Primary2["Data Engineer"]
    actor_Primary3["BI Analyst"]
    actor_Primary4["Security Compliance Officer"]

    subgraph SystemBoundary["Data Warehouse Management System"]
        UC01(["Configure DW Cluster & Warehouse"])
        UC02(["Manage Star Schema Data Marts"])
        UC03(["Optimize Columnar Index Partitioning"])
        UC04(["Authenticate DW Admin Session"])
        UC05(["Ingest Batch ETL Pipeline Datasets"])
        UC06(["Monitor DW Query Compute Credits"])
        UC07(["Configure Role-Based Data Access Policies"])
        UC08(["Analyze Slow Query Concurrency Bottlenecks"])
        UC09(["Execute Time-Travel Data Point Restore"])
        UC10(["Manage Data Lake Storage Integration"])
        UC11(["Schedule Automated Table Vacuum & Compress"])
        UC12(["Configure Multi-Region Data Replication"])
        UC13(["Generate Credit Usage & Spend Forecasts"])
        UC14(["Export SOC2 Data Warehouse Audit Logs"])
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
| 1 | Data Warehouse Administrator | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | Data Engineer | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | BI Analyst | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | Security Compliance Officer | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Configure DW Cluster & Warehouse | Data Warehouse Administrator | Supporting System | Handles configure dw cluster & warehouse operations within system boundary | High |
| 2 | UC02 | Manage Star Schema Data Marts | Data Engineer | Supporting System | Handles manage star schema data marts operations within system boundary | High |
| 3 | UC03 | Optimize Columnar Index Partitioning | BI Analyst | Supporting System | Handles optimize columnar index partitioning operations within system boundary | High |
| 4 | UC04 | Authenticate DW Admin Session | Security Compliance Officer | Supporting System | Handles authenticate dw admin session operations within system boundary | High |
| 5 | UC05 | Ingest Batch ETL Pipeline Datasets | Data Warehouse Administrator | Supporting System | Handles ingest batch etl pipeline datasets operations within system boundary | High |
| 6 | UC06 | Monitor DW Query Compute Credits | Data Engineer | Supporting System | Handles monitor dw query compute credits operations within system boundary | High |
| 7 | UC07 | Configure Role-Based Data Access Policies | BI Analyst | Supporting System | Handles configure role-based data access policies operations within system boundary | High |
| 8 | UC08 | Analyze Slow Query Concurrency Bottlenecks | Security Compliance Officer | Supporting System | Handles analyze slow query concurrency bottlenecks operations within system boundary | Medium |
| 9 | UC09 | Execute Time-Travel Data Point Restore | Data Warehouse Administrator | Supporting System | Handles execute time-travel data point restore operations within system boundary | High |
| 10 | UC10 | Manage Data Lake Storage Integration | Data Engineer | Supporting System | Handles manage data lake storage integration operations within system boundary | Medium |
| 11 | UC11 | Schedule Automated Table Vacuum & Compress | BI Analyst | Supporting System | Handles schedule automated table vacuum & compress operations within system boundary | Medium |
| 12 | UC12 | Configure Multi-Region Data Replication | Security Compliance Officer | Supporting System | Handles configure multi-region data replication operations within system boundary | High |
| 13 | UC13 | Generate Credit Usage & Spend Forecasts | Data Warehouse Administrator | Supporting System | Handles generate credit usage & spend forecasts operations within system boundary | Medium |
| 14 | UC14 | Export SOC2 Data Warehouse Audit Logs | Data Engineer | Supporting System | Handles export soc2 data warehouse audit logs operations within system boundary | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Configure DW Cluster & Warehouse

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Configure DW Cluster & Warehouse |
| **Actor(s)** | Primary: Data Warehouse Administrator |
| **Description** | Allows primary actors to configure and execute configure dw cluster & warehouse within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Ingest Batch ETL Pipeline Datasets

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Ingest Batch ETL Pipeline Datasets |
| **Actor(s)** | Primary: Data Engineer |
| **Description** | Executes ingest batch etl pipeline datasets with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Monitor DW Query Compute Credits

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Monitor DW Query Compute Credits |
| **Actor(s)** | Primary: BI Analyst |
| **Description** | Performs monitor dw query compute credits to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — Configure Role-Based Data Access Policies

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | Configure Role-Based Data Access Policies |
| **Actor(s)** | Primary: BI Analyst |
| **Description** | Manages configure role-based data access policies to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Manage Data Lake Storage Integration

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Manage Data Lake Storage Integration |
| **Actor(s)** | Primary: Security Compliance Officer |
| **Description** | Conducts manage data lake storage integration for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
