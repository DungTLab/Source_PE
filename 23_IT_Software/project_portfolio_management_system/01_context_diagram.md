# Context Diagram — Project Portfolio Management System

## Mermaid Code

```mermaid
flowchart LR
    PortfolioManagementOfficer["Portfolio Management Officer"]
    ProjectManager["Project Manager"]
    ResourceManager["Resource Manager"]
    FinanceDirector["Finance Director"]

    EnterpriseERPSystem["Enterprise ERP System"]
    AgileProjectTracker["Agile Project Tracker"]
    ActiveDirectoryLDAP["Active Directory LDAP"]
    EmailNotificationGateway["Email Notification Gateway"]
    ExecutiveDashboard["Executive Dashboard"]

    SystemNode(("Project Portfolio Management System"))

    PortfolioManagementOfficer -->|"submits management requests & policies"| SystemNode
    SystemNode -->|"returns system status & analytics reports"| PortfolioManagementOfficer

    ProjectManager -->|"interacts with self-service operations"| SystemNode
    SystemNode -->|"provides real-time processing results"| ProjectManager

    ResourceManager -->|"configures operational rules & data"| SystemNode
    SystemNode -->|"returns execution logs & alerts"| ResourceManager

    FinanceDirector -->|"audits compliance & security logs"| SystemNode
    SystemNode -->|"exports compliance audit records"| FinanceDirector

    EnterpriseERPSystem -->|"provides integration payloads & telemetry"| SystemNode
    SystemNode -->|"dispatches API requests & sync events"| EnterpriseERPSystem

    AgileProjectTracker -->|"authenticates user credentials"| SystemNode
    SystemNode -->|"queries identity & role memberships"| AgileProjectTracker

    SystemNode -->|"exports financial & inventory data"| ActiveDirectoryLDAP
    SystemNode -->|"triggers emergency alert notifications"| EmailNotificationGateway
    SystemNode -->|"streams audit events & compliance data"| ExecutiveDashboard
```

## Actor & Interaction Table | Bảng Actor & Tương tác

| # | Actor | Actor Type | Data Sent TO System | Data Received FROM System | Notes |
|---|-------|------------|---------------------|---------------------------|-------|
| 1 | Portfolio Management Officer | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Portfolio Management Officer role |
| 2 | Project Manager | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Project Manager role |
| 3 | Resource Manager | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Resource Manager role |
| 4 | Finance Director | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Finance Director role |
| 5 | Enterprise ERP System | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Enterprise ERP System role |
| 6 | Agile Project Tracker | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Agile Project Tracker role |
| 7 | Active Directory LDAP | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Active Directory LDAP role |
| 8 | Email Notification Gateway | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Email Notification Gateway role |
| 9 | Executive Dashboard | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Executive Dashboard role |

## System Boundary Description | Mô tả Scope Hệ thống

Hệ thống **Project Portfolio Management System** (Hệ thống Quản lý Danh mục Dự án) được thiết kế nhằm quản lý tập trung và tự động hóa các quy trình vận hành CNTT cốt lõi trong doanh nghiệp.

- **Phạm vi bên trong hệ thống (In-Scope)**:
  - Quản lý dữ liệu nghiệp vụ trung tâm, tự động hóa quy trình theo chính sách doanh nghiệp.
  - Phân quyền người dùng chi tiết, theo dõi lịch sử thao tác và xuất báo cáo tuân thủ (ISO/SOC2).
  - Tích hợp phát hiện sự cố, gửi cảnh báo tức thì và kết nối dữ liệu hai chiều.

- **Bên ngoài phạm vi hệ thống (Out-of-Scope)**:
  - Trực tiếp quản lý hạ tầng phần cứng máy chủ vật lý.
  - Trực tiếp xử lý xác thực mật khẩu người dùng gốc (do Identity Provider đảm nhận).
