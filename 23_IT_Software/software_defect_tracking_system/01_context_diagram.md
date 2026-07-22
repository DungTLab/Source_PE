# Context Diagram — Software Defect Tracking System

## Mermaid Code

```mermaid
flowchart LR
    QATestLead["QA Test Lead"]
    SoftwareDeveloper["Software Developer"]
    ProductManager["Product Manager"]
    ReleaseLead["Release Lead"]

    JiraIssueEngine["Jira Issue Engine"]
    GitProvider["Git Provider"]
    ActiveDirectoryLDAP["Active Directory LDAP"]
    EmailGateway["Email Gateway"]
    AuditSystem["Audit System"]

    SystemNode(("Software Defect Tracking System"))

    QATestLead -->|"submits management requests & policies"| SystemNode
    SystemNode -->|"returns system status & analytics reports"| QATestLead

    SoftwareDeveloper -->|"interacts with self-service operations"| SystemNode
    SystemNode -->|"provides real-time processing results"| SoftwareDeveloper

    ProductManager -->|"configures operational rules & data"| SystemNode
    SystemNode -->|"returns execution logs & alerts"| ProductManager

    ReleaseLead -->|"audits compliance & security logs"| SystemNode
    SystemNode -->|"exports compliance audit records"| ReleaseLead

    JiraIssueEngine -->|"provides integration payloads & telemetry"| SystemNode
    SystemNode -->|"dispatches API requests & sync events"| JiraIssueEngine

    GitProvider -->|"authenticates user credentials"| SystemNode
    SystemNode -->|"queries identity & role memberships"| GitProvider

    SystemNode -->|"exports financial & inventory data"| ActiveDirectoryLDAP
    SystemNode -->|"triggers emergency alert notifications"| EmailGateway
    SystemNode -->|"streams audit events & compliance data"| AuditSystem
```

## Actor & Interaction Table | Bảng Actor & Tương tác

| # | Actor | Actor Type | Data Sent TO System | Data Received FROM System | Notes |
|---|-------|------------|---------------------|---------------------------|-------|
| 1 | QA Test Lead | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | QA Test Lead role |
| 2 | Software Developer | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Software Developer role |
| 3 | Product Manager | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Product Manager role |
| 4 | Release Lead | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Release Lead role |
| 5 | Jira Issue Engine | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Jira Issue Engine role |
| 6 | Git Provider | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Git Provider role |
| 7 | Active Directory LDAP | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Active Directory LDAP role |
| 8 | Email Gateway | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Email Gateway role |
| 9 | Audit System | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Audit System role |

## System Boundary Description | Mô tả Scope Hệ thống

Hệ thống **Software Defect Tracking System** (Hệ thống Theo dõi Lỗi Phần mềm) được thiết kế nhằm quản lý tập trung và tự động hóa các quy trình vận hành CNTT cốt lõi trong doanh nghiệp.

- **Phạm vi bên trong hệ thống (In-Scope)**:
  - Quản lý dữ liệu nghiệp vụ trung tâm, tự động hóa quy trình theo chính sách doanh nghiệp.
  - Phân quyền người dùng chi tiết, theo dõi lịch sử thao tác và xuất báo cáo tuân thủ (ISO/SOC2).
  - Tích hợp phát hiện sự cố, gửi cảnh báo tức thì và kết nối dữ liệu hai chiều.

- **Bên ngoài phạm vi hệ thống (Out-of-Scope)**:
  - Trực tiếp quản lý hạ tầng phần cứng máy chủ vật lý.
  - Trực tiếp xử lý xác thực mật khẩu người dùng gốc (do Identity Provider đảm nhận).
