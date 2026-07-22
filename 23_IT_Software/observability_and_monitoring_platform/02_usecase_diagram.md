# Use Case Diagram — Observability & Monitoring Platform

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["Observability Architect"]
    actor_Primary2["DevOps & Site Reliability Engineer SRE"]
    actor_Primary3["Software Engineer"]
    actor_Primary4["NOC Analyst"]

    subgraph SystemBoundary["Observability & Monitoring Platform"]
        UC01(["Ingest OpenTelemetry Metrics & Logs"])
        UC02(["Visualize Distributed Trace Spans"])
        UC03(["Configure High-Frequency Alert Thresholds"])
        UC04(["Authenticate SRE Engineer Session"])
        UC05(["Troubleshoot Root Cause Latency Spikes"])
        UC06(["Correlate Logs Metrics & Traces MELT"])
        UC07(["Monitor Service Level Indicators SLIs"])
        UC08(["Manage Log Data Retention Hot Cold Tier"])
        UC09(["Detect Machine Learning Anomaly Outliers"])
        UC10(["Configure Custom Observability Dashboards"])
        UC11(["Dispatch Emergency Incident Notifications"])
        UC12(["Manage Telemetry Collector Sampling Rates"])
        UC13(["Generate Service Reliability & Error Budget Reports"])
        UC14(["Export Observability Compliance Audit Logs"])
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
| 1 | Observability Architect | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | DevOps & Site Reliability Engineer SRE | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | Software Engineer | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | NOC Analyst | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Ingest OpenTelemetry Metrics & Logs | Observability Architect | Supporting System | Handles ingest opentelemetry metrics & logs operations within system boundary | High |
| 2 | UC02 | Visualize Distributed Trace Spans | DevOps & Site Reliability Engineer SRE | Supporting System | Handles visualize distributed trace spans operations within system boundary | High |
| 3 | UC03 | Configure High-Frequency Alert Thresholds | Software Engineer | Supporting System | Handles configure high-frequency alert thresholds operations within system boundary | High |
| 4 | UC04 | Authenticate SRE Engineer Session | NOC Analyst | Supporting System | Handles authenticate sre engineer session operations within system boundary | High |
| 5 | UC05 | Troubleshoot Root Cause Latency Spikes | Observability Architect | Supporting System | Handles troubleshoot root cause latency spikes operations within system boundary | High |
| 6 | UC06 | Correlate Logs Metrics & Traces MELT | DevOps & Site Reliability Engineer SRE | Supporting System | Handles correlate logs metrics & traces melt operations within system boundary | High |
| 7 | UC07 | Monitor Service Level Indicators SLIs | Software Engineer | Supporting System | Handles monitor service level indicators slis operations within system boundary | High |
| 8 | UC08 | Manage Log Data Retention Hot Cold Tier | NOC Analyst | Supporting System | Handles manage log data retention hot cold tier operations within system boundary | Medium |
| 9 | UC09 | Detect Machine Learning Anomaly Outliers | Observability Architect | Supporting System | Handles detect machine learning anomaly outliers operations within system boundary | High |
| 10 | UC10 | Configure Custom Observability Dashboards | DevOps & Site Reliability Engineer SRE | Supporting System | Handles configure custom observability dashboards operations within system boundary | Medium |
| 11 | UC11 | Dispatch Emergency Incident Notifications | Software Engineer | Supporting System | Handles dispatch emergency incident notifications operations within system boundary | High |
| 12 | UC12 | Manage Telemetry Collector Sampling Rates | NOC Analyst | Supporting System | Handles manage telemetry collector sampling rates operations within system boundary | Medium |
| 13 | UC13 | Generate Service Reliability & Error Budget Reports | Observability Architect | Supporting System | Handles generate service reliability & error budget reports operations within system boundary | Medium |
| 14 | UC14 | Export Observability Compliance Audit Logs | DevOps & Site Reliability Engineer SRE | Supporting System | Handles export observability compliance audit logs operations within system boundary | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Ingest OpenTelemetry Metrics & Logs

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Ingest OpenTelemetry Metrics & Logs |
| **Actor(s)** | Primary: Observability Architect |
| **Description** | Allows primary actors to configure and execute ingest opentelemetry metrics & logs within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Troubleshoot Root Cause Latency Spikes

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Troubleshoot Root Cause Latency Spikes |
| **Actor(s)** | Primary: DevOps & Site Reliability Engineer SRE |
| **Description** | Executes troubleshoot root cause latency spikes with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Correlate Logs Metrics & Traces MELT

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Correlate Logs Metrics & Traces MELT |
| **Actor(s)** | Primary: Software Engineer |
| **Description** | Performs correlate logs metrics & traces melt to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — Monitor Service Level Indicators SLIs

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | Monitor Service Level Indicators SLIs |
| **Actor(s)** | Primary: Software Engineer |
| **Description** | Manages monitor service level indicators slis to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Configure Custom Observability Dashboards

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Configure Custom Observability Dashboards |
| **Actor(s)** | Primary: NOC Analyst |
| **Description** | Conducts configure custom observability dashboards for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
