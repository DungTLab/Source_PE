# Context Diagram — Employee Referral Program System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Employee["Employee"]
    Candidate["Referred Candidate"]
    HRRecruiter["HR Recruiter"]
    HiringManager["Hiring Manager"]
    Admin["System Admin"]
    ATS["Applicant Tracking System"]
    PayrollSystem["Payroll System"]
    BackgroundCheck["Background Check System"]

    System(("Employee Referral Program System"))

    Employee -->|"submits referral links"| System
    Employee -->|"tracks referral status"| System
    
    Candidate -->|"submits job application"| System
    
    HRRecruiter -->|"publishes job openings"| System
    HRRecruiter -->|"reviews candidate applications"| System
    
    HiringManager -->|"updates interview feedback"| System
    
    Admin -->|"configures system settings"| System
    
    System -->|"syncs job data"| ATS
    System -->|"requests bonus payout"| PayrollSystem
    System -->|"verifies candidate history"| BackgroundCheck
```

## Actor & Interaction Table | Bang Actor & Tuong tac

| # | Actor | Actor Type | Data Sent TO System | Data Received FROM System | Notes |
|---|-------|------------|---------------------|---------------------------|-------|
| 1 | Employee | Primary | Referral submissions, candidate details | Referral statuses, bonus notifications | Nhan vien gioi thieu ung vien |
| 2 | Referred Candidate | Primary | Application details, resumes | Application status updates, interview schedules | Ung vien duoc gioi thieu |
| 3 | HR Recruiter | Primary | Job postings, application review statuses | New referral alerts, candidate profiles | Chuyen vien tuyen dung |
| 4 | Hiring Manager | Primary | Interview feedback, hiring decisions | Candidate profiles, interview schedules | Quan ly tuyen dung |
| 5 | System Admin | Primary | System configurations, user roles, reward rules | System logs, audit reports | Quan tri he thong |
| 6 | Applicant Tracking System | Supporting | Job requirement updates | Candidate sync data | He thong quan ly tuyen dung chung |
| 7 | Payroll System | Supporting | Payout confirmation | Bonus payment requests | He thong tinh luong de tra thuong |
| 8 | Background Check System | Supporting | Verification reports | Candidate verification requests | He thong kiem tra ly lich |

## System Boundary Description | Mo ta Pham vi He thong

The Employee Referral Program System manages the end-to-end process of internal job referrals, allowing employees to refer candidates and track their progress. It handles job postings specifically for referrals, candidate applications, interview feedback, and bonus tracking. The system integrates with external Applicant Tracking Systems for overall recruitment management and Payroll Systems to process referral rewards. However, the system does not conduct the actual background checks or disburse payments directly.
