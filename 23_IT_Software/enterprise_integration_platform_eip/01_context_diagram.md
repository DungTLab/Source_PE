# Context Diagram — Enterprise Integration Platform (EIP)

## Mermaid Code

```mermaid
flowchart LR
    IntegrationArchitect["Integration Architect"]
    EnterpriseDeveloper["Enterprise Developer"]
    SystemAdministrator["System Administrator"]
    SecurityAuditor["Security Auditor"]

    ApacheCamelEngine["Apache Camel Engine"]
    EnterpriseERPSystem["Enterprise ERP System"]
    ActiveDirectoryLDAP["Active Directory LDAP"]
    KafkaMessageBroker["Kafka Message Broker"]
    SIEMSecurityPortal["SIEM Security Portal"]

    SystemNode(("Enterprise Integration Platform (EIP)"))

    IntegrationArchitect -->|"submits management requests & policies"| SystemNode
    SystemNode -->|"returns system status & analytics reports"| IntegrationArchitect

    EnterpriseDeveloper -->|"interacts with self-service operations"| SystemNode
    SystemNode -->|"provides real-time processing results"| EnterpriseDeveloper

    SystemAdministrator -->|"configures operational rules & data"| SystemNode
    SystemNode -->|"returns execution logs & alerts"| SystemAdministrator

    SecurityAuditor -->|"audits compliance & security logs"| SystemNode
    SystemNode -->|"exports compliance audit records"| SecurityAuditor

    ApacheCamelEngine -->|"provides integration payloads & telemetry"| SystemNode
    SystemNode -->|"dispatches API requests & sync events"| ApacheCamelEngine

    EnterpriseERPSystem -->|"authenticates user credentials"| SystemNode
    SystemNode -->|"queries identity & role memberships"| EnterpriseERPSystem

    SystemNode -->|"exports financial & inventory data"| ActiveDirectoryLDAP
    SystemNode -->|"triggers emergency alert notifications"| KafkaMessageBroker
    SystemNode -->|"streams audit events & compliance data"| SIEMSecurityPortal
```

## Actor & Interaction Table | Bảng Actor & Tương tác

| # | Actor | Actor Type | Data Sent TO System | Data Received FROM System | Notes |
|---|-------|------------|---------------------|---------------------------|-------|
| 1 | Integration Architect | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Integration Architect role |
| 2 | Enterprise Developer | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Enterprise Developer role |
| 3 | System Administrator | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | System Administrator role |
| 4 | Security Auditor | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Security Auditor role |
| 5 | Apache Camel Engine | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Apache Camel Engine role |
| 6 | Enterprise ERP System | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Enterprise ERP System role |
| 7 | Active Directory LDAP | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Active Directory LDAP role |
| 8 | Kafka Message Broker | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Kafka Message Broker role |
| 9 | SIEM Security Portal | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | SIEM Security Portal role |

## System Boundary Description | Mô tả Scope Hệ thống

Hệ thống **Enterprise Integration Platform (EIP)** (Nền tảng Tích hợp Doanh nghiệp (EIP)) được thiết kế nhằm quản lý tập trung và tự động hóa các quy trình vận hành CNTT cốt lõi trong doanh nghiệp.

- **Phạm vi bên trong hệ thống (In-Scope)**:
  - Quản lý dữ liệu nghiệp vụ trung tâm, tự động hóa quy trình theo chính sách doanh nghiệp.
  - Phân quyền người dùng chi tiết, theo dõi lịch sử thao tác và xuất báo cáo tuân thủ (ISO/SOC2).
  - Tích hợp phát hiện sự cố, gửi cảnh báo tức thì và kết nối dữ liệu hai chiều.

- **Bên ngoài phạm vi hệ thống (Out-of-Scope)**:
  - Trực tiếp quản lý hạ tầng phần cứng máy chủ vật lý.
  - Trực tiếp xử lý xác thực mật khẩu người dùng gốc (do Identity Provider đảm nhận).
