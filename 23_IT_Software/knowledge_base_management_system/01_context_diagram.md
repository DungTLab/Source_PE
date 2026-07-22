# Context Diagram — Knowledge Base Management System

## Mermaid Code

```mermaid
flowchart LR
    KnowledgeBaseManager["Knowledge Base Manager"]
    TechnicalAuthor["Technical Author"]
    EnterpriseSupportStaff["Enterprise Support Staff"]
    EndUserCustomer["End User Customer"]

    AISemanticSearchEngine["AI Semantic Search Engine"]
    HelpDeskSystem["Help Desk System"]
    ActiveDirectoryLDAP["Active Directory LDAP"]
    AnalyticsLogger["Analytics Logger"]
    AuditSystem["Audit System"]

    SystemNode(("Knowledge Base Management System"))

    KnowledgeBaseManager -->|"submits management requests & policies"| SystemNode
    SystemNode -->|"returns system status & analytics reports"| KnowledgeBaseManager

    TechnicalAuthor -->|"interacts with self-service operations"| SystemNode
    SystemNode -->|"provides real-time processing results"| TechnicalAuthor

    EnterpriseSupportStaff -->|"configures operational rules & data"| SystemNode
    SystemNode -->|"returns execution logs & alerts"| EnterpriseSupportStaff

    EndUserCustomer -->|"audits compliance & security logs"| SystemNode
    SystemNode -->|"exports compliance audit records"| EndUserCustomer

    AISemanticSearchEngine -->|"provides integration payloads & telemetry"| SystemNode
    SystemNode -->|"dispatches API requests & sync events"| AISemanticSearchEngine

    HelpDeskSystem -->|"authenticates user credentials"| SystemNode
    SystemNode -->|"queries identity & role memberships"| HelpDeskSystem

    SystemNode -->|"exports financial & inventory data"| ActiveDirectoryLDAP
    SystemNode -->|"triggers emergency alert notifications"| AnalyticsLogger
    SystemNode -->|"streams audit events & compliance data"| AuditSystem
```

## Actor & Interaction Table | Bảng Actor & Tương tác

| # | Actor | Actor Type | Data Sent TO System | Data Received FROM System | Notes |
|---|-------|------------|---------------------|---------------------------|-------|
| 1 | Knowledge Base Manager | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Knowledge Base Manager role |
| 2 | Technical Author | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Technical Author role |
| 3 | Enterprise Support Staff | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Enterprise Support Staff role |
| 4 | End User Customer | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | End User Customer role |
| 5 | AI Semantic Search Engine | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | AI Semantic Search Engine role |
| 6 | Help Desk System | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Help Desk System role |
| 7 | Active Directory LDAP | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Active Directory LDAP role |
| 8 | Analytics Logger | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Analytics Logger role |
| 9 | Audit System | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Audit System role |

## System Boundary Description | Mô tả Scope Hệ thống

Hệ thống **Knowledge Base Management System** (Hệ thống Quản lý Cơ sở Tri thức) được thiết kế nhằm quản lý tập trung và tự động hóa các quy trình vận hành CNTT cốt lõi trong doanh nghiệp.

- **Phạm vi bên trong hệ thống (In-Scope)**:
  - Quản lý dữ liệu nghiệp vụ trung tâm, tự động hóa quy trình theo chính sách doanh nghiệp.
  - Phân quyền người dùng chi tiết, theo dõi lịch sử thao tác và xuất báo cáo tuân thủ (ISO/SOC2).
  - Tích hợp phát hiện sự cố, gửi cảnh báo tức thì và kết nối dữ liệu hai chiều.

- **Bên ngoài phạm vi hệ thống (Out-of-Scope)**:
  - Trực tiếp quản lý hạ tầng phần cứng máy chủ vật lý.
  - Trực tiếp xử lý xác thực mật khẩu người dùng gốc (do Identity Provider đảm nhận).
