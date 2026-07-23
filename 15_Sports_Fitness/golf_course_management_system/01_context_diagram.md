# Context Diagram — Golf Course Management System

## Mermaid Code

```mermaid
flowchart LR
    PrimaryUser["Golf Course User"]
    DomainAdmin["Golf Course Administrator"]
    StaffManager["Operational Manager"]
    FieldOfficial["Field Official / Inspector"]
    PaymentGateway["Payment Gateway API"]
    NotificationAPI["Notification & SMS Gateway"]
    TelemetryGateway["IoT Telemetry Gateway"]
    RegulatoryPortal["Sports Federation Audit Portal"]
    System(("Golf Course Management System"))

    PrimaryUser -->|"Submits golf course requests"| System
    System -->|"Receives golf course status"| PrimaryUser
    DomainAdmin -->|"Configures golf course settings"| System
    System -->|"Receives audit logs"| DomainAdmin
    StaffManager -->|"Assigns tasks"| System
    System -->|"Receives operational alerts"| StaffManager
    FieldOfficial -->|"Inputs match results"| System
    System -->|"Receives schedule assignments"| FieldOfficial
    PaymentGateway -->|"Processes transaction payments and refunds"| System
    System -->|"Returns payment authorization receipts"| PaymentGateway
    NotificationAPI -->|"Dispatches automated alerts and reminders"| System
    System -->|"Returns delivery notification status"| NotificationAPI
    TelemetryGateway -->|"Transmits sensor and device data logs"| System
    System -->|"Receives telemetry processing confirmation"| TelemetryGateway
    RegulatoryPortal -->|"Requests compliance data and tournament logs"| System
    System -->|"Receives official audit reports"| RegulatoryPortal
```

## Actor & Interaction Table | Bảng Actor & Tương tác

| # | Actor | Actor Type | Data Sent TO System | Data Received FROM System | Notes |
|---|-------|------------|---------------------|---------------------------|-------|
| 1 | Golf Course User | Primary | Submits golf course requests, updates profile | Receives golf course status, confirmation | Primary domain user |
| 2 | Golf Course Administrator | Primary | Configures golf course settings, manages permissions | Receives audit logs, system performance metrics | System administrator |
| 3 | Operational Manager | Primary | Assigns tasks, manages schedules, reviews reports | Receives operational alerts, user feedback | Operations lead |
| 4 | Field Official / Inspector | Primary | Inputs match results, logs field inspections | Receives schedule assignments, guidelines | On-site officer |
| 5 | Payment Gateway API | Supporting | Processes transaction payments and refunds | Returns payment authorization receipts | Financial gateway |
| 6 | Notification & SMS Gateway | Supporting | Dispatches automated alerts and reminders | Returns delivery notification status | Messaging integration |
| 7 | IoT Telemetry Gateway | Supporting | Transmits sensor and device data logs | Receives telemetry processing confirmation | Hardware/IoT integration |
| 8 | Sports Federation Audit Portal | Regulatory | Requests compliance data and tournament logs | Receives official audit reports | Regulatory compliance portal |


## System Boundary Description | Mô tả Scope Hệ thống

The Golf Course Management System provides an end-to-end digital ecosystem designed specifically to automate and optimize operational workflows for Hệ Thống Quản Lý Sân Golf. The system boundary includes core module capabilities such as user registrations, event/session scheduling, data processing, resource allocation, and automated reporting. External integrations with payment gateways, messaging networks, IoT sensor hardware, and regulatory audit portals operate outside the core application server but maintain secure API interactions. Manual paper-based logs and unintegrated external physical facilities remain outside the system boundary. overall system enforces strict role-based access control (RBAC) and encryption to safeguard data privacy.
