# Use Case Diagram — Enterprise Integration Platform (EIP)

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["Integration Architect"]
    actor_Primary2["Enterprise Developer"]
    actor_Primary3["System Administrator"]
    actor_Primary4["Security Auditor"]

    subgraph SystemBoundary["Enterprise Integration Platform (EIP)"]
        UC01(["Configure Enterprise Integration Flow"])
        UC02(["Register System Connector Endpoint"])
        UC03(["Transform XML JSON Data Payload"])
        UC04(["Authenticate Integration Session"])
        UC05(["Monitor Message Queue Throughput"])
        UC06(["Configure Dead Letter Queue DLQ Rules"])
        UC07(["Enforce Message Encryption Payload"])
        UC08(["Replay Failed Message Transactions"])
        UC09(["Manage Enterprise API Connectors"])
        UC10(["Configure Content-Based Router"])
        UC11(["Monitor Real-Time Integration Latency"])
        UC12(["Configure Dynamic Service Throttling"])
        UC13(["Generate Integration Transaction Reports"])
        UC14(["Export EIP Compliance Audit Logs"])
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
| 1 | Integration Architect | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | Enterprise Developer | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | System Administrator | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | Security Auditor | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Configure Enterprise Integration Flow | Integration Architect | Supporting System | Handles configure enterprise integration flow operations within system boundary | High |
| 2 | UC02 | Register System Connector Endpoint | Enterprise Developer | Supporting System | Handles register system connector endpoint operations within system boundary | High |
| 3 | UC03 | Transform XML JSON Data Payload | System Administrator | Supporting System | Handles transform xml json data payload operations within system boundary | High |
| 4 | UC04 | Authenticate Integration Session | Security Auditor | Supporting System | Handles authenticate integration session operations within system boundary | High |
| 5 | UC05 | Monitor Message Queue Throughput | Integration Architect | Supporting System | Handles monitor message queue throughput operations within system boundary | High |
| 6 | UC06 | Configure Dead Letter Queue DLQ Rules | Enterprise Developer | Supporting System | Handles configure dead letter queue dlq rules operations within system boundary | High |
| 7 | UC07 | Enforce Message Encryption Payload | System Administrator | Supporting System | Handles enforce message encryption payload operations within system boundary | High |
| 8 | UC08 | Replay Failed Message Transactions | Security Auditor | Supporting System | Handles replay failed message transactions operations within system boundary | Medium |
| 9 | UC09 | Manage Enterprise API Connectors | Integration Architect | Supporting System | Handles manage enterprise api connectors operations within system boundary | Medium |
| 10 | UC10 | Configure Content-Based Router | Enterprise Developer | Supporting System | Handles configure content-based router operations within system boundary | High |
| 11 | UC11 | Monitor Real-Time Integration Latency | System Administrator | Supporting System | Handles monitor real-time integration latency operations within system boundary | Medium |
| 12 | UC12 | Configure Dynamic Service Throttling | Security Auditor | Supporting System | Handles configure dynamic service throttling operations within system boundary | Medium |
| 13 | UC13 | Generate Integration Transaction Reports | Integration Architect | Supporting System | Handles generate integration transaction reports operations within system boundary | Medium |
| 14 | UC14 | Export EIP Compliance Audit Logs | Enterprise Developer | Supporting System | Handles export eip compliance audit logs operations within system boundary | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Configure Enterprise Integration Flow

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Configure Enterprise Integration Flow |
| **Actor(s)** | Primary: Integration Architect |
| **Description** | Allows primary actors to configure and execute configure enterprise integration flow within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Monitor Message Queue Throughput

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Monitor Message Queue Throughput |
| **Actor(s)** | Primary: Enterprise Developer |
| **Description** | Executes monitor message queue throughput with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Configure Dead Letter Queue DLQ Rules

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Configure Dead Letter Queue DLQ Rules |
| **Actor(s)** | Primary: System Administrator |
| **Description** | Performs configure dead letter queue dlq rules to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — Enforce Message Encryption Payload

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | Enforce Message Encryption Payload |
| **Actor(s)** | Primary: System Administrator |
| **Description** | Manages enforce message encryption payload to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Configure Content-Based Router

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Configure Content-Based Router |
| **Actor(s)** | Primary: Security Auditor |
| **Description** | Conducts configure content-based router for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
