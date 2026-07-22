# Use Case Diagram — Software License Management System

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["Software License Manager"]
    actor_Primary2["Enterprise Employee"]
    actor_Primary3["Procurement Specialist"]
    actor_Primary4["IT Auditor"]

    subgraph SystemBoundary["Software License Management System"]
        UC01(["Register Software License Contract"])
        UC02(["Allocate License Seats to Employees"])
        UC03(["Scan Installed Software Endpoints"])
        UC04(["Authenticate User Session"])
        UC05(["Reclaim Unused License Seats"])
        UC06(["Audit License Over-Allocation & Compliance"])
        UC07(["Track Software License Renewal Dates"])
        UC08(["Calculate Software True-Up Costs"])
        UC09(["Manage License Pool Keys"])
        UC10(["Enforce SaaS Application SSO Access"])
        UC11(["Generate License Usage Trends"])
        UC12(["Manage Software Vendor Agreements"])
        UC13(["Export Software Compliance Audit Reports"])
        UC14(["Blacklist Unauthorized Software Installations"])
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
| 1 | Software License Manager | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | Enterprise Employee | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | Procurement Specialist | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | IT Auditor | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Register Software License Contract | Software License Manager | Supporting System | Handles register software license contract operations within system boundary | High |
| 2 | UC02 | Allocate License Seats to Employees | Enterprise Employee | Supporting System | Handles allocate license seats to employees operations within system boundary | High |
| 3 | UC03 | Scan Installed Software Endpoints | Procurement Specialist | Supporting System | Handles scan installed software endpoints operations within system boundary | High |
| 4 | UC04 | Authenticate User Session | IT Auditor | Supporting System | Handles authenticate user session operations within system boundary | High |
| 5 | UC05 | Reclaim Unused License Seats | Software License Manager | Supporting System | Handles reclaim unused license seats operations within system boundary | High |
| 6 | UC06 | Audit License Over-Allocation & Compliance | Enterprise Employee | Supporting System | Handles audit license over-allocation & compliance operations within system boundary | High |
| 7 | UC07 | Track Software License Renewal Dates | Procurement Specialist | Supporting System | Handles track software license renewal dates operations within system boundary | Medium |
| 8 | UC08 | Calculate Software True-Up Costs | IT Auditor | Supporting System | Handles calculate software true-up costs operations within system boundary | Medium |
| 9 | UC09 | Manage License Pool Keys | Software License Manager | Supporting System | Handles manage license pool keys operations within system boundary | Medium |
| 10 | UC10 | Enforce SaaS Application SSO Access | Enterprise Employee | Supporting System | Handles enforce saas application sso access operations within system boundary | High |
| 11 | UC11 | Generate License Usage Trends | Procurement Specialist | Supporting System | Handles generate license usage trends operations within system boundary | Medium |
| 12 | UC12 | Manage Software Vendor Agreements | IT Auditor | Supporting System | Handles manage software vendor agreements operations within system boundary | Medium |
| 13 | UC13 | Export Software Compliance Audit Reports | Software License Manager | Supporting System | Handles export software compliance audit reports operations within system boundary | Low |
| 14 | UC14 | Blacklist Unauthorized Software Installations | Enterprise Employee | Supporting System | Handles blacklist unauthorized software installations operations within system boundary | High |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Register Software License Contract

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Register Software License Contract |
| **Actor(s)** | Primary: Software License Manager |
| **Description** | Allows primary actors to configure and execute register software license contract within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Reclaim Unused License Seats

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Reclaim Unused License Seats |
| **Actor(s)** | Primary: Enterprise Employee |
| **Description** | Executes reclaim unused license seats with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Audit License Over-Allocation & Compliance

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Audit License Over-Allocation & Compliance |
| **Actor(s)** | Primary: Procurement Specialist |
| **Description** | Performs audit license over-allocation & compliance to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — Track Software License Renewal Dates

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | Track Software License Renewal Dates |
| **Actor(s)** | Primary: Procurement Specialist |
| **Description** | Manages track software license renewal dates to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Enforce SaaS Application SSO Access

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Enforce SaaS Application SSO Access |
| **Actor(s)** | Primary: IT Auditor |
| **Description** | Conducts enforce saas application sso access for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
