# Use Case Diagram — Data Quality Management System

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["Data Quality Analyst"]
    actor_Primary2["Data Steward"]
    actor_Primary3["Data Engineer"]
    actor_Primary4["Compliance Officer"]

    subgraph SystemBoundary["Data Quality Management System"]
        UC01(["Configure Data Quality Rule Test"])
        UC02(["Execute Automated Quality Profiling"])
        UC03(["Detect Duplicate & Anomaly Records"])
        UC04(["Authenticate DQ Analyst Session"])
        UC05(["Execute Data Cleansing & Standardization"])
        UC06(["Calculate Data Completeness Accuracy Score"])
        UC07(["Manage Quarantine Table for Invalid Data"])
        UC08(["Trigger DQ Alert on Threshold Breach"])
        UC09(["Map DQ Metrics to Data Catalog Assets"])
        UC10(["Review Manual Data Correction Workflow"])
        UC11(["Configure Custom Regex Matching Rules"])
        UC12(["Schedule Periodic Quality Scans"])
        UC13(["Generate Executive Data Quality Index"])
        UC14(["Export Data Compliance Audit Reports"])
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
| 1 | Data Quality Analyst | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | Data Steward | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | Data Engineer | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | Compliance Officer | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Configure Data Quality Rule Test | Data Quality Analyst | Supporting System | Handles configure data quality rule test operations within system boundary | High |
| 2 | UC02 | Execute Automated Quality Profiling | Data Steward | Supporting System | Handles execute automated quality profiling operations within system boundary | High |
| 3 | UC03 | Detect Duplicate & Anomaly Records | Data Engineer | Supporting System | Handles detect duplicate & anomaly records operations within system boundary | High |
| 4 | UC04 | Authenticate DQ Analyst Session | Compliance Officer | Supporting System | Handles authenticate dq analyst session operations within system boundary | High |
| 5 | UC05 | Execute Data Cleansing & Standardization | Data Quality Analyst | Supporting System | Handles execute data cleansing & standardization operations within system boundary | High |
| 6 | UC06 | Calculate Data Completeness Accuracy Score | Data Steward | Supporting System | Handles calculate data completeness accuracy score operations within system boundary | High |
| 7 | UC07 | Manage Quarantine Table for Invalid Data | Data Engineer | Supporting System | Handles manage quarantine table for invalid data operations within system boundary | High |
| 8 | UC08 | Trigger DQ Alert on Threshold Breach | Compliance Officer | Supporting System | Handles trigger dq alert on threshold breach operations within system boundary | High |
| 9 | UC09 | Map DQ Metrics to Data Catalog Assets | Data Quality Analyst | Supporting System | Handles map dq metrics to data catalog assets operations within system boundary | Medium |
| 10 | UC10 | Review Manual Data Correction Workflow | Data Steward | Supporting System | Handles review manual data correction workflow operations within system boundary | Medium |
| 11 | UC11 | Configure Custom Regex Matching Rules | Data Engineer | Supporting System | Handles configure custom regex matching rules operations within system boundary | Medium |
| 12 | UC12 | Schedule Periodic Quality Scans | Compliance Officer | Supporting System | Handles schedule periodic quality scans operations within system boundary | Medium |
| 13 | UC13 | Generate Executive Data Quality Index | Data Quality Analyst | Supporting System | Handles generate executive data quality index operations within system boundary | Medium |
| 14 | UC14 | Export Data Compliance Audit Reports | Data Steward | Supporting System | Handles export data compliance audit reports operations within system boundary | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Configure Data Quality Rule Test

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Configure Data Quality Rule Test |
| **Actor(s)** | Primary: Data Quality Analyst |
| **Description** | Allows primary actors to configure and execute configure data quality rule test within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Execute Data Cleansing & Standardization

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Execute Data Cleansing & Standardization |
| **Actor(s)** | Primary: Data Steward |
| **Description** | Executes execute data cleansing & standardization with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Calculate Data Completeness Accuracy Score

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Calculate Data Completeness Accuracy Score |
| **Actor(s)** | Primary: Data Engineer |
| **Description** | Performs calculate data completeness accuracy score to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — Manage Quarantine Table for Invalid Data

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | Manage Quarantine Table for Invalid Data |
| **Actor(s)** | Primary: Data Engineer |
| **Description** | Manages manage quarantine table for invalid data to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Review Manual Data Correction Workflow

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Review Manual Data Correction Workflow |
| **Actor(s)** | Primary: Compliance Officer |
| **Description** | Conducts review manual data correction workflow for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
