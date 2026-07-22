# Context Diagram — Enterprise Content Management System

## Mermaid Code

```mermaid
flowchart LR
    ECMDocumentManager["ECM Document Manager"]
    EnterpriseEmployee["Enterprise Employee"]
    LegalComplianceSpecialist["Legal Compliance Specialist"]
    SystemAdministrator["System Administrator"]

    OpticalCharacterRecognitionOCREngine["Optical Character Recognition OCR Engine"]
    DigitalSignatureProvider["Digital Signature Provider"]
    ActiveDirectoryLDAP["Active Directory LDAP"]
    CloudStorageStorage["Cloud Storage Storage"]
    AuditPortal["Audit Portal"]

    SystemNode(("Enterprise Content Management System"))

    ECMDocumentManager -->|"submits management requests & policies"| SystemNode
    SystemNode -->|"returns system status & analytics reports"| ECMDocumentManager

    EnterpriseEmployee -->|"interacts with self-service operations"| SystemNode
    SystemNode -->|"provides real-time processing results"| EnterpriseEmployee

    LegalComplianceSpecialist -->|"configures operational rules & data"| SystemNode
    SystemNode -->|"returns execution logs & alerts"| LegalComplianceSpecialist

    SystemAdministrator -->|"audits compliance & security logs"| SystemNode
    SystemNode -->|"exports compliance audit records"| SystemAdministrator

    OpticalCharacterRecognitionOCREngine -->|"provides integration payloads & telemetry"| SystemNode
    SystemNode -->|"dispatches API requests & sync events"| OpticalCharacterRecognitionOCREngine

    DigitalSignatureProvider -->|"authenticates user credentials"| SystemNode
    SystemNode -->|"queries identity & role memberships"| DigitalSignatureProvider

    SystemNode -->|"exports financial & inventory data"| ActiveDirectoryLDAP
    SystemNode -->|"triggers emergency alert notifications"| CloudStorageStorage
    SystemNode -->|"streams audit events & compliance data"| AuditPortal
```

## Actor & Interaction Table | Bảng Actor & Tương tác

| # | Actor | Actor Type | Data Sent TO System | Data Received FROM System | Notes |
|---|-------|------------|---------------------|---------------------------|-------|
| 1 | ECM Document Manager | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | ECM Document Manager role |
| 2 | Enterprise Employee | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Enterprise Employee role |
| 3 | Legal Compliance Specialist | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Legal Compliance Specialist role |
| 4 | System Administrator | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | System Administrator role |
| 5 | Optical Character Recognition OCR Engine | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Optical Character Recognition OCR Engine role |
| 6 | Digital Signature Provider | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Digital Signature Provider role |
| 7 | Active Directory LDAP | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Active Directory LDAP role |
| 8 | Cloud Storage Storage | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Cloud Storage Storage role |
| 9 | Audit Portal | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Audit Portal role |

## System Boundary Description | Mô tả Scope Hệ thống

Hệ thống **Enterprise Content Management System** (Hệ thống Quản lý Nội dung Doanh nghiệp) được thiết kế nhằm quản lý tập trung và tự động hóa các quy trình vận hành CNTT cốt lõi trong doanh nghiệp.

- **Phạm vi bên trong hệ thống (In-Scope)**:
  - Quản lý dữ liệu nghiệp vụ trung tâm, tự động hóa quy trình theo chính sách doanh nghiệp.
  - Phân quyền người dùng chi tiết, theo dõi lịch sử thao tác và xuất báo cáo tuân thủ (ISO/SOC2).
  - Tích hợp phát hiện sự cố, gửi cảnh báo tức thì và kết nối dữ liệu hai chiều.

- **Bên ngoài phạm vi hệ thống (Out-of-Scope)**:
  - Trực tiếp quản lý hạ tầng phần cứng máy chủ vật lý.
  - Trực tiếp xử lý xác thực mật khẩu người dùng gốc (do Identity Provider đảm nhận).
