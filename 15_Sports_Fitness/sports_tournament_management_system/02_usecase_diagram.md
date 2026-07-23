# Use Case Diagram — Sports Tournament Management System

## Mermaid Code

```mermaid
flowchart LR
    actor_PrimaryUser["Sports Tournament User"]
    actor_DomainAdmin["Sports Tournament Administrator"]
    actor_StaffManager["Operational Manager"]
    actor_FieldOfficial["Field Official / Inspector"]
    actor_PaymentGateway["Payment Gateway API"]
    actor_NotificationAPI["Notification & SMS Gateway"]
    actor_TelemetryGateway["IoT Telemetry Gateway"]
    actor_RegulatoryPortal["Sports Federation Audit Portal"]

    subgraph SystemBoundary["Sports Tournament Management System"]
        UC01(["Register Sports Tournament Account"])
        UC02(["Manage Sports Tournament Configuration"])
        UC03(["Schedule Sports Tournament Event"])
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
| 1 | Sports Tournament User | Primary | Primary domain user | UC01, UC04, UC13 |
| 2 | Sports Tournament Administrator | Primary | System administrator | UC02, UC08, UC10, UC14 |
| 3 | Operational Manager | Primary | Operations lead | UC03, UC09, UC11 |
| 4 | Field Official / Inspector | Primary | On-site officer | UC05, UC12 |
| 5 | Payment Gateway API | Supporting | Financial gateway | UC01, UC02 |
| 6 | Notification & SMS Gateway | Supporting | Messaging integration | UC06 |
| 7 | IoT Telemetry Gateway | Supporting | Hardware/IoT integration | UC07 |
| 8 | Sports Federation Audit Portal | Regulatory | Regulatory compliance portal | UC01, UC02 |


## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Register Sports Tournament Account | Sports Tournament User | Payment Gateway API | Allows users to register and setup sports tournament profiles. | High |
| 2 | UC02 | Manage Sports Tournament Configuration | Sports Tournament Administrator | None | Configures core parameters and rules for sports tournament. | High |
| 3 | UC03 | Schedule Sports Tournament Event | Operational Manager | Field Official / Inspector | Schedules timelines, matches, or operational events. | High |
| 4 | UC04 | Process Payment Transaction | Sports Tournament User | Payment Gateway API | Executes online fee payments, deposits, or subscriptions. | High |
| 5 | UC05 | Log Field Inspection Data | Field Official / Inspector | Operational Manager | Records live metrics, match results, or inspection check-lists. | Medium |
| 6 | UC06 | Send Automated Notifications | Notification & SMS Gateway | Sports Tournament User | Broadcasts system updates, schedule changes, and reminders. | Low |
| 7 | UC07 | Ingest IoT Sensor Telemetry | IoT Telemetry Gateway | Sports Tournament Administrator | Processes stream data from sensors, wearables, or gate scanners. | Medium |
| 8 | UC08 | Generate Compliance Audit | Sports Tournament Administrator | Sports Federation Audit Portal | Exports standardized regulatory compliance reports. | High |
| 9 | UC09 | Verify User Eligibility | Operational Manager | Sports Tournament User | Checks credentials, medical clearances, or membership status. | Medium |
| 10 | UC10 | Export Performance Analytics | Sports Tournament Administrator | None | Generates statistical trends, revenue charts, and operational dashboards. | High |
| 11 | UC11 | Manage Resource Allocation | Operational Manager | None | Assigns venues, equipment, or staff to active events. | Medium |
| 12 | UC12 | Handle Incident Report | Field Official / Inspector | Sports Tournament Administrator | Logs safety infractions, equipment failures, or participant disputes. | Medium |
| 13 | UC13 | Update User Profile | Sports Tournament User | None | Updates contact info, preferences, and emergency details. | Low |
| 14 | UC14 | Archive Historical Records | Sports Tournament Administrator | Sports Federation Audit Portal | Stores completed event logs and participant history for long-term audit. | Low |


## Use Case Specification | Đặc tả Use Case

### UC01 — Register Sports Tournament Account

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Register Sports Tournament Account |
| **Actor(s)** | Primary: Sports Tournament User / Secondary: Payment Gateway API |
| **Description** | Allows users to register and setup sports tournament profiles. |
| **Precondition** | 1. User is authenticated with appropriate role permissions.<br>2. System network connection and target database service are fully active. |
| **Main Flow** | 1. Sports Tournament User initiates Register Sports Tournament Account request via the system dashboard.<br>2. System validates input data parameters and displays confirmation screen.<br>3. Sports Tournament User reviews details and submits final transaction.<br>4. System processes payload and communicates with Payment Gateway API.<br>5. Payment Gateway API returns authorization code and transaction status.<br>6. System updates internal record and returns success notification to Sports Tournament User. |
| **Alternative Flow** | **AF1** — Saved Draft Flow: If user chooses save draft, system stores state without submitting.<br>**AF2** — Fast-track Flow: If user holds VIP badge, system bypasses standard queue validation. |
| **Exception Flow** | **EX1** — Network Timeout: If secondary system fails to respond within 10 seconds, system displays retry prompt.<br>**EX2** — Validation Error: If input fields contain invalid format, system highlights error fields. |
| **Postcondition** | Target transaction state is saved into DB and confirmation log is recorded. |
| **Business Rule** | **BR1**: All transactions must be encrypted using AES-256.<br>**BR2**: Logs must be archived for audit compliance. |

---

### UC02 — Manage Sports Tournament Configuration

| Field | Detail |
|-------|--------|
| **UC ID** | UC02 |
| **Use Case Name** | Manage Sports Tournament Configuration |
| **Actor(s)** | Primary: Sports Tournament Administrator / Secondary: None |
| **Description** | Configures core parameters and rules for sports tournament. |
| **Precondition** | 1. User is authenticated with appropriate role permissions.<br>2. System network connection and target database service are fully active. |
| **Main Flow** | 1. Sports Tournament Administrator initiates Manage Sports Tournament Configuration request via the system dashboard.<br>2. System validates input data parameters and displays confirmation screen.<br>3. Sports Tournament Administrator reviews details and submits final transaction.<br>4. System processes payload and communicates with None.<br>5. None returns authorization code and transaction status.<br>6. System updates internal record and returns success notification to Sports Tournament Administrator. |
| **Alternative Flow** | **AF1** — Saved Draft Flow: If user chooses save draft, system stores state without submitting.<br>**AF2** — Fast-track Flow: If user holds VIP badge, system bypasses standard queue validation. |
| **Exception Flow** | **EX1** — Network Timeout: If secondary system fails to respond within 10 seconds, system displays retry prompt.<br>**EX2** — Validation Error: If input fields contain invalid format, system highlights error fields. |
| **Postcondition** | Target transaction state is saved into DB and confirmation log is recorded. |
| **Business Rule** | **BR1**: All transactions must be encrypted using AES-256.<br>**BR2**: Logs must be archived for audit compliance. |

---

### UC03 — Schedule Sports Tournament Event

| Field | Detail |
|-------|--------|
| **UC ID** | UC03 |
| **Use Case Name** | Schedule Sports Tournament Event |
| **Actor(s)** | Primary: Operational Manager / Secondary: Field Official / Inspector |
| **Description** | Schedules timelines, matches, or operational events. |
| **Precondition** | 1. User is authenticated with appropriate role permissions.<br>2. System network connection and target database service are fully active. |
| **Main Flow** | 1. Operational Manager initiates Schedule Sports Tournament Event request via the system dashboard.<br>2. System validates input data parameters and displays confirmation screen.<br>3. Operational Manager reviews details and submits final transaction.<br>4. System processes payload and communicates with Field Official / Inspector.<br>5. Field Official / Inspector returns authorization code and transaction status.<br>6. System updates internal record and returns success notification to Operational Manager. |
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
| **Actor(s)** | Primary: Sports Tournament User / Secondary: Payment Gateway API |
| **Description** | Executes online fee payments, deposits, or subscriptions. |
| **Precondition** | 1. User is authenticated with appropriate role permissions.<br>2. System network connection and target database service are fully active. |
| **Main Flow** | 1. Sports Tournament User initiates Process Payment Transaction request via the system dashboard.<br>2. System validates input data parameters and displays confirmation screen.<br>3. Sports Tournament User reviews details and submits final transaction.<br>4. System processes payload and communicates with Payment Gateway API.<br>5. Payment Gateway API returns authorization code and transaction status.<br>6. System updates internal record and returns success notification to Sports Tournament User. |
| **Alternative Flow** | **AF1** — Saved Draft Flow: If user chooses save draft, system stores state without submitting.<br>**AF2** — Fast-track Flow: If user holds VIP badge, system bypasses standard queue validation. |
| **Exception Flow** | **EX1** — Network Timeout: If secondary system fails to respond within 10 seconds, system displays retry prompt.<br>**EX2** — Validation Error: If input fields contain invalid format, system highlights error fields. |
| **Postcondition** | Target transaction state is saved into DB and confirmation log is recorded. |
| **Business Rule** | **BR1**: All transactions must be encrypted using AES-256.<br>**BR2**: Logs must be archived for audit compliance. |

---

