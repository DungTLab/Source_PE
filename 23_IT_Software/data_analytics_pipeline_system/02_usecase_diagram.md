# Use Case Diagram — Data Analytics Pipeline System

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["Data Pipeline Engineer"]
    actor_Primary2["Data Scientist"]
    actor_Primary3["BI Developer"]
    actor_Primary4["Security Auditor"]

    subgraph SystemBoundary["Data Analytics Pipeline System"]
        UC01(["Author Data Pipeline DAG Workflow"])
        UC02(["Schedule Batch ETL Data Ingestion"])
        UC03(["Ingest Real-time Stream Analytics Data"])
        UC04(["Authenticate Data Engineer Session"])
        UC05(["Monitor Pipeline Task Execution Status"])
        UC06(["Execute Automated Pipeline Task Retry"])
        UC07(["Validate Ingested Data Quality Rules"])
        UC08(["Manage Spark Cluster Compute Resources"])
        UC09(["Trigger Backfill Data Pipeline Run"])
        UC10(["Configure Pipeline Alert Notifications"])
        UC11(["Manage Secret Keys & Connections Vault"])
        UC12(["Configure Pipeline Operator Extensions"])
        UC13(["Generate Pipeline Duration & SLA Metrics"])
        UC14(["Export Pipeline Security Audit Logs"])
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
| 1 | Data Pipeline Engineer | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | Data Scientist | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | BI Developer | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | Security Auditor | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Author Data Pipeline DAG Workflow | Data Pipeline Engineer | Supporting System | Handles author data pipeline dag workflow operations within system boundary | High |
| 2 | UC02 | Schedule Batch ETL Data Ingestion | Data Scientist | Supporting System | Handles schedule batch etl data ingestion operations within system boundary | High |
| 3 | UC03 | Ingest Real-time Stream Analytics Data | BI Developer | Supporting System | Handles ingest real-time stream analytics data operations within system boundary | High |
| 4 | UC04 | Authenticate Data Engineer Session | Security Auditor | Supporting System | Handles authenticate data engineer session operations within system boundary | High |
| 5 | UC05 | Monitor Pipeline Task Execution Status | Data Pipeline Engineer | Supporting System | Handles monitor pipeline task execution status operations within system boundary | High |
| 6 | UC06 | Execute Automated Pipeline Task Retry | Data Scientist | Supporting System | Handles execute automated pipeline task retry operations within system boundary | High |
| 7 | UC07 | Validate Ingested Data Quality Rules | BI Developer | Supporting System | Handles validate ingested data quality rules operations within system boundary | High |
| 8 | UC08 | Manage Spark Cluster Compute Resources | Security Auditor | Supporting System | Handles manage spark cluster compute resources operations within system boundary | Medium |
| 9 | UC09 | Trigger Backfill Data Pipeline Run | Data Pipeline Engineer | Supporting System | Handles trigger backfill data pipeline run operations within system boundary | Medium |
| 10 | UC10 | Configure Pipeline Alert Notifications | Data Scientist | Supporting System | Handles configure pipeline alert notifications operations within system boundary | High |
| 11 | UC11 | Manage Secret Keys & Connections Vault | BI Developer | Supporting System | Handles manage secret keys & connections vault operations within system boundary | High |
| 12 | UC12 | Configure Pipeline Operator Extensions | Security Auditor | Supporting System | Handles configure pipeline operator extensions operations within system boundary | Low |
| 13 | UC13 | Generate Pipeline Duration & SLA Metrics | Data Pipeline Engineer | Supporting System | Handles generate pipeline duration & sla metrics operations within system boundary | Medium |
| 14 | UC14 | Export Pipeline Security Audit Logs | Data Scientist | Supporting System | Handles export pipeline security audit logs operations within system boundary | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Author Data Pipeline DAG Workflow

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Author Data Pipeline DAG Workflow |
| **Actor(s)** | Primary: Data Pipeline Engineer |
| **Description** | Allows primary actors to configure and execute author data pipeline dag workflow within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Monitor Pipeline Task Execution Status

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Monitor Pipeline Task Execution Status |
| **Actor(s)** | Primary: Data Scientist |
| **Description** | Executes monitor pipeline task execution status with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Execute Automated Pipeline Task Retry

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Execute Automated Pipeline Task Retry |
| **Actor(s)** | Primary: BI Developer |
| **Description** | Performs execute automated pipeline task retry to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — Validate Ingested Data Quality Rules

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | Validate Ingested Data Quality Rules |
| **Actor(s)** | Primary: BI Developer |
| **Description** | Manages validate ingested data quality rules to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Configure Pipeline Alert Notifications

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Configure Pipeline Alert Notifications |
| **Actor(s)** | Primary: Security Auditor |
| **Description** | Conducts configure pipeline alert notifications for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
