# Context Diagram — Data Analytics Pipeline System

## Mermaid Code

```mermaid
flowchart LR
    DataPipelineEngineer["Data Pipeline Engineer"]
    DataScientist["Data Scientist"]
    BIDeveloper["BI Developer"]
    SecurityAuditor["Security Auditor"]

    ApacheAirflowDAGEngine["Apache Airflow DAG Engine"]
    SparkClusterEngine["Spark Cluster Engine"]
    ActiveDirectoryLDAP["Active Directory LDAP"]
    DataLakeStorage["Data Lake Storage"]
    SIEMSecurityPortal["SIEM Security Portal"]

    SystemNode(("Data Analytics Pipeline System"))

    DataPipelineEngineer -->|"submits management requests & policies"| SystemNode
    SystemNode -->|"returns system status & analytics reports"| DataPipelineEngineer

    DataScientist -->|"interacts with self-service operations"| SystemNode
    SystemNode -->|"provides real-time processing results"| DataScientist

    BIDeveloper -->|"configures operational rules & data"| SystemNode
    SystemNode -->|"returns execution logs & alerts"| BIDeveloper

    SecurityAuditor -->|"audits compliance & security logs"| SystemNode
    SystemNode -->|"exports compliance audit records"| SecurityAuditor

    ApacheAirflowDAGEngine -->|"provides integration payloads & telemetry"| SystemNode
    SystemNode -->|"dispatches API requests & sync events"| ApacheAirflowDAGEngine

    SparkClusterEngine -->|"authenticates user credentials"| SystemNode
    SystemNode -->|"queries identity & role memberships"| SparkClusterEngine

    SystemNode -->|"exports financial & inventory data"| ActiveDirectoryLDAP
    SystemNode -->|"triggers emergency alert notifications"| DataLakeStorage
    SystemNode -->|"streams audit events & compliance data"| SIEMSecurityPortal
```

## Actor & Interaction Table | Bảng Actor & Tương tác

| # | Actor | Actor Type | Data Sent TO System | Data Received FROM System | Notes |
|---|-------|------------|---------------------|---------------------------|-------|
| 1 | Data Pipeline Engineer | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Data Pipeline Engineer role |
| 2 | Data Scientist | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Data Scientist role |
| 3 | BI Developer | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | BI Developer role |
| 4 | Security Auditor | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Security Auditor role |
| 5 | Apache Airflow DAG Engine | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Apache Airflow DAG Engine role |
| 6 | Spark Cluster Engine | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Spark Cluster Engine role |
| 7 | Active Directory LDAP | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Active Directory LDAP role |
| 8 | Data Lake Storage | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Data Lake Storage role |
| 9 | SIEM Security Portal | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | SIEM Security Portal role |

## System Boundary Description | Mô tả Scope Hệ thống

Hệ thống **Data Analytics Pipeline System** (Hệ thống Đường ống Phân tích Dữ liệu) được thiết kế nhằm quản lý tập trung và tự động hóa các quy trình vận hành CNTT cốt lõi trong doanh nghiệp.

- **Phạm vi bên trong hệ thống (In-Scope)**:
  - Quản lý dữ liệu nghiệp vụ trung tâm, tự động hóa quy trình theo chính sách doanh nghiệp.
  - Phân quyền người dùng chi tiết, theo dõi lịch sử thao tác và xuất báo cáo tuân thủ (ISO/SOC2).
  - Tích hợp phát hiện sự cố, gửi cảnh báo tức thì và kết nối dữ liệu hai chiều.

- **Bên ngoài phạm vi hệ thống (Out-of-Scope)**:
  - Trực tiếp quản lý hạ tầng phần cứng máy chủ vật lý.
  - Trực tiếp xử lý xác thực mật khẩu người dùng gốc (do Identity Provider đảm nhận).
