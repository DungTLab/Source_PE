# Context Diagram — Data Quality Management System

## Mermaid Code

```mermaid
flowchart LR
    DataQualityAnalyst["Data Quality Analyst"]
    DataSteward["Data Steward"]
    DataEngineer["Data Engineer"]
    ComplianceOfficer["Compliance Officer"]

    EnterpriseDataWarehouse["Enterprise Data Warehouse"]
    ETLPipelineServer["ETL Pipeline Server"]
    ActiveDirectoryLDAP["Active Directory LDAP"]
    BiAnalyticsPlatform["Bi Analytics Platform"]
    AuditSystem["Audit System"]

    SystemNode(("Data Quality Management System"))

    DataQualityAnalyst -->|"submits management requests & policies"| SystemNode
    SystemNode -->|"returns system status & analytics reports"| DataQualityAnalyst

    DataSteward -->|"interacts with self-service operations"| SystemNode
    SystemNode -->|"provides real-time processing results"| DataSteward

    DataEngineer -->|"configures operational rules & data"| SystemNode
    SystemNode -->|"returns execution logs & alerts"| DataEngineer

    ComplianceOfficer -->|"audits compliance & security logs"| SystemNode
    SystemNode -->|"exports compliance audit records"| ComplianceOfficer

    EnterpriseDataWarehouse -->|"provides integration payloads & telemetry"| SystemNode
    SystemNode -->|"dispatches API requests & sync events"| EnterpriseDataWarehouse

    ETLPipelineServer -->|"authenticates user credentials"| SystemNode
    SystemNode -->|"queries identity & role memberships"| ETLPipelineServer

    SystemNode -->|"exports financial & inventory data"| ActiveDirectoryLDAP
    SystemNode -->|"triggers emergency alert notifications"| BiAnalyticsPlatform
    SystemNode -->|"streams audit events & compliance data"| AuditSystem
```

## Actor & Interaction Table | Bảng Actor & Tương tác

| # | Actor | Actor Type | Data Sent TO System | Data Received FROM System | Notes |
|---|-------|------------|---------------------|---------------------------|-------|
| 1 | Data Quality Analyst | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Data Quality Analyst role |
| 2 | Data Steward | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Data Steward role |
| 3 | Data Engineer | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Data Engineer role |
| 4 | Compliance Officer | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Compliance Officer role |
| 5 | Enterprise Data Warehouse | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Enterprise Data Warehouse role |
| 6 | ETL Pipeline Server | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | ETL Pipeline Server role |
| 7 | Active Directory LDAP | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Active Directory LDAP role |
| 8 | Bi Analytics Platform | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Bi Analytics Platform role |
| 9 | Audit System | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Audit System role |

## System Boundary Description | Mô tả Scope Hệ thống

Hệ thống **Data Quality Management System** (Hệ thống Quản lý Chất lượng Dữ liệu) được thiết kế nhằm quản lý tập trung và tự động hóa các quy trình vận hành CNTT cốt lõi trong doanh nghiệp.

- **Phạm vi bên trong hệ thống (In-Scope)**:
  - Quản lý dữ liệu nghiệp vụ trung tâm, tự động hóa quy trình theo chính sách doanh nghiệp.
  - Phân quyền người dùng chi tiết, theo dõi lịch sử thao tác và xuất báo cáo tuân thủ (ISO/SOC2).
  - Tích hợp phát hiện sự cố, gửi cảnh báo tức thì và kết nối dữ liệu hai chiều.

- **Bên ngoài phạm vi hệ thống (Out-of-Scope)**:
  - Trực tiếp quản lý hạ tầng phần cứng máy chủ vật lý.
  - Trực tiếp xử lý xác thực mật khẩu người dùng gốc (do Identity Provider đảm nhận).
