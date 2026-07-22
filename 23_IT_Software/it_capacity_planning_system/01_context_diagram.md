# Context Diagram — IT Capacity Planning System

## Mermaid Code

```mermaid
flowchart LR
    CapacityPlanningSpecialist["Capacity Planning Specialist"]
    ITInfrastructureLead["IT Infrastructure Lead"]
    FinOpsManager["FinOps Manager"]
    ChiefInformationOfficerCIO["Chief Information Officer CIO"]

    vCenterInfrastructureAPI["vCenter Infrastructure API"]
    AWSCloudWatchAPI["AWS CloudWatch API"]
    ActiveDirectoryLDAP["Active Directory LDAP"]
    ERPProcurementSystem["ERP Procurement System"]
    AuditPortal["Audit Portal"]

    SystemNode(("IT Capacity Planning System"))

    CapacityPlanningSpecialist -->|"submits management requests & policies"| SystemNode
    SystemNode -->|"returns system status & analytics reports"| CapacityPlanningSpecialist

    ITInfrastructureLead -->|"interacts with self-service operations"| SystemNode
    SystemNode -->|"provides real-time processing results"| ITInfrastructureLead

    FinOpsManager -->|"configures operational rules & data"| SystemNode
    SystemNode -->|"returns execution logs & alerts"| FinOpsManager

    ChiefInformationOfficerCIO -->|"audits compliance & security logs"| SystemNode
    SystemNode -->|"exports compliance audit records"| ChiefInformationOfficerCIO

    vCenterInfrastructureAPI -->|"provides integration payloads & telemetry"| SystemNode
    SystemNode -->|"dispatches API requests & sync events"| vCenterInfrastructureAPI

    AWSCloudWatchAPI -->|"authenticates user credentials"| SystemNode
    SystemNode -->|"queries identity & role memberships"| AWSCloudWatchAPI

    SystemNode -->|"exports financial & inventory data"| ActiveDirectoryLDAP
    SystemNode -->|"triggers emergency alert notifications"| ERPProcurementSystem
    SystemNode -->|"streams audit events & compliance data"| AuditPortal
```

## Actor & Interaction Table | Bảng Actor & Tương tác

| # | Actor | Actor Type | Data Sent TO System | Data Received FROM System | Notes |
|---|-------|------------|---------------------|---------------------------|-------|
| 1 | Capacity Planning Specialist | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Capacity Planning Specialist role |
| 2 | IT Infrastructure Lead | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | IT Infrastructure Lead role |
| 3 | FinOps Manager | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | FinOps Manager role |
| 4 | Chief Information Officer CIO | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Chief Information Officer CIO role |
| 5 | vCenter Infrastructure API | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | vCenter Infrastructure API role |
| 6 | AWS CloudWatch API | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | AWS CloudWatch API role |
| 7 | Active Directory LDAP | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Active Directory LDAP role |
| 8 | ERP Procurement System | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | ERP Procurement System role |
| 9 | Audit Portal | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Audit Portal role |

## System Boundary Description | Mô tả Scope Hệ thống

Hệ thống **IT Capacity Planning System** (Hệ thống Lập kế hoạch Năng lực IT) được thiết kế nhằm quản lý tập trung và tự động hóa các quy trình vận hành CNTT cốt lõi trong doanh nghiệp.

- **Phạm vi bên trong hệ thống (In-Scope)**:
  - Quản lý dữ liệu nghiệp vụ trung tâm, tự động hóa quy trình theo chính sách doanh nghiệp.
  - Phân quyền người dùng chi tiết, theo dõi lịch sử thao tác và xuất báo cáo tuân thủ (ISO/SOC2).
  - Tích hợp phát hiện sự cố, gửi cảnh báo tức thì và kết nối dữ liệu hai chiều.

- **Bên ngoài phạm vi hệ thống (Out-of-Scope)**:
  - Trực tiếp quản lý hạ tầng phần cứng máy chủ vật lý.
  - Trực tiếp xử lý xác thực mật khẩu người dùng gốc (do Identity Provider đảm nhận).
