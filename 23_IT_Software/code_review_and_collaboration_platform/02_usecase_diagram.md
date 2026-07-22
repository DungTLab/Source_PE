# Use Case Diagram — Code Review & Collaboration Platform

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["Lead Software Architect"]
    actor_Primary2["Senior Developer Reviewer"]
    actor_Primary3["Software Engineer Author"]
    actor_Primary4["Security Engineer"]

    subgraph SystemBoundary["Code Review & Collaboration Platform"]
        UC01(["Create Code Review Pull Request"])
        UC02(["Perform Line-by-Line Inline Code Review"])
        UC03(["Approve Pull Request Merge"])
        UC04(["Authenticate Developer Session"])
        UC05(["Request Changes on Code Review"])
        UC06(["Enforce Branch Protection Approval Gate"])
        UC07(["View Side-by-Side Unified Code Diff"])
        UC08(["Auto-Assign Code Reviewers by CODEOWNERS"])
        UC09(["Integrate Automated Linter SAST Checks"])
        UC10(["Track Pull Request Resolution Time"])
        UC11(["Manage Code Suggestion One-Click Commit"])
        UC12(["Configure Reviewer Assignment Round-Robin"])
        UC13(["Generate Code Review Team Velocity Reports"])
        UC14(["Export Code Review Security Audit Trail"])
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
| 1 | Lead Software Architect | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | Senior Developer Reviewer | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | Software Engineer Author | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | Security Engineer | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Create Code Review Pull Request | Lead Software Architect | Supporting System | Handles create code review pull request operations within system boundary | High |
| 2 | UC02 | Perform Line-by-Line Inline Code Review | Senior Developer Reviewer | Supporting System | Handles perform line-by-line inline code review operations within system boundary | High |
| 3 | UC03 | Approve Pull Request Merge | Software Engineer Author | Supporting System | Handles approve pull request merge operations within system boundary | High |
| 4 | UC04 | Authenticate Developer Session | Security Engineer | Supporting System | Handles authenticate developer session operations within system boundary | High |
| 5 | UC05 | Request Changes on Code Review | Lead Software Architect | Supporting System | Handles request changes on code review operations within system boundary | High |
| 6 | UC06 | Enforce Branch Protection Approval Gate | Senior Developer Reviewer | Supporting System | Handles enforce branch protection approval gate operations within system boundary | High |
| 7 | UC07 | View Side-by-Side Unified Code Diff | Software Engineer Author | Supporting System | Handles view side-by-side unified code diff operations within system boundary | High |
| 8 | UC08 | Auto-Assign Code Reviewers by CODEOWNERS | Security Engineer | Supporting System | Handles auto-assign code reviewers by codeowners operations within system boundary | High |
| 9 | UC09 | Integrate Automated Linter SAST Checks | Lead Software Architect | Supporting System | Handles integrate automated linter sast checks operations within system boundary | High |
| 10 | UC10 | Track Pull Request Resolution Time | Senior Developer Reviewer | Supporting System | Handles track pull request resolution time operations within system boundary | Medium |
| 11 | UC11 | Manage Code Suggestion One-Click Commit | Software Engineer Author | Supporting System | Handles manage code suggestion one-click commit operations within system boundary | Medium |
| 12 | UC12 | Configure Reviewer Assignment Round-Robin | Security Engineer | Supporting System | Handles configure reviewer assignment round-robin operations within system boundary | Medium |
| 13 | UC13 | Generate Code Review Team Velocity Reports | Lead Software Architect | Supporting System | Handles generate code review team velocity reports operations within system boundary | Medium |
| 14 | UC14 | Export Code Review Security Audit Trail | Senior Developer Reviewer | Supporting System | Handles export code review security audit trail operations within system boundary | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Create Code Review Pull Request

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Create Code Review Pull Request |
| **Actor(s)** | Primary: Lead Software Architect |
| **Description** | Allows primary actors to configure and execute create code review pull request within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Request Changes on Code Review

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Request Changes on Code Review |
| **Actor(s)** | Primary: Senior Developer Reviewer |
| **Description** | Executes request changes on code review with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Enforce Branch Protection Approval Gate

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Enforce Branch Protection Approval Gate |
| **Actor(s)** | Primary: Software Engineer Author |
| **Description** | Performs enforce branch protection approval gate to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — View Side-by-Side Unified Code Diff

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | View Side-by-Side Unified Code Diff |
| **Actor(s)** | Primary: Software Engineer Author |
| **Description** | Manages view side-by-side unified code diff to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Track Pull Request Resolution Time

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Track Pull Request Resolution Time |
| **Actor(s)** | Primary: Security Engineer |
| **Description** | Conducts track pull request resolution time for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
