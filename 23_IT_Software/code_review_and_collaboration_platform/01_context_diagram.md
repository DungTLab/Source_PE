# Context Diagram — Code Review & Collaboration Platform

## Mermaid Code

```mermaid
flowchart LR
    LeadSoftwareArchitect["Lead Software Architect"]
    SeniorDeveloperReviewer["Senior Developer Reviewer"]
    SoftwareEngineerAuthor["Software Engineer Author"]
    SecurityEngineer["Security Engineer"]

    GitRepositoryHost["Git Repository Host"]
    CICDPipelineEngine["CI/CD Pipeline Engine"]
    ActiveDirectoryLDAP["Active Directory LDAP"]
    NotificationGateway["Notification Gateway"]
    AuditLogger["Audit Logger"]

    SystemNode(("Code Review & Collaboration Platform"))

    LeadSoftwareArchitect -->|"submits management requests & policies"| SystemNode
    SystemNode -->|"returns system status & analytics reports"| LeadSoftwareArchitect

    SeniorDeveloperReviewer -->|"interacts with self-service operations"| SystemNode
    SystemNode -->|"provides real-time processing results"| SeniorDeveloperReviewer

    SoftwareEngineerAuthor -->|"configures operational rules & data"| SystemNode
    SystemNode -->|"returns execution logs & alerts"| SoftwareEngineerAuthor

    SecurityEngineer -->|"audits compliance & security logs"| SystemNode
    SystemNode -->|"exports compliance audit records"| SecurityEngineer

    GitRepositoryHost -->|"provides integration payloads & telemetry"| SystemNode
    SystemNode -->|"dispatches API requests & sync events"| GitRepositoryHost

    CICDPipelineEngine -->|"authenticates user credentials"| SystemNode
    SystemNode -->|"queries identity & role memberships"| CICDPipelineEngine

    SystemNode -->|"exports financial & inventory data"| ActiveDirectoryLDAP
    SystemNode -->|"triggers emergency alert notifications"| NotificationGateway
    SystemNode -->|"streams audit events & compliance data"| AuditLogger
```

## Actor & Interaction Table | Bảng Actor & Tương tác

| # | Actor | Actor Type | Data Sent TO System | Data Received FROM System | Notes |
|---|-------|------------|---------------------|---------------------------|-------|
| 1 | Lead Software Architect | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Lead Software Architect role |
| 2 | Senior Developer Reviewer | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Senior Developer Reviewer role |
| 3 | Software Engineer Author | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Software Engineer Author role |
| 4 | Security Engineer | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Security Engineer role |
| 5 | Git Repository Host | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Git Repository Host role |
| 6 | CI/CD Pipeline Engine | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | CI/CD Pipeline Engine role |
| 7 | Active Directory LDAP | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Active Directory LDAP role |
| 8 | Notification Gateway | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Notification Gateway role |
| 9 | Audit Logger | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Audit Logger role |

## System Boundary Description | Mô tả Scope Hệ thống

Hệ thống **Code Review & Collaboration Platform** (Nền tảng Review Code và Hợp tác) được thiết kế nhằm quản lý tập trung và tự động hóa các quy trình vận hành CNTT cốt lõi trong doanh nghiệp.

- **Phạm vi bên trong hệ thống (In-Scope)**:
  - Quản lý dữ liệu nghiệp vụ trung tâm, tự động hóa quy trình theo chính sách doanh nghiệp.
  - Phân quyền người dùng chi tiết, theo dõi lịch sử thao tác và xuất báo cáo tuân thủ (ISO/SOC2).
  - Tích hợp phát hiện sự cố, gửi cảnh báo tức thì và kết nối dữ liệu hai chiều.

- **Bên ngoài phạm vi hệ thống (Out-of-Scope)**:
  - Trực tiếp quản lý hạ tầng phần cứng máy chủ vật lý.
  - Trực tiếp xử lý xác thực mật khẩu người dùng gốc (do Identity Provider đảm nhận).
