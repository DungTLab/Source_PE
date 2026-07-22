# Use Case Diagram — Tech Talent Acquisition System

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["Tech Recruiter"]
    actor_Primary2["Engineering Hiring Manager"]
    actor_Primary3["Technical Interviewer"]
    actor_Primary4["Tech Candidate"]

    subgraph SystemBoundary["Tech Talent Acquisition System"]
        UC01(["Publish Tech Job Requisition"])
        UC02(["Parse Candidate Resume CV"])
        UC03(["Dispatch Automated Coding Assessment Test"])
        UC04(["Authenticate Recruiter Session"])
        UC05(["Schedule Technical Interview Panel"])
        UC06(["Submit Technical Interview Scorecard"])
        UC07(["Generate Job Offer Letter Package"])
        UC08(["Import Candidate Profile from LinkedIn"])
        UC09(["Manage Recruitment Funnel Stages"])
        UC10(["Track Time-to-Hire Tech Metrics"])
        UC11(["Conduct Candidate Background Check"])
        UC12(["Configure Tech Skill Taxonomy Tags"])
        UC13(["Generate Recruitment Analytics Dashboard"])
        UC14(["Export Hiring Compliance Audit Logs"])
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
| 1 | Tech Recruiter | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | Engineering Hiring Manager | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | Technical Interviewer | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | Tech Candidate | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Publish Tech Job Requisition | Tech Recruiter | Supporting System | Handles publish tech job requisition operations within system boundary | High |
| 2 | UC02 | Parse Candidate Resume CV | Engineering Hiring Manager | Supporting System | Handles parse candidate resume cv operations within system boundary | High |
| 3 | UC03 | Dispatch Automated Coding Assessment Test | Technical Interviewer | Supporting System | Handles dispatch automated coding assessment test operations within system boundary | High |
| 4 | UC04 | Authenticate Recruiter Session | Tech Candidate | Supporting System | Handles authenticate recruiter session operations within system boundary | High |
| 5 | UC05 | Schedule Technical Interview Panel | Tech Recruiter | Supporting System | Handles schedule technical interview panel operations within system boundary | High |
| 6 | UC06 | Submit Technical Interview Scorecard | Engineering Hiring Manager | Supporting System | Handles submit technical interview scorecard operations within system boundary | High |
| 7 | UC07 | Generate Job Offer Letter Package | Technical Interviewer | Supporting System | Handles generate job offer letter package operations within system boundary | High |
| 8 | UC08 | Import Candidate Profile from LinkedIn | Tech Candidate | Supporting System | Handles import candidate profile from linkedin operations within system boundary | Medium |
| 9 | UC09 | Manage Recruitment Funnel Stages | Tech Recruiter | Supporting System | Handles manage recruitment funnel stages operations within system boundary | High |
| 10 | UC10 | Track Time-to-Hire Tech Metrics | Engineering Hiring Manager | Supporting System | Handles track time-to-hire tech metrics operations within system boundary | Medium |
| 11 | UC11 | Conduct Candidate Background Check | Technical Interviewer | Supporting System | Handles conduct candidate background check operations within system boundary | Medium |
| 12 | UC12 | Configure Tech Skill Taxonomy Tags | Tech Candidate | Supporting System | Handles configure tech skill taxonomy tags operations within system boundary | Low |
| 13 | UC13 | Generate Recruitment Analytics Dashboard | Tech Recruiter | Supporting System | Handles generate recruitment analytics dashboard operations within system boundary | Medium |
| 14 | UC14 | Export Hiring Compliance Audit Logs | Engineering Hiring Manager | Supporting System | Handles export hiring compliance audit logs operations within system boundary | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Publish Tech Job Requisition

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Publish Tech Job Requisition |
| **Actor(s)** | Primary: Tech Recruiter |
| **Description** | Allows primary actors to configure and execute publish tech job requisition within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Schedule Technical Interview Panel

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Schedule Technical Interview Panel |
| **Actor(s)** | Primary: Engineering Hiring Manager |
| **Description** | Executes schedule technical interview panel with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Submit Technical Interview Scorecard

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Submit Technical Interview Scorecard |
| **Actor(s)** | Primary: Technical Interviewer |
| **Description** | Performs submit technical interview scorecard to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — Generate Job Offer Letter Package

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | Generate Job Offer Letter Package |
| **Actor(s)** | Primary: Technical Interviewer |
| **Description** | Manages generate job offer letter package to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Track Time-to-Hire Tech Metrics

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Track Time-to-Hire Tech Metrics |
| **Actor(s)** | Primary: Tech Candidate |
| **Description** | Conducts track time-to-hire tech metrics for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
