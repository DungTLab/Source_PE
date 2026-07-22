# Use Case Diagram — Edge Computing Management Platform

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["Edge Platform Architect"]
    actor_Primary2["Edge Operations Lead"]
    actor_Primary3["Application Developer"]
    actor_Primary4["Security Officer"]

    subgraph SystemBoundary["Edge Computing Management Platform"]
        UC01(["Provision Edge Compute Hardware Node"])
        UC02(["Deploy Micro-Container App to Edge"])
        UC03(["Synchronize Edge Data with Central Cloud"])
        UC04(["Authenticate Edge Admin Session"])
        UC05(["Monitor Edge Node Latency & Connectivity"])
        UC06(["Execute Offline Standalone Edge Mode"])
        UC07(["Remote Flash Edge OS Image"])
        UC08(["Manage Geographic Edge Clusters"])
        UC09(["Enforce Edge Zero-Trust Security Policy"])
        UC10(["Configure Edge Storage Caching"])
        UC11(["Troubleshoot Disconnected Edge Nodes"])
        UC12(["Manage Edge Application Rollout Rings"])
        UC13(["Generate Edge Bandwidth Savings Metrics"])
        UC14(["Export Edge Platform Security Audit Logs"])
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
| 1 | Edge Platform Architect | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | Edge Operations Lead | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | Application Developer | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | Security Officer | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Provision Edge Compute Hardware Node | Edge Platform Architect | Supporting System | Handles provision edge compute hardware node operations within system boundary | High |
| 2 | UC02 | Deploy Micro-Container App to Edge | Edge Operations Lead | Supporting System | Handles deploy micro-container app to edge operations within system boundary | High |
| 3 | UC03 | Synchronize Edge Data with Central Cloud | Application Developer | Supporting System | Handles synchronize edge data with central cloud operations within system boundary | High |
| 4 | UC04 | Authenticate Edge Admin Session | Security Officer | Supporting System | Handles authenticate edge admin session operations within system boundary | High |
| 5 | UC05 | Monitor Edge Node Latency & Connectivity | Edge Platform Architect | Supporting System | Handles monitor edge node latency & connectivity operations within system boundary | High |
| 6 | UC06 | Execute Offline Standalone Edge Mode | Edge Operations Lead | Supporting System | Handles execute offline standalone edge mode operations within system boundary | High |
| 7 | UC07 | Remote Flash Edge OS Image | Application Developer | Supporting System | Handles remote flash edge os image operations within system boundary | High |
| 8 | UC08 | Manage Geographic Edge Clusters | Security Officer | Supporting System | Handles manage geographic edge clusters operations within system boundary | Medium |
| 9 | UC09 | Enforce Edge Zero-Trust Security Policy | Edge Platform Architect | Supporting System | Handles enforce edge zero-trust security policy operations within system boundary | High |
| 10 | UC10 | Configure Edge Storage Caching | Edge Operations Lead | Supporting System | Handles configure edge storage caching operations within system boundary | Medium |
| 11 | UC11 | Troubleshoot Disconnected Edge Nodes | Application Developer | Supporting System | Handles troubleshoot disconnected edge nodes operations within system boundary | High |
| 12 | UC12 | Manage Edge Application Rollout Rings | Security Officer | Supporting System | Handles manage edge application rollout rings operations within system boundary | Medium |
| 13 | UC13 | Generate Edge Bandwidth Savings Metrics | Edge Platform Architect | Supporting System | Handles generate edge bandwidth savings metrics operations within system boundary | Medium |
| 14 | UC14 | Export Edge Platform Security Audit Logs | Edge Operations Lead | Supporting System | Handles export edge platform security audit logs operations within system boundary | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Provision Edge Compute Hardware Node

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Provision Edge Compute Hardware Node |
| **Actor(s)** | Primary: Edge Platform Architect |
| **Description** | Allows primary actors to configure and execute provision edge compute hardware node within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Monitor Edge Node Latency & Connectivity

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Monitor Edge Node Latency & Connectivity |
| **Actor(s)** | Primary: Edge Operations Lead |
| **Description** | Executes monitor edge node latency & connectivity with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Execute Offline Standalone Edge Mode

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Execute Offline Standalone Edge Mode |
| **Actor(s)** | Primary: Application Developer |
| **Description** | Performs execute offline standalone edge mode to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — Remote Flash Edge OS Image

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | Remote Flash Edge OS Image |
| **Actor(s)** | Primary: Application Developer |
| **Description** | Manages remote flash edge os image to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Configure Edge Storage Caching

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Configure Edge Storage Caching |
| **Actor(s)** | Primary: Security Officer |
| **Description** | Conducts configure edge storage caching for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
