# Use Case Diagram — Wearable Fitness Data Analytics System

## Mermaid Code

```mermaid
flowchart LR
    actor_PrimaryUser["Wearable Fitness Data Analytics User"]
    actor_DomainAdmin["Wearable Fitness Data Analytics Administrator"]
    actor_StaffManager["Operational Manager"]
    actor_FieldOfficial["Field Official / Inspector"]
    actor_PaymentGateway["Payment Gateway API"]
    actor_NotificationAPI["Notification & SMS Gateway"]
    actor_TelemetryGateway["IoT Telemetry Gateway"]
    actor_RegulatoryPortal["Sports Federation Audit Portal"]

    subgraph SystemBoundary["Wearable Fitness Data Analytics System"]
        UC01(["Register Wearable Fitness Data Analytics Account"])
        UC02(["Manage Wearable Fitness Data Analytics Configuration"])
        UC03(["Schedule Wearable Fitness Data Analytics Event"])
        UC04(["Process Payment Transaction"])
        UC05(["Log Field Inspection Data"])
        UC06(["Send Automated Notifications"])
        UC07(["Ingest IoT Sensor Telemetry"])
        UC08(["Generate Compliance Audit"])
        UC09(["Verify User Eligibility"])
        UC10(["Export Performance Analytics"])
        UC11(["Manage Resource Allocation"])
        UC12(["Handle Incident Report"])
        UC13(["Update User Profile"])
        UC14(["Archive Historical Records"])
    end

    actor_PrimaryUser --> UC01
    actor_DomainAdmin --> UC02
    actor_StaffManager --> UC03
    actor_PrimaryUser --> UC04
    actor_FieldOfficial --> UC05
    actor_NotificationAPI --> UC06
    actor_TelemetryGateway --> UC07
    actor_DomainAdmin --> UC08
    actor_StaffManager --> UC09
    actor_DomainAdmin --> UC10
    actor_StaffManager --> UC11
    actor_FieldOfficial --> UC12
    actor_PrimaryUser --> UC13
    actor_DomainAdmin --> UC14
    UC01 -.->|"<<include>>"| UC04
    UC03 -.->|"<<extend>>"| UC06
```

## Actor Table | Bảng Actor

| # | Actor | Actor Type | Role Description | Related Use Cases |
|---|-------|------------|------------------|-------------------|
| 1 | Wearable Fitness Data Analytics User | Primary | Primary domain user | UC01, UC04, UC13 |
| 2 | Wearable Fitness Data Analytics Administrator | Primary | System administrator | UC02, UC08, UC10, UC14 |
| 3 | Operational Manager | Primary | Operations lead | UC03, UC09, UC11 |
| 4 | Field Official / Inspector | Primary | On-site officer | UC05, UC12 |
| 5 | Payment Gateway API | Supporting | Financial gateway | UC01, UC02 |
| 6 | Notification & SMS Gateway | Supporting | Messaging integration | UC06 |
| 7 | IoT Telemetry Gateway | Supporting | Hardware/IoT integration | UC07 |
| 8 | Sports Federation Audit Portal | Regulatory | Regulatory compliance portal | UC01, UC02 |


## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Register Wearable Fitness Data Analytics Account | Wearable Fitness Data Analytics User | Payment Gateway API | Allows users to register and setup wearable fitness data analytics profiles. | High |
| 2 | UC02 | Manage Wearable Fitness Data Analytics Configuration | Wearable Fitness Data Analytics Administrator | None | Configures core parameters and rules for wearable fitness data analytics. | High |
| 3 | UC03 | Schedule Wearable Fitness Data Analytics Event | Operational Manager | Field Official / Inspector | Schedules timelines, matches, or operational events. | High |
| 4 | UC04 | Process Payment Transaction | Wearable Fitness Data Analytics User | Payment Gateway API | Executes online fee payments, deposits, or subscriptions. | High |
| 5 | UC05 | Log Field Inspection Data | Field Official / Inspector | Operational Manager | Records live metrics, match results, or inspection check-lists. | Medium |
| 6 | UC06 | Send Automated Notifications | Notification & SMS Gateway | Wearable Fitness Data Analytics User | Broadcasts system updates, schedule changes, and reminders. | Low |
| 7 | UC07 | Ingest IoT Sensor Telemetry | IoT Telemetry Gateway | Wearable Fitness Data Analytics Administrator | Processes stream data from sensors, wearables, or gate scanners. | Medium |
| 8 | UC08 | Generate Compliance Audit | Wearable Fitness Data Analytics Administrator | Sports Federation Audit Portal | Exports standardized regulatory compliance reports. | High |
| 9 | UC09 | Verify User Eligibility | Operational Manager | Wearable Fitness Data Analytics User | Checks credentials, medical clearances, or membership status. | Medium |
| 10 | UC10 | Export Performance Analytics | Wearable Fitness Data Analytics Administrator | None | Generates statistical trends, revenue charts, and operational dashboards. | High |
| 11 | UC11 | Manage Resource Allocation | Operational Manager | None | Assigns venues, equipment, or staff to active events. | Medium |
| 12 | UC12 | Handle Incident Report | Field Official / Inspector | Wearable Fitness Data Analytics Administrator | Logs safety infractions, equipment failures, or participant disputes. | Medium |
| 13 | UC13 | Update User Profile | Wearable Fitness Data Analytics User | None | Updates contact info, preferences, and emergency details. | Low |
| 14 | UC14 | Archive Historical Records | Wearable Fitness Data Analytics Administrator | Sports Federation Audit Portal | Stores completed event logs and participant history for long-term audit. | Low |


## Use Case Specification | Đặc tả Use Case

### UC01 — Register Wearable Fitness Data Analytics Account

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Register Wearable Fitness Data Analytics Account |
| **Actor(s)** | Primary: Wearable Fitness Data Analytics User / Secondary: Payment Gateway API |
| **Description** | Allows users to register and setup wearable fitness data analytics profiles. |
| **Precondition** | 1. User is authenticated with appropriate role permissions.<br>2. System network connection and target database service are fully active. |
| **Main Flow** | 1. Wearable Fitness Data Analytics User initiates Register Wearable Fitness Data Analytics Account request via the system dashboard.<br>2. System validates input data parameters and displays confirmation screen.<br>3. Wearable Fitness Data Analytics User reviews details and submits final transaction.<br>4. System processes payload and communicates with Payment Gateway API.<br>5. Payment Gateway API returns authorization code and transaction status.<br>6. System updates internal record and returns success notification to Wearable Fitness Data Analytics User. |
| **Alternative Flow** | **AF1** — Saved Draft Flow: If user chooses save draft, system stores state without submitting.<br>**AF2** — Fast-track Flow: If user holds VIP badge, system bypasses standard queue validation. |
| **Exception Flow** | **EX1** — Network Timeout: If secondary system fails to respond within 10 seconds, system displays retry prompt.<br>**EX2** — Validation Error: If input fields contain invalid format, system highlights error fields. |
| **Postcondition** | Target transaction state is saved into DB and confirmation log is recorded. |
| **Business Rule** | **BR1**: All transactions must be encrypted using AES-256.<br>**BR2**: Logs must be archived for audit compliance. |

---

### UC02 — Manage Wearable Fitness Data Analytics Configuration

