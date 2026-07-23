# Use Case Diagram — Green Building Design Management System

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

    subgraph SystemBoundary["Green Building Design Management System"]
        UC01(["Authenticate Green User"])
        UC02(["Initialize Green Profile"])
        UC03(["Log LEED/LOTUS Rating Data"])
        UC04(["Process  Energy Efficiency Simulation Workflow"])
        UC05(["Evaluate  Recycled Materials Compliance"])
        UC06(["Manage  Carbon Log Records"])
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
| 1 | Project Manager | Primary | Responsible for execution and monitoring within Green Building Design Management System | UC01, UC02, UC07, UC12 |
| 2 | Site Engineer | Primary | Responsible for execution and monitoring within Green Building Design Management System | UC03, UC04, UC10 |
| 3 | Specialized Contractor | Primary | Responsible for execution and monitoring within Green Building Design Management System | UC06 |
| 4 | Quality / Safety Inspector | Primary | Responsible for execution and monitoring within Green Building Design Management System | UC05, UC08 |
| 5 | Client / Owner Representative | Primary | Responsible for execution and monitoring within Green Building Design Management System | UC09 |
| 6 | Enterprise ERP System | Supporting | Responsible for execution and monitoring within Green Building Design Management System | UC11 |
| 7 | Regulatory Building Authority | Regulatory | Responsible for execution and monitoring within Green Building Design Management System | UC01 |

## Use Case Table | Bang Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Authenticate Green User | Project Manager | None | Authenticates system user for Green Building Design Management System | High |
| 2 | UC02 | Initialize Green Profile | Project Manager | Client / Owner Representative | Sets up core project baseline and parameters for Green Building Design Management System | High |
| 3 | UC03 | Log LEED/LOTUS Rating Data | Site Engineer | Specialized Contractor | Enters operational field records for LEED/LOTUS Rating | High |
| 4 | UC04 | Process  Energy Efficiency Simulation Workflow | Site Engineer | Quality / Safety Inspector | Executes standard process flow for  Energy Efficiency Simulation | High |
| 5 | UC05 | Evaluate  Recycled Materials Compliance | Quality / Safety Inspector | Project Manager | Audits field activities against  Recycled Materials standards | High |
| 6 | UC06 | Manage  Carbon Log Records | Specialized Contractor | Site Engineer | Maintains documentation and certificates for  Carbon Log | High |
| 7 | UC07 | Perform Real-time Analytics | Project Manager | Enterprise ERP System | Computes system KPIs, variances, and status trends | Medium |
| 8 | UC08 | Generate Regulatory Audit Package | Quality / Safety Inspector | Regulatory Building Authority | Compiles required compliance documentation for official authority | High |
| 9 | UC09 | Approve Status Sign-off | Client / Owner Representative | Project Manager | Grants formal approval for project milestone completion | High |
| 10 | UC10 | Version System Documentation | Site Engineer | Project Manager | Tracks historical document revisions and sign-off logs | Medium |
| 11 | UC11 | Trigger Automated Exception Alerts | Enterprise ERP System | Project Manager | Issues system warnings upon threshold breaches | High |
| 12 | UC12 | Export Executive Progress Reports | Project Manager | Client / Owner Representative | Generates summary dashboard analytics and exportable reports | High |

## Use Case Specification | Dac ta Use Case

---

### UC02 — Initialize Green Profile

| Field | Detail |
|-------|--------|
| **UC ID** | UC02 |
| **Use Case Name** | Initialize Green Profile |
| **Actor(s)** | Primary: Project Manager <br> Secondary: Client / Owner Representative |
| **Description** | Sets up core project baseline and parameters for Green Building Design Management System |
| **Precondition** | 1. User is authenticated with valid role permissions. <br> 2. Active project context is loaded in Green Building Design Management System. |
| **Main Flow** | 1. Actor selects "Initialize Green Profile" from system navigation menu. <br> 2. System retrieves relevant workspace records and displays input interface. <br> 3. Actor enters required operational parameters and attaches supporting documents. <br> 4. System validates business logic constraints and data completeness. <br> 5. Actor confirms action and submits form. <br> 6. System saves record, updates status ledger, and issues confirmation notice. |
| **Alternative Flow** | **AF1** — Bulk Import: Actor uploads structured CSV/Excel template file for batch processing. <br> **AF2** — Draft Save: Actor saves input draft for pending review before final submission. |
| **Exception Flow** | **EX1** — Validation Error: System flags missing mandatory fields and highlights input errors. <br> **EX2** — Permission Denied: System blocks execution if user role lacks authorization. |
| **Postcondition** | Record is locked into system audit trail and downstream notification alerts are triggered. |
| **Business Rule** | **BR1**: All transactions must be timestamped and logged with user ID. <br> **BR2**: Changes affecting baseline figures require manager approval. |

---

### UC03 — Log LEED/LOTUS Rating Data

