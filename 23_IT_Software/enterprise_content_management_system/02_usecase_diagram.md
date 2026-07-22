# Use Case Diagram — Enterprise Content Management System

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["ECM Document Manager"]
    actor_Primary2["Enterprise Employee"]
    actor_Primary3["Legal Compliance Specialist"]
    actor_Primary4["System Administrator"]

    subgraph SystemBoundary["Enterprise Content Management System"]
        UC01(["Upload Enterprise Document"])
        UC02(["Extract OCR Full-Text Index"])
        UC03(["Manage Document Version History"])
        UC04(["Authenticate User Session"])
        UC05(["Execute Full-Text Document Search"])
        UC06(["Apply Digital Signature to Document"])
        UC07(["Configure Document Retention Policies"])
        UC08(["Check-out & Check-in Document"])
        UC09(["Configure Access Permission ACLs"])
        UC10(["Route Document for Multi-level Approval"])
        UC11(["Watermark Confidential Documents"])
        UC12(["Archive Expired Legal Documents"])
        UC13(["Generate Content Utilization Summary"])
        UC14(["Export ISO 27001 Content Audit Logs"])
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
| 1 | ECM Document Manager | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | Enterprise Employee | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | Legal Compliance Specialist | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | System Administrator | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Upload Enterprise Document | ECM Document Manager | Supporting System | Handles upload enterprise document operations within system boundary | High |
| 2 | UC02 | Extract OCR Full-Text Index | Enterprise Employee | Supporting System | Handles extract ocr full-text index operations within system boundary | High |
| 3 | UC03 | Manage Document Version History | Legal Compliance Specialist | Supporting System | Handles manage document version history operations within system boundary | High |
| 4 | UC04 | Authenticate User Session | System Administrator | Supporting System | Handles authenticate user session operations within system boundary | High |
| 5 | UC05 | Execute Full-Text Document Search | ECM Document Manager | Supporting System | Handles execute full-text document search operations within system boundary | High |
| 6 | UC06 | Apply Digital Signature to Document | Enterprise Employee | Supporting System | Handles apply digital signature to document operations within system boundary | High |
| 7 | UC07 | Configure Document Retention Policies | Legal Compliance Specialist | Supporting System | Handles configure document retention policies operations within system boundary | High |
| 8 | UC08 | Check-out & Check-in Document | System Administrator | Supporting System | Handles check-out & check-in document operations within system boundary | Medium |
| 9 | UC09 | Configure Access Permission ACLs | ECM Document Manager | Supporting System | Handles configure access permission acls operations within system boundary | High |
| 10 | UC10 | Route Document for Multi-level Approval | Enterprise Employee | Supporting System | Handles route document for multi-level approval operations within system boundary | High |
| 11 | UC11 | Watermark Confidential Documents | Legal Compliance Specialist | Supporting System | Handles watermark confidential documents operations within system boundary | Medium |
| 12 | UC12 | Archive Expired Legal Documents | System Administrator | Supporting System | Handles archive expired legal documents operations within system boundary | Medium |
| 13 | UC13 | Generate Content Utilization Summary | ECM Document Manager | Supporting System | Handles generate content utilization summary operations within system boundary | Medium |
| 14 | UC14 | Export ISO 27001 Content Audit Logs | Enterprise Employee | Supporting System | Handles export iso 27001 content audit logs operations within system boundary | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Upload Enterprise Document

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Upload Enterprise Document |
| **Actor(s)** | Primary: ECM Document Manager |
| **Description** | Allows primary actors to configure and execute upload enterprise document within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Execute Full-Text Document Search

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Execute Full-Text Document Search |
| **Actor(s)** | Primary: Enterprise Employee |
| **Description** | Executes execute full-text document search with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Apply Digital Signature to Document

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Apply Digital Signature to Document |
| **Actor(s)** | Primary: Legal Compliance Specialist |
| **Description** | Performs apply digital signature to document to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — Configure Document Retention Policies

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | Configure Document Retention Policies |
| **Actor(s)** | Primary: Legal Compliance Specialist |
| **Description** | Manages configure document retention policies to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Route Document for Multi-level Approval

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Route Document for Multi-level Approval |
| **Actor(s)** | Primary: System Administrator |
| **Description** | Conducts route document for multi-level approval for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
