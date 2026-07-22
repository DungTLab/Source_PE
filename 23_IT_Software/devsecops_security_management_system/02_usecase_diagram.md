# Use Case Diagram — DevSecOps Security Management System

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["DevSecOps Engineer"]
    actor_Primary2["Security Architect"]
    actor_Primary3["Software Developer"]
    actor_Primary4["Compliance Auditor"]

    subgraph SystemBoundary["DevSecOps Security Management System"]
        UC01(["Configure DevSecOps Pipeline Security Gate"])
        UC02(["Execute SAST Static Code Analysis"])
        UC03(["Scan SCA Dependency Vulnerabilities"])
        UC04(["Authenticate Security Engineer Session"])
        UC05(["Detect Hardcoded Secrets in Code"])
        UC06(["Generate Software Bill of Materials SBOM"])
        UC07(["Manage Vulnerability Exemption Whitelist"])
        UC08(["Scan DAST Dynamic Application Attack"])
        UC09(["Track Vulnerability Remediation SLAs"])
        UC10(["Block PR Merge on Critical Security Flaw"])
        UC11(["Analyze Open Source License Risks"])
        UC12(["Configure Container Security Policies"])
        UC13(["Generate Application Security Posture Score"])
        UC14(["Export Executive DevSecOps Audit Logs"])
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
| 1 | DevSecOps Engineer | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | Security Architect | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | Software Developer | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | Compliance Auditor | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Configure DevSecOps Pipeline Security Gate | DevSecOps Engineer | Supporting System | Handles configure devsecops pipeline security gate operations within system boundary | High |
| 2 | UC02 | Execute SAST Static Code Analysis | Security Architect | Supporting System | Handles execute sast static code analysis operations within system boundary | High |
| 3 | UC03 | Scan SCA Dependency Vulnerabilities | Software Developer | Supporting System | Handles scan sca dependency vulnerabilities operations within system boundary | High |
| 4 | UC04 | Authenticate Security Engineer Session | Compliance Auditor | Supporting System | Handles authenticate security engineer session operations within system boundary | High |
| 5 | UC05 | Detect Hardcoded Secrets in Code | DevSecOps Engineer | Supporting System | Handles detect hardcoded secrets in code operations within system boundary | High |
| 6 | UC06 | Generate Software Bill of Materials SBOM | Security Architect | Supporting System | Handles generate software bill of materials sbom operations within system boundary | High |
| 7 | UC07 | Manage Vulnerability Exemption Whitelist | Software Developer | Supporting System | Handles manage vulnerability exemption whitelist operations within system boundary | Medium |
| 8 | UC08 | Scan DAST Dynamic Application Attack | Compliance Auditor | Supporting System | Handles scan dast dynamic application attack operations within system boundary | High |
| 9 | UC09 | Track Vulnerability Remediation SLAs | DevSecOps Engineer | Supporting System | Handles track vulnerability remediation slas operations within system boundary | High |
| 10 | UC10 | Block PR Merge on Critical Security Flaw | Security Architect | Supporting System | Handles block pr merge on critical security flaw operations within system boundary | High |
| 11 | UC11 | Analyze Open Source License Risks | Software Developer | Supporting System | Handles analyze open source license risks operations within system boundary | Medium |
| 12 | UC12 | Configure Container Security Policies | Compliance Auditor | Supporting System | Handles configure container security policies operations within system boundary | Medium |
| 13 | UC13 | Generate Application Security Posture Score | DevSecOps Engineer | Supporting System | Handles generate application security posture score operations within system boundary | Medium |
| 14 | UC14 | Export Executive DevSecOps Audit Logs | Security Architect | Supporting System | Handles export executive devsecops audit logs operations within system boundary | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Configure DevSecOps Pipeline Security Gate

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Configure DevSecOps Pipeline Security Gate |
| **Actor(s)** | Primary: DevSecOps Engineer |
| **Description** | Allows primary actors to configure and execute configure devsecops pipeline security gate within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Detect Hardcoded Secrets in Code

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Detect Hardcoded Secrets in Code |
| **Actor(s)** | Primary: Security Architect |
| **Description** | Executes detect hardcoded secrets in code with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Generate Software Bill of Materials SBOM

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Generate Software Bill of Materials SBOM |
| **Actor(s)** | Primary: Software Developer |
| **Description** | Performs generate software bill of materials sbom to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — Manage Vulnerability Exemption Whitelist

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | Manage Vulnerability Exemption Whitelist |
| **Actor(s)** | Primary: Software Developer |
| **Description** | Manages manage vulnerability exemption whitelist to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Block PR Merge on Critical Security Flaw

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Block PR Merge on Critical Security Flaw |
| **Actor(s)** | Primary: Compliance Auditor |
| **Description** | Conducts block pr merge on critical security flaw for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
