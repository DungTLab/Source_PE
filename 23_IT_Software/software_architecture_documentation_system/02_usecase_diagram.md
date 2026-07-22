# Use Case Diagram — Software Architecture Documentation System

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["Enterprise Architect"]
    actor_Primary2["Software Architect"]
    actor_Primary3["Lead Developer"]
    actor_Primary4["Security Auditor"]

    subgraph SystemBoundary["Software Architecture Documentation System"]
        UC01(["Author C4 Model Architecture Diagram"])
        UC02(["Record Architecture Decision Record ADR"])
        UC03(["Publish Interactive Architecture Portal"])
        UC04(["Authenticate Architect Session"])
        UC05(["Execute Architecture Search & Query"])
        UC06(["Review Architecture Compliance PR"])
        UC07(["Map System Technology Stack Catalog"])
        UC08(["Version Control Architecture Code"])
        UC09(["Audit Architectural Tech Debt Risks"])
        UC10(["Export Architecture Diagram to PNG SVG"])
        UC11(["Link Architecture Components to Repos"])
        UC12(["Configure Diagram Styling Templates"])
        UC13(["Generate Architecture Inventory Reports"])
        UC14(["Export Architecture Compliance Audit Trail"])
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
| 1 | Enterprise Architect | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | Software Architect | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | Lead Developer | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | Security Auditor | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Author C4 Model Architecture Diagram | Enterprise Architect | Supporting System | Handles author c4 model architecture diagram operations within system boundary | High |
| 2 | UC02 | Record Architecture Decision Record ADR | Software Architect | Supporting System | Handles record architecture decision record adr operations within system boundary | High |
| 3 | UC03 | Publish Interactive Architecture Portal | Lead Developer | Supporting System | Handles publish interactive architecture portal operations within system boundary | High |
| 4 | UC04 | Authenticate Architect Session | Security Auditor | Supporting System | Handles authenticate architect session operations within system boundary | High |
| 5 | UC05 | Execute Architecture Search & Query | Enterprise Architect | Supporting System | Handles execute architecture search & query operations within system boundary | High |
| 6 | UC06 | Review Architecture Compliance PR | Software Architect | Supporting System | Handles review architecture compliance pr operations within system boundary | High |
| 7 | UC07 | Map System Technology Stack Catalog | Lead Developer | Supporting System | Handles map system technology stack catalog operations within system boundary | Medium |
| 8 | UC08 | Version Control Architecture Code | Security Auditor | Supporting System | Handles version control architecture code operations within system boundary | High |
| 9 | UC09 | Audit Architectural Tech Debt Risks | Enterprise Architect | Supporting System | Handles audit architectural tech debt risks operations within system boundary | Medium |
| 10 | UC10 | Export Architecture Diagram to PNG SVG | Software Architect | Supporting System | Handles export architecture diagram to png svg operations within system boundary | Medium |
| 11 | UC11 | Link Architecture Components to Repos | Lead Developer | Supporting System | Handles link architecture components to repos operations within system boundary | Medium |
| 12 | UC12 | Configure Diagram Styling Templates | Security Auditor | Supporting System | Handles configure diagram styling templates operations within system boundary | Low |
| 13 | UC13 | Generate Architecture Inventory Reports | Enterprise Architect | Supporting System | Handles generate architecture inventory reports operations within system boundary | Medium |
| 14 | UC14 | Export Architecture Compliance Audit Trail | Software Architect | Supporting System | Handles export architecture compliance audit trail operations within system boundary | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Author C4 Model Architecture Diagram

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Author C4 Model Architecture Diagram |
| **Actor(s)** | Primary: Enterprise Architect |
| **Description** | Allows primary actors to configure and execute author c4 model architecture diagram within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Execute Architecture Search & Query

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Execute Architecture Search & Query |
| **Actor(s)** | Primary: Software Architect |
| **Description** | Executes execute architecture search & query with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Review Architecture Compliance PR

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Review Architecture Compliance PR |
| **Actor(s)** | Primary: Lead Developer |
| **Description** | Performs review architecture compliance pr to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — Map System Technology Stack Catalog

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | Map System Technology Stack Catalog |
| **Actor(s)** | Primary: Lead Developer |
| **Description** | Manages map system technology stack catalog to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Export Architecture Diagram to PNG SVG

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Export Architecture Diagram to PNG SVG |
| **Actor(s)** | Primary: Security Auditor |
| **Description** | Conducts export architecture diagram to png svg for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
