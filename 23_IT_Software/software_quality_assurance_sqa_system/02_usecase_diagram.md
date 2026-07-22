# Use Case Diagram — Software Quality Assurance (SQA) System

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["SQA Manager / Auditor"]
    actor_Primary2["Software Quality Engineer"]
    actor_Primary3["Project Manager"]
    actor_Primary4["Process Owner"]

    subgraph SystemBoundary["Software Quality Assurance (SQA) System"]
        UC01(["Formulate Project SQA Quality Plan"])
        UC02(["Conduct Software Process Audit Inspection"])
        UC03(["Log Process Non-Conformance Report NC"])
        UC04(["Authenticate SQA Auditor Session"])
        UC05(["Verify Corrective Action Plan CAP"])
        UC06(["Evaluate CMMI Process Maturity Level"])
        UC07(["Audit Software Artifact Sign-offs"])
        UC08(["Track Software Quality Gate Compliance"])
        UC09(["Manage SQA Process Checklist Templates"])
        UC10(["Evaluate Code Review Coverage Metrics"])
        UC11(["Conduct Phase-End Stage-Gate Quality Review"])
        UC12(["Configure SQA Audit Sampling Rules"])
        UC13(["Generate Executive SQA Quality Dashboard"])
        UC14(["Export ISO 9001 CMMI Compliance Audit Trail"])
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
| 1 | SQA Manager / Auditor | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | Software Quality Engineer | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | Project Manager | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | Process Owner | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Formulate Project SQA Quality Plan | SQA Manager / Auditor | Supporting System | Handles formulate project sqa quality plan operations within system boundary | High |
| 2 | UC02 | Conduct Software Process Audit Inspection | Software Quality Engineer | Supporting System | Handles conduct software process audit inspection operations within system boundary | High |
| 3 | UC03 | Log Process Non-Conformance Report NC | Project Manager | Supporting System | Handles log process non-conformance report nc operations within system boundary | High |
| 4 | UC04 | Authenticate SQA Auditor Session | Process Owner | Supporting System | Handles authenticate sqa auditor session operations within system boundary | High |
| 5 | UC05 | Verify Corrective Action Plan CAP | SQA Manager / Auditor | Supporting System | Handles verify corrective action plan cap operations within system boundary | High |
| 6 | UC06 | Evaluate CMMI Process Maturity Level | Software Quality Engineer | Supporting System | Handles evaluate cmmi process maturity level operations within system boundary | High |
| 7 | UC07 | Audit Software Artifact Sign-offs | Project Manager | Supporting System | Handles audit software artifact sign-offs operations within system boundary | High |
| 8 | UC08 | Track Software Quality Gate Compliance | Process Owner | Supporting System | Handles track software quality gate compliance operations within system boundary | High |
| 9 | UC09 | Manage SQA Process Checklist Templates | SQA Manager / Auditor | Supporting System | Handles manage sqa process checklist templates operations within system boundary | Medium |
| 10 | UC10 | Evaluate Code Review Coverage Metrics | Software Quality Engineer | Supporting System | Handles evaluate code review coverage metrics operations within system boundary | Medium |
| 11 | UC11 | Conduct Phase-End Stage-Gate Quality Review | Project Manager | Supporting System | Handles conduct phase-end stage-gate quality review operations within system boundary | High |
| 12 | UC12 | Configure SQA Audit Sampling Rules | Process Owner | Supporting System | Handles configure sqa audit sampling rules operations within system boundary | Low |
| 13 | UC13 | Generate Executive SQA Quality Dashboard | SQA Manager / Auditor | Supporting System | Handles generate executive sqa quality dashboard operations within system boundary | Medium |
| 14 | UC14 | Export ISO 9001 CMMI Compliance Audit Trail | Software Quality Engineer | Supporting System | Handles export iso 9001 cmmi compliance audit trail operations within system boundary | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Formulate Project SQA Quality Plan

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Formulate Project SQA Quality Plan |
| **Actor(s)** | Primary: SQA Manager / Auditor |
| **Description** | Allows primary actors to configure and execute formulate project sqa quality plan within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Verify Corrective Action Plan CAP

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Verify Corrective Action Plan CAP |
| **Actor(s)** | Primary: Software Quality Engineer |
| **Description** | Executes verify corrective action plan cap with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Evaluate CMMI Process Maturity Level

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Evaluate CMMI Process Maturity Level |
| **Actor(s)** | Primary: Project Manager |
| **Description** | Performs evaluate cmmi process maturity level to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — Audit Software Artifact Sign-offs

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | Audit Software Artifact Sign-offs |
| **Actor(s)** | Primary: Project Manager |
| **Description** | Manages audit software artifact sign-offs to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Evaluate Code Review Coverage Metrics

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Evaluate Code Review Coverage Metrics |
| **Actor(s)** | Primary: Process Owner |
| **Description** | Conducts evaluate code review coverage metrics for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
