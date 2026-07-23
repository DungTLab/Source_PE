# Use Case Diagram — Building Permit & Approval System

## Mermaid Code

```mermaid
flowchart LR
    actor_1["Project Manager"]
    actor_2["Site Engineer"]
    actor_3["Specialized Contractor"]
    actor_4["Quality / Safety Inspector"]
    actor_5["Client / Owner Representative"]
    actor_6["Enterprise ERP System"]
    actor_7["Regulatory Building Authority"]

    subgraph SystemBoundary["Building Permit & Approval System"]
        UC01(["Authenticate Building User"])
        UC02(["Initialize Building Profile"])
        UC03(["Log Permit Applications Data"])
        UC04(["Process  Municipal Inspections Workflow"])
        UC05(["Evaluate  Zoning Review Compliance"])
        UC06(["Manage  Permit Issuance Records"])
        UC07(["Perform Real-time Analytics"])
        UC08(["Generate Regulatory Audit Package"])
        UC09(["Approve Status Sign-off"])
        UC10(["Version System Documentation"])
        UC11(["Trigger Automated Exception Alerts"])
        UC12(["Export Executive Progress Reports"])
    end

    actor_1 --> UC01
    actor_1 --> UC02
    actor_2 --> UC03
    actor_2 --> UC04
    actor_4 --> UC05
    actor_3 --> UC06
    actor_1 --> UC07
    actor_4 --> UC08
    actor_5 --> UC09
    actor_2 --> UC10
    actor_6 --> UC11
    actor_1 --> UC12

    UC02 -.->|"<<include>>"| UC01
    UC04 -.->|"<<include>>"| UC01
    UC05 -.->|"<<extend>>"| UC03
    UC08 -.->|"<<extend>>"| UC05
```

## Actor Table | Bang Actor

| # | Actor | Actor Type | Role Description | Related Use Cases |
|---|-------|------------|------------------|-------------------|
| 1 | Project Manager | Primary | Responsible for execution and monitoring within Building Permit & Approval System | UC01, UC02, UC07, UC12 |
| 2 | Site Engineer | Primary | Responsible for execution and monitoring within Building Permit & Approval System | UC03, UC04, UC10 |
| 3 | Specialized Contractor | Primary | Responsible for execution and monitoring within Building Permit & Approval System | UC06 |
| 4 | Quality / Safety Inspector | Primary | Responsible for execution and monitoring within Building Permit & Approval System | UC05, UC08 |
| 5 | Client / Owner Representative | Primary | Responsible for execution and monitoring within Building Permit & Approval System | UC09 |
| 6 | Enterprise ERP System | Supporting | Responsible for execution and monitoring within Building Permit & Approval System | UC11 |
| 7 | Regulatory Building Authority | Regulatory | Responsible for execution and monitoring within Building Permit & Approval System | UC01 |

## Use Case Table | Bang Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Authenticate Building User | Project Manager | None | Authenticates system user for Building Permit & Approval System | High |
| 2 | UC02 | Initialize Building Profile | Project Manager | Client / Owner Representative | Sets up core project baseline and parameters for Building Permit & Approval System | High |
| 3 | UC03 | Log Permit Applications Data | Site Engineer | Specialized Contractor | Enters operational field records for Permit Applications | High |
| 4 | UC04 | Process  Municipal Inspections Workflow | Site Engineer | Quality / Safety Inspector | Executes standard process flow for  Municipal Inspections | High |
| 5 | UC05 | Evaluate  Zoning Review Compliance | Quality / Safety Inspector | Project Manager | Audits field activities against  Zoning Review standards | High |
| 6 | UC06 | Manage  Permit Issuance Records | Specialized Contractor | Site Engineer | Maintains documentation and certificates for  Permit Issuance | High |
| 7 | UC07 | Perform Real-time Analytics | Project Manager | Enterprise ERP System | Computes system KPIs, variances, and status trends | Medium |
| 8 | UC08 | Generate Regulatory Audit Package | Quality / Safety Inspector | Regulatory Building Authority | Compiles required compliance documentation for official authority | High |
| 9 | UC09 | Approve Status Sign-off | Client / Owner Representative | Project Manager | Grants formal approval for project milestone completion | High |
| 10 | UC10 | Version System Documentation | Site Engineer | Project Manager | Tracks historical document revisions and sign-off logs | Medium |
| 11 | UC11 | Trigger Automated Exception Alerts | Enterprise ERP System | Project Manager | Issues system warnings upon threshold breaches | High |
| 12 | UC12 | Export Executive Progress Reports | Project Manager | Client / Owner Representative | Generates summary dashboard analytics and exportable reports | High |