| Field | Detail |
|-------|--------|
| **UC ID** | UC02 |
| **Use Case Name** | Manage Wearable Fitness Data Analytics Configuration |
| **Actor(s)** | Primary: Wearable Fitness Data Analytics Administrator / Secondary: None |
| **Description** | Configures core parameters and rules for wearable fitness data analytics. |
| **Precondition** | 1. User is authenticated with appropriate role permissions.<br>2. System network connection and target database service are fully active. |
| **Main Flow** | 1. Wearable Fitness Data Analytics Administrator initiates Manage Wearable Fitness Data Analytics Configuration request via the system dashboard.<br>2. System validates input data parameters and displays confirmation screen.<br>3. Wearable Fitness Data Analytics Administrator reviews details and submits final transaction.<br>4. System processes payload and communicates with None.<br>5. None returns authorization code and transaction status.<br>6. System updates internal record and returns success notification to Wearable Fitness Data Analytics Administrator. |
| **Alternative Flow** | **AF1** — Saved Draft Flow: If user chooses save draft, system stores state without submitting.<br>**AF2** — Fast-track Flow: If user holds VIP badge, system bypasses standard queue validation. |
| **Exception Flow** | **EX1** — Network Timeout: If secondary system fails to respond within 10 seconds, system displays retry prompt.<br>**EX2** — Validation Error: If input fields contain invalid format, system highlights error fields. |
| **Postcondition** | Target transaction state is saved into DB and confirmation log is recorded. |
| **Business Rule** | **BR1**: All transactions must be encrypted using AES-256.<br>**BR2**: Logs must be archived for audit compliance. |

---

### UC03 — Schedule Wearable Fitness Data Analytics Event

| Field | Detail |
|-------|--------|
| **UC ID** | UC03 |
| **Use Case Name** | Schedule Wearable Fitness Data Analytics Event |
| **Actor(s)** | Primary: Operational Manager / Secondary: Field Official / Inspector |
| **Description** | Schedules timelines, matches, or operational events. |
| **Precondition** | 1. User is authenticated with appropriate role permissions.<br>2. System network connection and target database service are fully active. |
| **Main Flow** | 1. Operational Manager initiates Schedule Wearable Fitness Data Analytics Event request via the system dashboard.<br>2. System validates input data parameters and displays confirmation screen.<br>3. Operational Manager reviews details and submits final transaction.<br>4. System processes payload and communicates with Field Official / Inspector.<br>5. Field Official / Inspector returns authorization code and transaction status.<br>6. System updates internal record and returns success notification to Operational Manager. |
| **Alternative Flow** | **AF1** — Saved Draft Flow: If user chooses save draft, system stores state without submitting.<br>**AF2** — Fast-track Flow: If user holds VIP badge, system bypasses standard queue validation. |
| **Exception Flow** | **EX1** — Network Timeout: If secondary system fails to respond within 10 seconds, system displays retry prompt.<br>**EX2** — Validation Error: If input fields contain invalid format, system highlights error fields. |
| **Postcondition** | Target transaction state is saved into DB and confirmation log is recorded. |
| **Business Rule** | **BR1**: All transactions must be encrypted using AES-256.<br>**BR2**: Logs must be archived for audit compliance. |

---

### UC04 — Process Payment Transaction

| Field | Detail |
|-------|--------|
| **UC ID** | UC04 |
| **Use Case Name** | Process Payment Transaction |
| **Actor(s)** | Primary: Wearable Fitness Data Analytics User / Secondary: Payment Gateway API |
| **Description** | Executes online fee payments, deposits, or subscriptions. |
| **Precondition** | 1. User is authenticated with appropriate role permissions.<br>2. System network connection and target database service are fully active. |
| **Main Flow** | 1. Wearable Fitness Data Analytics User initiates Process Payment Transaction request via the system dashboard.<br>2. System validates input data parameters and displays confirmation screen.<br>3. Wearable Fitness Data Analytics User reviews details and submits final transaction.<br>4. System processes payload and communicates with Payment Gateway API.<br>5. Payment Gateway API returns authorization code and transaction status.<br>6. System updates internal record and returns success notification to Wearable Fitness Data Analytics User. |
| **Alternative Flow** | **AF1** — Saved Draft Flow: If user chooses save draft, system stores state without submitting.<br>**AF2** — Fast-track Flow: If user holds VIP badge, system bypasses standard queue validation. |
| **Exception Flow** | **EX1** — Network Timeout: If secondary system fails to respond within 10 seconds, system displays retry prompt.<br>**EX2** — Validation Error: If input fields contain invalid format, system highlights error fields. |
| **Postcondition** | Target transaction state is saved into DB and confirmation log is recorded. |
| **Business Rule** | **BR1**: All transactions must be encrypted using AES-256.<br>**BR2**: Logs must be archived for audit compliance. |

---

