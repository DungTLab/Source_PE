# Use Case Diagram — Multi-tenant SaaS Platform

## Mermaid Code

```mermaid
flowchart LR
    actor_Primary1["SaaS Platform Administrator"]
    actor_Primary2["Tenant Admin"]
    actor_Primary3["End User Customer"]
    actor_Primary4["Billing Specialist"]

    subgraph SystemBoundary["Multi-tenant SaaS Platform"]
        UC01(["Provision New SaaS Tenant Account"])
        UC02(["Configure Tenant Database Isolation"])
        UC03(["Manage Subscription Plans & Pricing"])
        UC04(["Authenticate Tenant User Session"])
        UC05(["Monitor Tenant Resource Consumption"])
        UC06(["Configure Custom Branding & Subdomains"])
        UC07(["Execute Automated Monthly Recurring Billing"])
        UC08(["Enforce Tenant Quota Rate Limits"])
        UC09(["Manage Tenant SSO & IdP Integration"])
        UC10(["Suspend Non-Payment Tenant Accounts"])
        UC11(["Execute Tenant Data Migration Export"])
        UC12(["Configure Feature Flag Toggles by Plan"])
        UC13(["Generate Monthly Recurring Revenue MRR Report"])
        UC14(["Export Multi-tenant Security Audit Trail"])
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
| 1 | SaaS Platform Administrator | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 2 | Tenant Admin | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 3 | End User Customer | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |
| 4 | Billing Specialist | Primary | Main actor responsible for system operations and oversight | UC01, UC02, UC05, UC10 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Provision New SaaS Tenant Account | SaaS Platform Administrator | Supporting System | Handles provision new saas tenant account operations within system boundary | High |
| 2 | UC02 | Configure Tenant Database Isolation | Tenant Admin | Supporting System | Handles configure tenant database isolation operations within system boundary | High |
| 3 | UC03 | Manage Subscription Plans & Pricing | End User Customer | Supporting System | Handles manage subscription plans & pricing operations within system boundary | High |
| 4 | UC04 | Authenticate Tenant User Session | Billing Specialist | Supporting System | Handles authenticate tenant user session operations within system boundary | High |
| 5 | UC05 | Monitor Tenant Resource Consumption | SaaS Platform Administrator | Supporting System | Handles monitor tenant resource consumption operations within system boundary | High |
| 6 | UC06 | Configure Custom Branding & Subdomains | Tenant Admin | Supporting System | Handles configure custom branding & subdomains operations within system boundary | Medium |
| 7 | UC07 | Execute Automated Monthly Recurring Billing | End User Customer | Supporting System | Handles execute automated monthly recurring billing operations within system boundary | High |
| 8 | UC08 | Enforce Tenant Quota Rate Limits | Billing Specialist | Supporting System | Handles enforce tenant quota rate limits operations within system boundary | High |
| 9 | UC09 | Manage Tenant SSO & IdP Integration | SaaS Platform Administrator | Supporting System | Handles manage tenant sso & idp integration operations within system boundary | High |
| 10 | UC10 | Suspend Non-Payment Tenant Accounts | Tenant Admin | Supporting System | Handles suspend non-payment tenant accounts operations within system boundary | High |
| 11 | UC11 | Execute Tenant Data Migration Export | End User Customer | Supporting System | Handles execute tenant data migration export operations within system boundary | Medium |
| 12 | UC12 | Configure Feature Flag Toggles by Plan | Billing Specialist | Supporting System | Handles configure feature flag toggles by plan operations within system boundary | Medium |
| 13 | UC13 | Generate Monthly Recurring Revenue MRR Report | SaaS Platform Administrator | Supporting System | Handles generate monthly recurring revenue mrr report operations within system boundary | Medium |
| 14 | UC14 | Export Multi-tenant Security Audit Trail | Tenant Admin | Supporting System | Handles export multi-tenant security audit trail operations within system boundary | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Provision New SaaS Tenant Account

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Provision New SaaS Tenant Account |
| **Actor(s)** | Primary: SaaS Platform Administrator |
| **Description** | Allows primary actors to configure and execute provision new saas tenant account within the system. |
| **Precondition** | 1. Actor must be authenticated. <br> 2. System must be in operational status. |
| **Main Flow** | 1. Actor accesses system module. <br> 2. System displays input form. <br> 3. Actor inputs required details. <br> 4. System validates parameters. <br> 5. Actor submits request. <br> 6. System saves record and updates status. |
| **Alternative Flow** | **AF1** — Bulk Operation: System processes input items in batch mode. <br> **AF2** — Template Loading: System auto-populates fields using preset template. |
| **Exception Flow** | **EX1** — Validation Error: System highlights missing mandatory fields. <br> **EX2** — System Timeout: System logs transaction and prompts retry. |
| **Postcondition** | Record is saved and audit trail entry is generated. |
| **Business Rule** | **BR1**: Operation requires valid administrative privileges. |

---

### UC05 — Monitor Tenant Resource Consumption

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Monitor Tenant Resource Consumption |
| **Actor(s)** | Primary: Tenant Admin |
| **Description** | Executes monitor tenant resource consumption with real-time feedback and validation. |
| **Precondition** | 1. User must have operational role. <br> 2. Target items must exist. |
| **Main Flow** | 1. User initiates operation. <br> 2. System retrieves target data. <br> 3. User verifies details. <br> 4. User confirms execution. <br> 5. System processes transaction. <br> 6. System returns success confirmation. |
| **Alternative Flow** | **AF1** — Automated Trigger: System executes operation automatically based on policy. |
| **Exception Flow** | **EX1** — Resource Locked: System alerts user if item is locked by another session. |
| **Postcondition** | Execution status is updated to completed. |
| **Business Rule** | **BR1**: All state changes must record timestamp and operator ID. |

---

### UC06 — Configure Custom Branding & Subdomains

| Field | Detail |
|-------|--------|
| **UC ID** | UC06 |
| **Use Case Name** | Configure Custom Branding & Subdomains |
| **Actor(s)** | Primary: End User Customer |
| **Description** | Performs configure custom branding & subdomains to ensure operational compliance and quality. |
| **Precondition** | 1. System policies must be active. |
| **Main Flow** | 1. User opens audit/monitoring view. <br> 2. System performs automated scan. <br> 3. System presents findings. <br> 4. User applies corrective action. <br> 5. System updates compliance status. <br> 6. System dispatches notification. |
| **Alternative Flow** | **AF1** — Auto-Remediation: System auto-corrects non-compliant items. |
| **Exception Flow** | **EX1** — Access Denied: System blocks unauthorized role access. |
| **Postcondition** | Compliance logs are updated. |
| **Business Rule** | **BR1**: Non-compliant items must generate high-priority alerts. |

---

### UC07 — Execute Automated Monthly Recurring Billing

| Field | Detail |
|-------|--------|
| **UC ID** | UC07 |
| **Use Case Name** | Execute Automated Monthly Recurring Billing |
| **Actor(s)** | Primary: End User Customer |
| **Description** | Manages execute automated monthly recurring billing to maintain system efficiency. |
| **Precondition** | 1. Threshold rules must be defined. |
| **Main Flow** | 1. System detects threshold event. <br> 2. System alerts user. <br> 3. User reviews event parameters. <br> 4. User confirms action. <br> 5. System executes update. <br> 6. System logs outcome. |
| **Alternative Flow** | **AF1** — Scheduled Task: System executes task at off-peak hours. |
| **Exception Flow** | **EX1** — Integration Fail: System retries external API connection. |
| **Postcondition** | Metric trends are updated. |
| **Business Rule** | **BR1**: Critical metrics require immediate notification. |

---

### UC10 — Suspend Non-Payment Tenant Accounts

| Field | Detail |
|-------|--------|
| **UC ID** | UC10 |
| **Use Case Name** | Suspend Non-Payment Tenant Accounts |
| **Actor(s)** | Primary: Billing Specialist |
| **Description** | Conducts suspend non-payment tenant accounts for governance and security audits. |
| **Precondition** | 1. Audit rules must be pre-configured. |
| **Main Flow** | 1. Auditor opens governance portal. <br> 2. System compiles audit report. <br> 3. Auditor reviews compliance score. <br> 4. Auditor exports documentation. <br> 5. System logs audit event. <br> 6. System updates compliance status. |
| **Alternative Flow** | **AF1** — Automated Export: System dispatches weekly audit summary email. |
| **Exception Flow** | **EX1** — Data Gap Warning: System flags unverified data points. |
| **Postcondition** | Audit compliance record is finalized. |
| **Business Rule** | **BR1**: Audit records are immutable after publication. |
