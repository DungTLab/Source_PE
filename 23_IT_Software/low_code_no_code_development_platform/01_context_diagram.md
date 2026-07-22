# Context Diagram — Low-Code / No-Code Development Platform

## Mermaid Code

```mermaid
flowchart LR
    CitizenDeveloper["Citizen Developer"]
    EnterpriseITAdmin["Enterprise IT Admin"]
    BusinessEndUser["Business End User"]
    SecurityAuditor["Security Auditor"]

    PostgreSQLDatabaseGateway["PostgreSQL / Database Gateway"]
    RESTAPIConnector["REST API Connector"]
    ActiveDirectoryLDAP["Active Directory LDAP"]
    MobileAppBuilderEngine["Mobile App Builder Engine"]
    AuditPortal["Audit Portal"]

    SystemNode(("Low-Code / No-Code Development Platform"))

    CitizenDeveloper -->|"submits management requests & policies"| SystemNode
    SystemNode -->|"returns system status & analytics reports"| CitizenDeveloper

    EnterpriseITAdmin -->|"interacts with self-service operations"| SystemNode
    SystemNode -->|"provides real-time processing results"| EnterpriseITAdmin

    BusinessEndUser -->|"configures operational rules & data"| SystemNode
    SystemNode -->|"returns execution logs & alerts"| BusinessEndUser

    SecurityAuditor -->|"audits compliance & security logs"| SystemNode
    SystemNode -->|"exports compliance audit records"| SecurityAuditor

    PostgreSQLDatabaseGateway -->|"provides integration payloads & telemetry"| SystemNode
    SystemNode -->|"dispatches API requests & sync events"| PostgreSQLDatabaseGateway

    RESTAPIConnector -->|"authenticates user credentials"| SystemNode
    SystemNode -->|"queries identity & role memberships"| RESTAPIConnector

    SystemNode -->|"exports financial & inventory data"| ActiveDirectoryLDAP
    SystemNode -->|"triggers emergency alert notifications"| MobileAppBuilderEngine
    SystemNode -->|"streams audit events & compliance data"| AuditPortal
```

## Actor & Interaction Table | Bảng Actor & Tương tác

| # | Actor | Actor Type | Data Sent TO System | Data Received FROM System | Notes |
|---|-------|------------|---------------------|---------------------------|-------|
| 1 | Citizen Developer | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Citizen Developer role |
| 2 | Enterprise IT Admin | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Enterprise IT Admin role |
| 3 | Business End User | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Business End User role |
| 4 | Security Auditor | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Security Auditor role |
| 5 | PostgreSQL / Database Gateway | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | PostgreSQL / Database Gateway role |
| 6 | REST API Connector | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | REST API Connector role |
| 7 | Active Directory LDAP | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Active Directory LDAP role |
| 8 | Mobile App Builder Engine | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Mobile App Builder Engine role |
| 9 | Audit Portal | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Audit Portal role |

## System Boundary Description | Mô tả Scope Hệ thống

Hệ thống **Low-Code / No-Code Development Platform** (Nền tảng Phát triển Low-Code / No-Code) được thiết kế nhằm quản lý tập trung và tự động hóa các quy trình vận hành CNTT cốt lõi trong doanh nghiệp.

- **Phạm vi bên trong hệ thống (In-Scope)**:
  - Quản lý dữ liệu nghiệp vụ trung tâm, tự động hóa quy trình theo chính sách doanh nghiệp.
  - Phân quyền người dùng chi tiết, theo dõi lịch sử thao tác và xuất báo cáo tuân thủ (ISO/SOC2).
  - Tích hợp phát hiện sự cố, gửi cảnh báo tức thì và kết nối dữ liệu hai chiều.

- **Bên ngoài phạm vi hệ thống (Out-of-Scope)**:
  - Trực tiếp quản lý hạ tầng phần cứng máy chủ vật lý.
  - Trực tiếp xử lý xác thực mật khẩu người dùng gốc (do Identity Provider đảm nhận).
