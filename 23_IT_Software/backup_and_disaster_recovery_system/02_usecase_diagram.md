# Use Case Diagram — Backup & Disaster Recovery System

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["Disaster Recovery Administrator"]
    actor_Primary2["System Administrator"]
    actor_Primary3["Database Administrator"]
    actor_Primary4["Security Auditor"]

    subgraph SystemBoundary["Backup & Disaster Recovery System"]
        UC01(["Configure Automated Backup Policy"])
        UC02(["Execute VM Snapshot Backup Job"])
        UC03(["Replicate Snapshot to Offsite Cloud Vault"])
        UC04(["Authenticate Admin Session"])
        UC05(["Execute One-Click Disaster Recovery Failover"])
        UC06(["Perform Point-in-Time Data Restore"])
        UC07(["Verify Backup Archive Integrity Checksum"])
        UC08(["Test Disaster Recovery Simulation Drills"])
        UC09(["Monitor Backup Storage Capacity & Retention"])
        UC10(["Configure Encryption-at-Rest Backup Keys"])
        UC11(["Trigger Emergency Outage Alert Dispatch"])
        UC12(["Manage Cloud Replication Bandwidth Throttling"])
        UC13(["Generate Recovery Time Objective RTO Reports"])
        UC14(["Export ISO 27001 Backup Audit Logs"])
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
| 1 | Disaster Recovery Administrator | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | System Administrator | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | Database Administrator | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | Security Auditor | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Configure Automated Backup Policy | Disaster Recovery Administrator | Supporting System | Handles configure automated backup policy operations within system boundary | High |
| 2 | UC02 | Execute VM Snapshot Backup Job | System Administrator | Supporting System | Handles execute vm snapshot backup job operations within system boundary | High |
| 3 | UC03 | Replicate Snapshot to Offsite Cloud Vault | Database Administrator | Supporting System | Handles replicate snapshot to offsite cloud vault operations within system boundary | High |
| 4 | UC04 | Authenticate Admin Session | Security Auditor | Supporting System | Handles authenticate admin session operations within system boundary | High |
| 5 | UC05 | Execute One-Click Disaster Recovery Failover | Disaster Recovery Administrator | Supporting System | Handles execute one-click disaster recovery failover operations within system boundary | High |
| 6 | UC06 | Perform Point-in-Time Data Restore | System Administrator | Supporting System | Handles perform point-in-time data restore operations within system boundary | High |
| 7 | UC07 | Verify Backup Archive Integrity Checksum | Database Administrator | Supporting System | Handles verify backup archive integrity checksum operations within system boundary | High |
| 8 | UC08 | Test Disaster Recovery Simulation Drills | Security Auditor | Supporting System | Handles test disaster recovery simulation drills operations within system boundary | Medium |
| 9 | UC09 | Monitor Backup Storage Capacity & Retention | Disaster Recovery Administrator | Supporting System | Handles monitor backup storage capacity & retention operations within system boundary | Medium |
| 10 | UC10 | Configure Encryption-at-Rest Backup Keys | System Administrator | Supporting System | Handles configure encryption-at-rest backup keys operations within system boundary | High |
| 11 | UC11 | Trigger Emergency Outage Alert Dispatch | Database Administrator | Supporting System | Handles trigger emergency outage alert dispatch operations within system boundary | High |
| 12 | UC12 | Manage Cloud Replication Bandwidth Throttling | Security Auditor | Supporting System | Handles manage cloud replication bandwidth throttling operations within system boundary | Medium |
| 13 | UC13 | Generate Recovery Time Objective RTO Reports | Disaster Recovery Administrator | Supporting System | Handles generate recovery time objective rto reports operations within system boundary | Medium |
| 14 | UC14 | Export ISO 27001 Backup Audit Logs | System Administrator | Supporting System | Handles export iso 27001 backup audit logs operations within system boundary | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Configure Automated Backup Policy

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Configure Automated Backup Policy |
| **Actor(s)** | Primary: Disaster Recovery Administrator |
| **Description** | Allows primary actors to configure and execute configure automated backup policy within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Execute One-Click Disaster Recovery Failover

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Execute One-Click Disaster Recovery Failover |
| **Actor(s)** | Primary: System Administrator |
| **Description** | Executes execute one-click disaster recovery failover with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Perform Point-in-Time Data Restore

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Perform Point-in-Time Data Restore |
| **Actor(s)** | Primary: Database Administrator |
| **Description** | Performs perform point-in-time data restore to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — Verify Backup Archive Integrity Checksum

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | Verify Backup Archive Integrity Checksum |
| **Actor(s)** | Primary: Database Administrator |
| **Description** | Manages verify backup archive integrity checksum to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Configure Encryption-at-Rest Backup Keys

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Configure Encryption-at-Rest Backup Keys |
| **Actor(s)** | Primary: Security Auditor |
| **Description** | Conducts configure encryption-at-rest backup keys for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
