# Use Case Diagram — AI & Machine Learning Model Management System

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["MLOps Engineer"]
    actor_Primary2["Data Scientist"]
    actor_Primary3["AI Product Owner"]
    actor_Primary4["Security Auditor"]

    subgraph SystemBoundary["AI & Machine Learning Model Management System"]
        UC01(["Register AI ML Model Version"])
        UC02(["Track Training Dataset Lineage"])
        UC03(["Deploy Model to Inference Endpoint"])
        UC04(["Authenticate MLOps Session"])
        UC05(["Monitor Real-time Model Data Drift"])
        UC06(["Evaluate Model Accuracy & F1 Score"])
        UC07(["Rollback to Previous Model Version"])
        UC08(["Manage Feature Store Variables"])
        UC09(["Enforce AI Ethics & Bias Guardrails"])
        UC10(["Trigger Automated Retraining Pipeline"])
        UC11(["Monitor Inference API Latency & RPS"])
        UC12(["Configure Model A B Testing Split"])
        UC13(["Generate MLOps Resource Usage Metrics"])
        UC14(["Export AI Model Compliance Governance Logs"])
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
| 1 | MLOps Engineer | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | Data Scientist | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | AI Product Owner | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | Security Auditor | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Register AI ML Model Version | MLOps Engineer | Supporting System | Handles register ai ml model version operations within system boundary | High |
| 2 | UC02 | Track Training Dataset Lineage | Data Scientist | Supporting System | Handles track training dataset lineage operations within system boundary | High |
| 3 | UC03 | Deploy Model to Inference Endpoint | AI Product Owner | Supporting System | Handles deploy model to inference endpoint operations within system boundary | High |
| 4 | UC04 | Authenticate MLOps Session | Security Auditor | Supporting System | Handles authenticate mlops session operations within system boundary | High |
| 5 | UC05 | Monitor Real-time Model Data Drift | MLOps Engineer | Supporting System | Handles monitor real-time model data drift operations within system boundary | High |
| 6 | UC06 | Evaluate Model Accuracy & F1 Score | Data Scientist | Supporting System | Handles evaluate model accuracy & f1 score operations within system boundary | High |
| 7 | UC07 | Rollback to Previous Model Version | AI Product Owner | Supporting System | Handles rollback to previous model version operations within system boundary | High |
| 8 | UC08 | Manage Feature Store Variables | Security Auditor | Supporting System | Handles manage feature store variables operations within system boundary | Medium |
| 9 | UC09 | Enforce AI Ethics & Bias Guardrails | MLOps Engineer | Supporting System | Handles enforce ai ethics & bias guardrails operations within system boundary | High |
| 10 | UC10 | Trigger Automated Retraining Pipeline | Data Scientist | Supporting System | Handles trigger automated retraining pipeline operations within system boundary | High |
| 11 | UC11 | Monitor Inference API Latency & RPS | AI Product Owner | Supporting System | Handles monitor inference api latency & rps operations within system boundary | Medium |
| 12 | UC12 | Configure Model A B Testing Split | Security Auditor | Supporting System | Handles configure model a b testing split operations within system boundary | Medium |
| 13 | UC13 | Generate MLOps Resource Usage Metrics | MLOps Engineer | Supporting System | Handles generate mlops resource usage metrics operations within system boundary | Medium |
| 14 | UC14 | Export AI Model Compliance Governance Logs | Data Scientist | Supporting System | Handles export ai model compliance governance logs operations within system boundary | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Register AI ML Model Version

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Register AI ML Model Version |
| **Actor(s)** | Primary: MLOps Engineer |
| **Description** | Allows primary actors to configure and execute register ai ml model version within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Monitor Real-time Model Data Drift

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Monitor Real-time Model Data Drift |
| **Actor(s)** | Primary: Data Scientist |
| **Description** | Executes monitor real-time model data drift with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Evaluate Model Accuracy & F1 Score

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Evaluate Model Accuracy & F1 Score |
| **Actor(s)** | Primary: AI Product Owner |
| **Description** | Performs evaluate model accuracy & f1 score to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — Rollback to Previous Model Version

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | Rollback to Previous Model Version |
| **Actor(s)** | Primary: AI Product Owner |
| **Description** | Manages rollback to previous model version to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Trigger Automated Retraining Pipeline

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Trigger Automated Retraining Pipeline |
| **Actor(s)** | Primary: Security Auditor |
| **Description** | Conducts trigger automated retraining pipeline for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