| Field | Detail |
|-------|--------|
| **UC ID** | UC03 |
| **Use Case Name** | Log LEED/LOTUS Rating Data |
| **Actor(s)** | Primary: Site Engineer <br> Secondary: Specialized Contractor |
| **Description** | Enters operational field records for LEED/LOTUS Rating |
| **Precondition** | 1. User is authenticated with valid role permissions. <br> 2. Active project context is loaded in Green Building Design Management System. |
| **Main Flow** | 1. Actor selects "Log LEED/LOTUS Rating Data" from system navigation menu. <br> 2. System retrieves relevant workspace records and displays input interface. <br> 3. Actor enters required operational parameters and attaches supporting documents. <br> 4. System validates business logic constraints and data completeness. <br> 5. Actor confirms action and submits form. <br> 6. System saves record, updates status ledger, and issues confirmation notice. |
| **Alternative Flow** | **AF1** — Bulk Import: Actor uploads structured CSV/Excel template file for batch processing. <br> **AF2** — Draft Save: Actor saves input draft for pending review before final submission. |
| **Exception Flow** | **EX1** — Validation Error: System flags missing mandatory fields and highlights input errors. <br> **EX2** — Permission Denied: System blocks execution if user role lacks authorization. |
| **Postcondition** | Record is locked into system audit trail and downstream notification alerts are triggered. |
| **Business Rule** | **BR1**: All transactions must be timestamped and logged with user ID. <br> **BR2**: Changes affecting baseline figures require manager approval. |

---

### UC04 — Process  Energy Efficiency Simulation Workflow

| Field | Detail |
|-------|--------|
| **UC ID** | UC04 |
| **Use Case Name** | Process  Energy Efficiency Simulation Workflow |
| **Actor(s)** | Primary: Site Engineer <br> Secondary: Quality / Safety Inspector |
| **Description** | Executes standard process flow for  Energy Efficiency Simulation |
| **Precondition** | 1. User is authenticated with valid role permissions. <br> 2. Active project context is loaded in Green Building Design Management System. |
| **Main Flow** | 1. Actor selects "Process  Energy Efficiency Simulation Workflow" from system navigation menu. <br> 2. System retrieves relevant workspace records and displays input interface. <br> 3. Actor enters required operational parameters and attaches supporting documents. <br> 4. System validates business logic constraints and data completeness. <br> 5. Actor confirms action and submits form. <br> 6. System saves record, updates status ledger, and issues confirmation notice. |
| **Alternative Flow** | **AF1** — Bulk Import: Actor uploads structured CSV/Excel template file for batch processing. <br> **AF2** — Draft Save: Actor saves input draft for pending review before final submission. |
| **Exception Flow** | **EX1** — Validation Error: System flags missing mandatory fields and highlights input errors. <br> **EX2** — Permission Denied: System blocks execution if user role lacks authorization. |
| **Postcondition** | Record is locked into system audit trail and downstream notification alerts are triggered. |
| **Business Rule** | **BR1**: All transactions must be timestamped and logged with user ID. <br> **BR2**: Changes affecting baseline figures require manager approval. |

---

### UC05 — Evaluate  Recycled Materials Compliance

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Evaluate  Recycled Materials Compliance |
| **Actor(s)** | Primary: Quality / Safety Inspector <br> Secondary: Project Manager |
| **Description** | Audits field activities against  Recycled Materials standards |
| **Precondition** | 1. User is authenticated with valid role permissions. <br> 2. Active project context is loaded in Green Building Design Management System. |
| **Main Flow** | 1. Actor selects "Evaluate  Recycled Materials Compliance" from system navigation menu. <br> 2. System retrieves relevant workspace records and displays input interface. <br> 3. Actor enters required operational parameters and attaches supporting documents. <br> 4. System validates business logic constraints and data completeness. <br> 5. Actor confirms action and submits form. <br> 6. System saves record, updates status ledger, and issues confirmation notice. |
| **Alternative Flow** | **AF1** — Bulk Import: Actor uploads structured CSV/Excel template file for batch processing. <br> **AF2** — Draft Save: Actor saves input draft for pending review before final submission. |
| **Exception Flow** | **EX1** — Validation Error: System flags missing mandatory fields and highlights input errors. <br> **EX2** — Permission Denied: System blocks execution if user role lacks authorization. |
| **Postcondition** | Record is locked into system audit trail and downstream notification alerts are triggered. |
| **Business Rule** | **BR1**: All transactions must be timestamped and logged with user ID. <br> **BR2**: Changes affecting baseline figures require manager approval. |

---

### UC06 — Manage  Carbon Log Records

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Manage  Carbon Log Records |
| **Actor(s)** | Primary: Specialized Contractor <br> Secondary: Site Engineer |
| **Description** | Maintains documentation and certificates for  Carbon Log |
| **Precondition** | 1. User is authenticated with valid role permissions. <br> 2. Active project context is loaded in Green Building Design Management System. |
| **Main Flow** | 1. Actor selects "Manage  Carbon Log Records" from system navigation menu. <br> 2. System retrieves relevant workspace records and displays input interface. <br> 3. Actor enters required operational parameters and attaches supporting documents. <br> 4. System validates business logic constraints and data completeness. <br> 5. Actor confirms action and submits form. <br> 6. System saves record, updates status ledger, and issues confirmation notice. |
| **Alternative Flow** | **AF1** — Bulk Import: Actor uploads structured CSV/Excel template file for batch processing. <br> **AF2** — Draft Save: Actor saves input draft for pending review before final submission. |
| **Exception Flow** | **EX1** — Validation Error: System flags missing mandatory fields and highlights input errors. <br> **EX2** — Permission Denied: System blocks execution if user role lacks authorization. |
| **Postcondition** | Record is locked into system audit trail and downstream notification alerts are triggered. |
| **Business Rule** | **BR1**: All transactions must be timestamped and logged with user ID. <br> **BR2**: Changes affecting baseline figures require manager approval. |

