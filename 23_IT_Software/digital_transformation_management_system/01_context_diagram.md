# Context Diagram — Digital Transformation Management System

## Mermaid Code

```mermaid
flowchart LR
    ChiefDigitalOfficerCDO["Chief Digital Officer CDO"]
    DigitalTransformationLead["Digital Transformation Lead"]
    EnterpriseArchitect["Enterprise Architect"]
    BusinessUnitHead["Business Unit Head"]

    EnterpriseERPSystem["Enterprise ERP System"]
    HRTalentPortal["HR Talent Portal"]
    ActiveDirectoryLDAP["Active Directory LDAP"]
    BIAnalyticsEngine["BI Analytics Engine"]
    ExecutiveDashboard["Executive Dashboard"]

    SystemNode(("Digital Transformation Management System"))

    ChiefDigitalOfficerCDO -->|"submits management requests & policies"| SystemNode
    SystemNode -->|"returns system status & analytics reports"| ChiefDigitalOfficerCDO

    DigitalTransformationLead -->|"interacts with self-service operations"| SystemNode
    SystemNode -->|"provides real-time processing results"| DigitalTransformationLead

    EnterpriseArchitect -->|"configures operational rules & data"| SystemNode
    SystemNode -->|"returns execution logs & alerts"| EnterpriseArchitect

    BusinessUnitHead -->|"audits compliance & security logs"| SystemNode
    SystemNode -->|"exports compliance audit records"| BusinessUnitHead

    EnterpriseERPSystem -->|"provides integration payloads & telemetry"| SystemNode
    SystemNode -->|"dispatches API requests & sync events"| EnterpriseERPSystem

    HRTalentPortal -->|"authenticates user credentials"| SystemNode
    SystemNode -->|"queries identity & role memberships"| HRTalentPortal

    SystemNode -->|"exports financial & inventory data"| ActiveDirectoryLDAP
    SystemNode -->|"triggers emergency alert notifications"| BIAnalyticsEngine
    SystemNode -->|"streams audit events & compliance data"| ExecutiveDashboard
```

## Actor & Interaction Table | Bảng Actor & Tương tác

| # | Actor | Actor Type | Data Sent TO System | Data Received FROM System | Notes |
|---|-------|------------|---------------------|---------------------------|-------|
| 1 | Chief Digital Officer CDO | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Chief Digital Officer CDO role |
| 2 | Digital Transformation Lead | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Digital Transformation Lead role |
| 3 | Enterprise Architect | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Enterprise Architect role |
| 4 | Business Unit Head | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Business Unit Head role |
| 5 | Enterprise ERP System | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Enterprise ERP System role |
| 6 | HR Talent Portal | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | HR Talent Portal role |
| 7 | Active Directory LDAP | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Active Directory LDAP role |
| 8 | BI Analytics Engine | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | BI Analytics Engine role |
| 9 | Executive Dashboard | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Executive Dashboard role |

## System Boundary Description | Mô tả Scope Hệ thống

Hệ thống **Digital Transformation Management System** (Hệ thống Quản lý Chuyển đổi Số) được thiết kế nhằm quản lý tập trung và tự động hóa các quy trình vận hành CNTT cốt lõi trong doanh nghiệp.

- **Phạm vi bên trong hệ thống (In-Scope)**:
  - Quản lý dữ liệu nghiệp vụ trung tâm, tự động hóa quy trình theo chính sách doanh nghiệp.
  - Phân quyền người dùng chi tiết, theo dõi lịch sử thao tác và xuất báo cáo tuân thủ (ISO/SOC2).
  - Tích hợp phát hiện sự cố, gửi cảnh báo tức thì và kết nối dữ liệu hai chiều.

- **Bên ngoài phạm vi hệ thống (Out-of-Scope)**:
  - Trực tiếp quản lý hạ tầng phần cứng máy chủ vật lý.
  - Trực tiếp xử lý xác thực mật khẩu người dùng gốc (do Identity Provider đảm nhận).
