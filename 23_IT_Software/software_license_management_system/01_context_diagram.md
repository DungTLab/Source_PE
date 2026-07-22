# Context Diagram — Software License Management System

## Mermaid Code

```mermaid
flowchart LR
    SoftwareLicenseManager["Software License Manager"]
    EnterpriseEmployee["Enterprise Employee"]
    ProcurementSpecialist["Procurement Specialist"]
    ITAuditor["IT Auditor"]

    SoftwareVendorPortal["Software Vendor Portal"]
    ActiveDirectoryLDAP["Active Directory LDAP"]
    EndpointAssetAgent["Endpoint Asset Agent"]
    EnterpriseERPSystem["Enterprise ERP System"]
    ComplianceAuditPortal["Compliance Audit Portal"]

    SystemNode(("Software License Management System"))

    SoftwareLicenseManager -->|"submits management requests & policies"| SystemNode
    SystemNode -->|"returns system status & analytics reports"| SoftwareLicenseManager

    EnterpriseEmployee -->|"interacts with self-service operations"| SystemNode
    SystemNode -->|"provides real-time processing results"| EnterpriseEmployee

    ProcurementSpecialist -->|"configures operational rules & data"| SystemNode
    SystemNode -->|"returns execution logs & alerts"| ProcurementSpecialist

    ITAuditor -->|"audits compliance & security logs"| SystemNode
    SystemNode -->|"exports compliance audit records"| ITAuditor

    SoftwareVendorPortal -->|"provides integration payloads & telemetry"| SystemNode
    SystemNode -->|"dispatches API requests & sync events"| SoftwareVendorPortal

    ActiveDirectoryLDAP -->|"authenticates user credentials"| SystemNode
    SystemNode -->|"queries identity & role memberships"| ActiveDirectoryLDAP

    SystemNode -->|"exports financial & inventory data"| EndpointAssetAgent
    SystemNode -->|"triggers emergency alert notifications"| EnterpriseERPSystem
    SystemNode -->|"streams audit events & compliance data"| ComplianceAuditPortal
```

## Actor & Interaction Table | Bảng Actor & Tương tác

| # | Actor | Actor Type | Data Sent TO System | Data Received FROM System | Notes |
|---|-------|------------|---------------------|---------------------------|-------|
| 1 | Software License Manager | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Software License Manager role |
| 2 | Enterprise Employee | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Enterprise Employee role |
| 3 | Procurement Specialist | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Procurement Specialist role |
| 4 | IT Auditor | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | IT Auditor role |
| 5 | Software Vendor Portal | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Software Vendor Portal role |
| 6 | Active Directory LDAP | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Active Directory LDAP role |
| 7 | Endpoint Asset Agent | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Endpoint Asset Agent role |
| 8 | Enterprise ERP System | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Enterprise ERP System role |
| 9 | Compliance Audit Portal | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Compliance Audit Portal role |

## System Boundary Description | Mô tả Scope Hệ thống

Hệ thống **Software License Management System** (Hệ thống Quản lý Bản quyền Phần mềm) được thiết kế nhằm quản lý tập trung và tự động hóa các quy trình vận hành CNTT cốt lõi trong doanh nghiệp.

- **Phạm vi bên trong hệ thống (In-Scope)**:
  - Quản lý dữ liệu nghiệp vụ trung tâm, tự động hóa quy trình theo chính sách doanh nghiệp.
  - Phân quyền người dùng chi tiết, theo dõi lịch sử thao tác và xuất báo cáo tuân thủ (ISO/SOC2).
  - Tích hợp phát hiện sự cố, gửi cảnh báo tức thì và kết nối dữ liệu hai chiều.

- **Bên ngoài phạm vi hệ thống (Out-of-Scope)**:
  - Trực tiếp quản lý hạ tầng phần cứng máy chủ vật lý.
  - Trực tiếp xử lý xác thực mật khẩu người dùng gốc (do Identity Provider đảm nhận).