## Use Case Specification | Dac ta Use Case

---

### UC02 — Initialize Building Profile

| Field | Detail |
|-------|--------|
| **UC ID** | UC02 |
| **Use Case Name** | Initialize Building Profile |
| **Actor(s)** | Primary: Project Manager <br> Secondary: Client / Owner Representative |
| **Description** | Sets up core project baseline and parameters for Building Permit & Approval System |
| **Precondition** | 1. User is authenticated with valid role permissions. <br> 2. Active project context is loaded in Building Permit & Approval System. |
| **Main Flow** | 1. Actor selects "Initialize Building Profile" from system navigation menu. <br> 2. System retrieves relevant workspace records and displays input interface. <br> 3. Actor enters required operational parameters and attaches supporting documents. <br> 4. System validates business logic constraints and data completeness. <br> 5. Actor confirms action and submits form. <br> 6. System saves record, updates status ledger, and issues confirmation notice. |
| **Alternative Flow** | **AF1** — Bulk Import: Actor uploads structured CSV/Excel template file for batch processing. <br> **AF2** — Draft Save: Actor saves input draft for pending review before final submission. |
| **Exception Flow** | **EX1** — Validation Error: System flags missing mandatory fields and highlights input errors. <br> **EX2** — Permission Denied: System blocks execution if user role lacks authorization. |
| **Postcondition** | Record is locked into system audit trail and downstream notification alerts are triggered. |
| **Business Rule** | **BR1**: All transactions must be timestamped and logged with user ID. <br> **BR2**: Changes affecting baseline figures require manager approval. |

---

### UC03 — Log Permit Applications Data

| Field | Detail |
|-------|--------|
| **UC ID** | UC03 |
| **Use Case Name** | Log Permit Applications Data |
| **Actor(s)** | Primary: Site Engineer <br> Secondary: Specialized Contractor |
| **Description** | Enters operational field records for Permit Applications |
| **Precondition** | 1. User is authenticated with valid role permissions. <br> 2. Active project context is loaded in Building Permit & Approval System. |
| **Main Flow** | 1. Actor selects "Log Permit Applications Data" from system navigation menu. <br> 2. System retrieves relevant workspace records and displays input interface. <br> 3. Actor enters required operational parameters and attaches supporting documents. <br> 4. System validates business logic constraints and data completeness. <br> 5. Actor confirms action and submits form. <br> 6. System saves record, updates status ledger, and issues confirmation notice. |
| **Alternative Flow** | **AF1** — Bulk Import: Actor uploads structured CSV/Excel template file for batch processing. <br> **AF2** — Draft Save: Actor saves input draft for pending review before final submission. |
| **Exception Flow** | **EX1** — Validation Error: System flags missing mandatory fields and highlights input errors. <br> **EX2** — Permission Denied: System blocks execution if user role lacks authorization. |
| **Postcondition** | Record is locked into system audit trail and downstream notification alerts are triggered. |
| **Business Rule** | **BR1**: All transactions must be timestamped and logged with user ID. <br> **BR2**: Changes affecting baseline figures require manager approval. |

---

### UC04 — Process  Municipal Inspections Workflow

