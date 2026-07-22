# Use Case Diagram — Low-Code / No-Code Development Platform

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["Citizen Developer"]
    actor_Primary2["Enterprise IT Admin"]
    actor_Primary3["Business End User"]
    actor_Primary4["Security Auditor"]

    subgraph SystemBoundary["Low-Code / No-Code Development Platform"]
        UC01(["Design Drag-and-Drop Drag UI Form"])
        UC02(["Connect REST API Data Source"])
        UC03(["Publish Low-Code Application"])
        UC04(["Authenticate Citizen Developer Session"])
        UC05(["Configure Visual Workflow Logic"])
        UC06(["Manage Application Role Permissions"])
        UC07(["Export Application Source Package"])
        UC08(["Test App in Sandbox Environment"])
        UC09(["Audit Citizen Developer Apps"])
        UC10(["Configure Database Entity Binding"])
        UC11(["Build Mobile Responsive Layout"])
        UC12(["Manage App Version Rollback"])
        UC13(["Track Application Active Users Metrics"])
        UC14(["Export Platform Security Audit Logs"])
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
| 1 | Citizen Developer | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | Enterprise IT Admin | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | Business End User | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | Security Auditor | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Design Drag-and-Drop Drag UI Form | Citizen Developer | Supporting System | Handles design drag-and-drop drag ui form operations within system boundary | High |
| 2 | UC02 | Connect REST API Data Source | Enterprise IT Admin | Supporting System | Handles connect rest api data source operations within system boundary | High |
| 3 | UC03 | Publish Low-Code Application | Business End User | Supporting System | Handles publish low-code application operations within system boundary | High |
| 4 | UC04 | Authenticate Citizen Developer Session | Security Auditor | Supporting System | Handles authenticate citizen developer session operations within system boundary | High |
| 5 | UC05 | Configure Visual Workflow Logic | Citizen Developer | Supporting System | Handles configure visual workflow logic operations within system boundary | High |
| 6 | UC06 | Manage Application Role Permissions | Enterprise IT Admin | Supporting System | Handles manage application role permissions operations within system boundary | High |
| 7 | UC07 | Export Application Source Package | Business End User | Supporting System | Handles export application source package operations within system boundary | Medium |
| 8 | UC08 | Test App in Sandbox Environment | Security Auditor | Supporting System | Handles test app in sandbox environment operations within system boundary | High |
| 9 | UC09 | Audit Citizen Developer Apps | Citizen Developer | Supporting System | Handles audit citizen developer apps operations within system boundary | High |
| 10 | UC10 | Configure Database Entity Binding | Enterprise IT Admin | Supporting System | Handles configure database entity binding operations within system boundary | High |
| 11 | UC11 | Build Mobile Responsive Layout | Business End User | Supporting System | Handles build mobile responsive layout operations within system boundary | Medium |
| 12 | UC12 | Manage App Version Rollback | Security Auditor | Supporting System | Handles manage app version rollback operations within system boundary | Medium |
| 13 | UC13 | Track Application Active Users Metrics | Citizen Developer | Supporting System | Handles track application active users metrics operations within system boundary | Medium |
| 14 | UC14 | Export Platform Security Audit Logs | Enterprise IT Admin | Supporting System | Handles export platform security audit logs operations within system boundary | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Design Drag-and-Drop Drag UI Form

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Design Drag-and-Drop Drag UI Form |
| **Actor(s)** | Primary: Citizen Developer |
| **Description** | Allows primary actors to configure and execute design drag-and-drop drag ui form within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Configure Visual Workflow Logic

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Configure Visual Workflow Logic |
| **Actor(s)** | Primary: Enterprise IT Admin |
| **Description** | Executes configure visual workflow logic with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Manage Application Role Permissions

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Manage Application Role Permissions |
| **Actor(s)** | Primary: Business End User |
| **Description** | Performs manage application role permissions to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — Export Application Source Package

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | Export Application Source Package |
| **Actor(s)** | Primary: Business End User |
| **Description** | Manages export application source package to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Configure Database Entity Binding

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Configure Database Entity Binding |
| **Actor(s)** | Primary: Security Auditor |
| **Description** | Conducts configure database entity binding for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
