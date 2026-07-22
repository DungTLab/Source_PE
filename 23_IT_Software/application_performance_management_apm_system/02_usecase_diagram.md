# Use Case Diagram — Application Performance Management (APM) System

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["APM Specialist"]
    actor_Primary2["DevOps & SRE Engineer"]
    actor_Primary3["Software Architect"]
    actor_Primary4["QA Performance Engineer"]

    subgraph SystemBoundary["Application Performance Management (APM) System"]
        UC01(["Install APM Bytecode Profiling Agent"])
        UC02(["Monitor Real User Monitoring RUM Metrics"])
        UC03(["Trace Slow Database SQL Queries"])
        UC04(["Authenticate APM Specialist Session"])
        UC05(["Detect JVM Memory Leak & Thread Dumps"])
        UC06(["Calculate Application Apdex Score"])
        UC07(["Configure Transaction Threshold Alerts"])
        UC08(["Analyze Code-Level Method Execution Time"])
        UC09(["Monitor HTTP Error 5xx Failure Rates"])
        UC10(["Correlate Infrastructure CPU to APM Latency"])
        UC11(["Trigger Automated Diagnostic Heap Dump"])
        UC12(["Configure Transaction Naming Rules"])
        UC13(["Generate Application Health Performance Report"])
        UC14(["Export APM Security Audit Logs"])
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
| 1 | APM Specialist | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | DevOps & SRE Engineer | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | Software Architect | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | QA Performance Engineer | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Install APM Bytecode Profiling Agent | APM Specialist | Supporting System | Handles install apm bytecode profiling agent operations within system boundary | High |
| 2 | UC02 | Monitor Real User Monitoring RUM Metrics | DevOps & SRE Engineer | Supporting System | Handles monitor real user monitoring rum metrics operations within system boundary | High |
| 3 | UC03 | Trace Slow Database SQL Queries | Software Architect | Supporting System | Handles trace slow database sql queries operations within system boundary | High |
| 4 | UC04 | Authenticate APM Specialist Session | QA Performance Engineer | Supporting System | Handles authenticate apm specialist session operations within system boundary | High |
| 5 | UC05 | Detect JVM Memory Leak & Thread Dumps | APM Specialist | Supporting System | Handles detect jvm memory leak & thread dumps operations within system boundary | High |
| 6 | UC06 | Calculate Application Apdex Score | DevOps & SRE Engineer | Supporting System | Handles calculate application apdex score operations within system boundary | High |
| 7 | UC07 | Configure Transaction Threshold Alerts | Software Architect | Supporting System | Handles configure transaction threshold alerts operations within system boundary | High |
| 8 | UC08 | Analyze Code-Level Method Execution Time | QA Performance Engineer | Supporting System | Handles analyze code-level method execution time operations within system boundary | High |
| 9 | UC09 | Monitor HTTP Error 5xx Failure Rates | APM Specialist | Supporting System | Handles monitor http error 5xx failure rates operations within system boundary | Medium |
| 10 | UC10 | Correlate Infrastructure CPU to APM Latency | DevOps & SRE Engineer | Supporting System | Handles correlate infrastructure cpu to apm latency operations within system boundary | Medium |
| 11 | UC11 | Trigger Automated Diagnostic Heap Dump | Software Architect | Supporting System | Handles trigger automated diagnostic heap dump operations within system boundary | High |
| 12 | UC12 | Configure Transaction Naming Rules | QA Performance Engineer | Supporting System | Handles configure transaction naming rules operations within system boundary | Low |
| 13 | UC13 | Generate Application Health Performance Report | APM Specialist | Supporting System | Handles generate application health performance report operations within system boundary | Medium |
| 14 | UC14 | Export APM Security Audit Logs | DevOps & SRE Engineer | Supporting System | Handles export apm security audit logs operations within system boundary | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Install APM Bytecode Profiling Agent

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Install APM Bytecode Profiling Agent |
| **Actor(s)** | Primary: APM Specialist |
| **Description** | Allows primary actors to configure and execute install apm bytecode profiling agent within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Detect JVM Memory Leak & Thread Dumps

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Detect JVM Memory Leak & Thread Dumps |
| **Actor(s)** | Primary: DevOps & SRE Engineer |
| **Description** | Executes detect jvm memory leak & thread dumps with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Calculate Application Apdex Score

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Calculate Application Apdex Score |
| **Actor(s)** | Primary: Software Architect |
| **Description** | Performs calculate application apdex score to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — Configure Transaction Threshold Alerts

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | Configure Transaction Threshold Alerts |
| **Actor(s)** | Primary: Software Architect |
| **Description** | Manages configure transaction threshold alerts to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Correlate Infrastructure CPU to APM Latency

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Correlate Infrastructure CPU to APM Latency |
| **Actor(s)** | Primary: QA Performance Engineer |
| **Description** | Conducts correlate infrastructure cpu to apm latency for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
