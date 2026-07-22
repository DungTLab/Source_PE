# Context Diagram — Tech Talent Acquisition System

## Mermaid Code

```mermaid
flowchart LR
    TechRecruiter["Tech Recruiter"]
    EngineeringHiringManager["Engineering Hiring Manager"]
    TechnicalInterviewer["Technical Interviewer"]
    TechCandidate["Tech Candidate"]

    HackerRankCodingTestEngine["HackerRank Coding Test Engine"]
    LinkedInRecruiterAPI["LinkedIn Recruiter API"]
    ActiveDirectoryLDAP["Active Directory LDAP"]
    EmailGateway["Email Gateway"]
    HRAuditPortal["HR Audit Portal"]

    SystemNode(("Tech Talent Acquisition System"))

    TechRecruiter -->|"submits management requests & policies"| SystemNode
    SystemNode -->|"returns system status & analytics reports"| TechRecruiter

    EngineeringHiringManager -->|"interacts with self-service operations"| SystemNode
    SystemNode -->|"provides real-time processing results"| EngineeringHiringManager

    TechnicalInterviewer -->|"configures operational rules & data"| SystemNode
    SystemNode -->|"returns execution logs & alerts"| TechnicalInterviewer

    TechCandidate -->|"audits compliance & security logs"| SystemNode
    SystemNode -->|"exports compliance audit records"| TechCandidate

    HackerRankCodingTestEngine -->|"provides integration payloads & telemetry"| SystemNode
    SystemNode -->|"dispatches API requests & sync events"| HackerRankCodingTestEngine

    LinkedInRecruiterAPI -->|"authenticates user credentials"| SystemNode
    SystemNode -->|"queries identity & role memberships"| LinkedInRecruiterAPI

    SystemNode -->|"exports financial & inventory data"| ActiveDirectoryLDAP
    SystemNode -->|"triggers emergency alert notifications"| EmailGateway
    SystemNode -->|"streams audit events & compliance data"| HRAuditPortal
```

## Actor & Interaction Table | Bảng Actor & Tương tác

| # | Actor | Actor Type | Data Sent TO System | Data Received FROM System | Notes |
|---|-------|------------|---------------------|---------------------------|-------|
| 1 | Tech Recruiter | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Tech Recruiter role |
| 2 | Engineering Hiring Manager | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Engineering Hiring Manager role |
| 3 | Technical Interviewer | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Technical Interviewer role |
| 4 | Tech Candidate | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Tech Candidate role |
| 5 | HackerRank Coding Test Engine | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | HackerRank Coding Test Engine role |
| 6 | LinkedIn Recruiter API | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | LinkedIn Recruiter API role |
| 7 | Active Directory LDAP | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Active Directory LDAP role |
| 8 | Email Gateway | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Email Gateway role |
| 9 | HR Audit Portal | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | HR Audit Portal role |

## System Boundary Description | Mô tả Scope Hệ thống

Hệ thống **Tech Talent Acquisition System** (Hệ thống Tuyển dụng Nhân tài Công nghệ) được thiết kế nhằm quản lý tập trung và tự động hóa các quy trình vận hành CNTT cốt lõi trong doanh nghiệp.

- **Phạm vi bên trong hệ thống (In-Scope)**:
  - Quản lý dữ liệu nghiệp vụ trung tâm, tự động hóa quy trình theo chính sách doanh nghiệp.
  - Phân quyền người dùng chi tiết, theo dõi lịch sử thao tác và xuất báo cáo tuân thủ (ISO/SOC2).
  - Tích hợp phát hiện sự cố, gửi cảnh báo tức thì và kết nối dữ liệu hai chiều.

- **Bên ngoài phạm vi hệ thống (Out-of-Scope)**:
  - Trực tiếp quản lý hạ tầng phần cứng máy chủ vật lý.
  - Trực tiếp xử lý xác thực mật khẩu người dùng gốc (do Identity Provider đảm nhận).
