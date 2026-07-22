# Use Case Diagram — Agile & Scrum Project Tracking System

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["Scrum Master"]
    actor_Primary2["Product Owner"]
    actor_Primary3["Development Team Member"]
    actor_Primary4["Agile Coach"]

    subgraph SystemBoundary["Agile & Scrum Project Tracking System"]
        UC01(["Create Product Backlog Epics & Stories"])
        UC02(["Plan Sprint Iteration Backlog"])
        UC03(["Manage Interactive Scrum Kanban Board"])
        UC04(["Authenticate Team Member Session"])
        UC05(["Estimate Story Points Planning Poker"])
        UC06(["Track Real-time Sprint Burndown Chart"])
        UC07(["Conduct Sprint Retrospective Feedback"])
        UC08(["Calculate Team Velocity Metrics"])
        UC09(["Manage Impediment Blockers List"])
        UC10(["Link Git Commits to Backlog Ticket ID"])
        UC11(["Configure WIP Work In Progress Limits"])
        UC12(["Manage Release Roadmap Timelines"])
        UC13(["Generate Agile Velocity & Quality Reports"])
        UC14(["Export Agile Process Audit Logs"])
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
| 1 | Scrum Master | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | Product Owner | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | Development Team Member | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | Agile Coach | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Create Product Backlog Epics & Stories | Scrum Master | Supporting System | Handles create product backlog epics & stories operations within system boundary | High |
| 2 | UC02 | Plan Sprint Iteration Backlog | Product Owner | Supporting System | Handles plan sprint iteration backlog operations within system boundary | High |
| 3 | UC03 | Manage Interactive Scrum Kanban Board | Development Team Member | Supporting System | Handles manage interactive scrum kanban board operations within system boundary | High |
| 4 | UC04 | Authenticate Team Member Session | Agile Coach | Supporting System | Handles authenticate team member session operations within system boundary | High |
| 5 | UC05 | Estimate Story Points Planning Poker | Scrum Master | Supporting System | Handles estimate story points planning poker operations within system boundary | High |
| 6 | UC06 | Track Real-time Sprint Burndown Chart | Product Owner | Supporting System | Handles track real-time sprint burndown chart operations within system boundary | High |
| 7 | UC07 | Conduct Sprint Retrospective Feedback | Development Team Member | Supporting System | Handles conduct sprint retrospective feedback operations within system boundary | Medium |
| 8 | UC08 | Calculate Team Velocity Metrics | Agile Coach | Supporting System | Handles calculate team velocity metrics operations within system boundary | High |
| 9 | UC09 | Manage Impediment Blockers List | Scrum Master | Supporting System | Handles manage impediment blockers list operations within system boundary | High |
| 10 | UC10 | Link Git Commits to Backlog Ticket ID | Product Owner | Supporting System | Handles link git commits to backlog ticket id operations within system boundary | High |
| 11 | UC11 | Configure WIP Work In Progress Limits | Development Team Member | Supporting System | Handles configure wip work in progress limits operations within system boundary | Medium |
| 12 | UC12 | Manage Release Roadmap Timelines | Agile Coach | Supporting System | Handles manage release roadmap timelines operations within system boundary | Medium |
| 13 | UC13 | Generate Agile Velocity & Quality Reports | Scrum Master | Supporting System | Handles generate agile velocity & quality reports operations within system boundary | Medium |
| 14 | UC14 | Export Agile Process Audit Logs | Product Owner | Supporting System | Handles export agile process audit logs operations within system boundary | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Create Product Backlog Epics & Stories

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Create Product Backlog Epics & Stories |
| **Actor(s)** | Primary: Scrum Master |
| **Description** | Allows primary actors to configure and execute create product backlog epics & stories within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Estimate Story Points Planning Poker

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Estimate Story Points Planning Poker |
| **Actor(s)** | Primary: Product Owner |
| **Description** | Executes estimate story points planning poker with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Track Real-time Sprint Burndown Chart

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Track Real-time Sprint Burndown Chart |
| **Actor(s)** | Primary: Development Team Member |
| **Description** | Performs track real-time sprint burndown chart to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — Conduct Sprint Retrospective Feedback

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | Conduct Sprint Retrospective Feedback |
| **Actor(s)** | Primary: Development Team Member |
| **Description** | Manages conduct sprint retrospective feedback to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Link Git Commits to Backlog Ticket ID

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Link Git Commits to Backlog Ticket ID |
| **Actor(s)** | Primary: Agile Coach |
| **Description** | Conducts link git commits to backlog ticket id for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
