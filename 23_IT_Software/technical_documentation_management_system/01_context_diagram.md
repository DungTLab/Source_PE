# Context Diagram — Technical Documentation Management System

## Mermaid Code

```mermaid
flowchart LR
    TechnicalWriter["Technical Writer"]
    SoftwareArchitect["Software Architect"]
    DeveloperConsumer["Developer Consumer"]
    QAEngineer["QA Engineer"]

    GitRepositoryHost["Git Repository Host"]
    MarkdownStaticSiteGenerator["Markdown Static Site Generator"]
    ActiveDirectoryLDAP["Active Directory LDAP"]
    AlgoliaSearchAPI["Algolia Search API"]
    AuditLogger["Audit Logger"]

    SystemNode(("Technical Documentation Management System"))

    TechnicalWriter -->|"submits management requests & policies"| SystemNode
    SystemNode -->|"returns system status & analytics reports"| TechnicalWriter

    SoftwareArchitect -->|"interacts with self-service operations"| SystemNode
    SystemNode -->|"provides real-time processing results"| SoftwareArchitect

    DeveloperConsumer -->|"configures operational rules & data"| SystemNode
    SystemNode -->|"returns execution logs & alerts"| DeveloperConsumer

    QAEngineer -->|"audits compliance & security logs"| SystemNode
    SystemNode -->|"exports compliance audit records"| QAEngineer

    GitRepositoryHost -->|"provides integration payloads & telemetry"| SystemNode
    SystemNode -->|"dispatches API requests & sync events"| GitRepositoryHost

    MarkdownStaticSiteGenerator -->|"authenticates user credentials"| SystemNode
    SystemNode -->|"queries identity & role memberships"| MarkdownStaticSiteGenerator

    SystemNode -->|"exports financial & inventory data"| ActiveDirectoryLDAP
    SystemNode -->|"triggers emergency alert notifications"| AlgoliaSearchAPI
    SystemNode -->|"streams audit events & compliance data"| AuditLogger
```

## Actor & Interaction Table | Bảng Actor & Tương tác

| # | Actor | Actor Type | Data Sent TO System | Data Received FROM System | Notes |
|---|-------|------------|---------------------|---------------------------|-------|
| 1 | Technical Writer | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Technical Writer role |
| 2 | Software Architect | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Software Architect role |
| 3 | Developer Consumer | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Developer Consumer role |
| 4 | QA Engineer | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | QA Engineer role |
| 5 | Git Repository Host | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Git Repository Host role |
| 6 | Markdown Static Site Generator | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Markdown Static Site Generator role |
| 7 | Active Directory LDAP | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Active Directory LDAP role |
| 8 | Algolia Search API | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Algolia Search API role |
| 9 | Audit Logger | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Audit Logger role |

## System Boundary Description | Mô tả Scope Hệ thống

Hệ thống **Technical Documentation Management System** (Hệ thống Quản lý Tài liệu Kỹ thuật) được thiết kế nhằm quản lý tập trung và tự động hóa các quy trình vận hành CNTT cốt lõi trong doanh nghiệp.

- **Phạm vi bên trong hệ thống (In-Scope)**:
  - Quản lý dữ liệu nghiệp vụ trung tâm, tự động hóa quy trình theo chính sách doanh nghiệp.
  - Phân quyền người dùng chi tiết, theo dõi lịch sử thao tác và xuất báo cáo tuân thủ (ISO/SOC2).
  - Tích hợp phát hiện sự cố, gửi cảnh báo tức thì và kết nối dữ liệu hai chiều.

- **Bên ngoài phạm vi hệ thống (Out-of-Scope)**:
  - Trực tiếp quản lý hạ tầng phần cứng máy chủ vật lý.
  - Trực tiếp xử lý xác thực mật khẩu người dùng gốc (do Identity Provider đảm nhận).