| Field | Detail |
|-------|--------|
| **UC ID** | UC04 |
| **Use Case Name** | Process  Municipal Inspections Workflow |
| **Actor(s)** | Primary: Site Engineer <br> Secondary: Quality / Safety Inspector |
| **Description** | Executes standard process flow for  Municipal Inspections |
| **Precondition** | 1. User is authenticated with valid role permissions. <br> 2. Active project context is loaded in Building Permit & Approval System. |
| **Main Flow** | 1. Actor selects "Process  Municipal Inspections Workflow" from system navigation menu. <br> 2. System retrieves relevant workspace records and displays input interface. <br> 3. Actor enters required operational parameters and attaches supporting documents. <br> 4. System validates business logic constraints and data completeness. <br> 5. Actor confirms action and submits form. <br> 6. System saves record, updates status ledger, and issues confirmation notice. |
| **Alternative Flow** | **AF1** — Bulk Import: Actor uploads structured CSV/Excel template file for batch processing. <br> **AF2** — Draft Save: Actor saves input draft for pending review before final submission. |
| **Exception Flow** | **EX1** — Validation Error: System flags missing mandatory fields and highlights input errors. <br> **EX2** — Permission Denied: System blocks execution if user role lacks authorization. |
| **Postcondition** | Record is locked into system audit trail and downstream notification alerts are triggered. |
| **Business Rule** | **BR1**: All transactions must be timestamped and logged with user ID. <br> **BR2**: Changes affecting baseline figures require manager approval. |

---

### UC05 — Evaluate  Zoning Review Compliance

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Evaluate  Zoning Review Compliance |
| **Actor(s)** | Primary: Quality / Safety Inspector <br> Secondary: Project Manager |
| **Description** | Audits field activities against  Zoning Review standards |
| **Precondition** | 1. User is authenticated with valid role permissions. <br> 2. Active project context is loaded in Building Permit & Approval System. |
| **Main Flow** | 1. Actor selects "Evaluate  Zoning Review Compliance" from system navigation menu. <br> 2. System retrieves relevant workspace records and displays input interface. <br> 3. Actor enters required operational parameters and attaches supporting documents. <br> 4. System validates business logic constraints and data completeness. <br> 5. Actor confirms action and submits form. <br> 6. System saves record, updates status ledger, and issues confirmation notice. |
| **Alternative Flow** | **AF1** — Bulk Import: Actor uploads structured CSV/Excel template file for batch processing. <br> **AF2** — Draft Save: Actor saves input draft for pending review before final submission. |
| **Exception Flow** | **EX1** — Validation Error: System flags missing mandatory fields and highlights input errors. <br> **EX2** — Permission Denied: System blocks execution if user role lacks authorization. |
| **Postcondition** | Record is locked into system audit trail and downstream notification alerts are triggered. |
| **Business Rule** | **BR1**: All transactions must be timestamped and logged with user ID. <br> **BR2**: Changes affecting baseline figures require manager approval. |

---

### UC06 — Manage  Permit Issuance Records

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Manage  Permit Issuance Records |
| **Actor(s)** | Primary: Specialized Contractor <br> Secondary: Site Engineer |
| **Description** | Maintains documentation and certificates for  Permit Issuance |
| **Precondition** | 1. User is authenticated with valid role permissions. <br> 2. Active project context is loaded in Building Permit & Approval System. |
| **Main Flow** | 1. Actor selects "Manage  Permit Issuance Records" from system navigation menu. <br> 2. System retrieves relevant workspace records and displays input interface. <br> 3. Actor enters required operational parameters and attaches supporting documents. <br> 4. System validates business logic constraints and data completeness. <br> 5. Actor confirms action and submits form. <br> 6. System saves record, updates status ledger, and issues confirmation notice. |
| **Alternative Flow** | **AF1** — Bulk Import: Actor uploads structured CSV/Excel template file for batch processing. <br> **AF2** — Draft Save: Actor saves input draft for pending review before final submission. |
| **Exception Flow** | **EX1** — Validation Error: System flags missing mandatory fields and highlights input errors. <br> **EX2** — Permission Denied: System blocks execution if user role lacks authorization. |
| **Postcondition** | Record is locked into system audit trail and downstream notification alerts are triggered. |
| **Business Rule** | **BR1**: All transactions must be timestamped and logged with user ID. <br> **BR2**: Changes affecting baseline figures require manager approval. |

