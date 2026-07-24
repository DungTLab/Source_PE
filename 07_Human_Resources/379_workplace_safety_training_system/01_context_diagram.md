# Context Diagram — Workplace Safety Training System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    SafetyManager["Safety Manager"]
    Employee["Employee"]
    Instructor["Instructor"]
    HRSystem["HR System"]
    CertificationBoard["Certification Board"]
    EmailSystem["Email System"]
    Admin["System Admin"]

    System(("Workplace Safety Training System"))

    SafetyManager -->|"assigns training policies"| System
    SafetyManager -->|"tracks compliance status"| System
    
    Employee -->|"completes safety courses"| System
    Employee -->|"takes online exams"| System
    System -->|"issues safety certificates"| Employee
    
    Instructor -->|"uploads training materials"| System
    Instructor -->|"grades offline assessments"| System
    
    HRSystem -->|"syncs employee data"| System
    
    System -->|"reports certification status"| CertificationBoard
    System -->|"sends training reminders"| EmailSystem
    Admin -->|"manages users & system settings"| System
```

## Actor & Interaction Table | Bang Actor & Tuong tac

| # | Actor | Actor Type | Data Sent TO System | Data Received FROM System | Notes |
|---|-------|------------|---------------------|---------------------------|-------|
| 1 | Safety Manager | Primary | Training policies, compliance rules | Compliance reports, risk alerts | Quan ly an toan lao dong |
| 2 | Employee | Primary | Exam answers, course completion data | Safety certificates, training materials | Nhan vien tham gia hoc |
| 3 | Instructor | Primary | Course content, assessment grades | Trainee lists, course feedback | Giang vien dao tao |
| 4 | HR System | Supporting | Employee profiles, department structures | Training completion status | He thong nhan su |
| 5 | Certification Board | Regulatory | Certification standards | Employee certification records | To chuc cap chung chi |
| 6 | Email System | Supporting | Email delivery status | Notifications, training reminders | He thong email |
| 7 | System Admin | Primary | System configurations, user roles | System logs, audit reports | Quan tri he thong |

## System Boundary Description | Mo ta Pham vi He thong

The Workplace Safety Training System is designed to manage and deliver safety training courses to employees, ensuring organizational compliance with safety regulations. It provides a platform for Safety Managers to assign courses, Instructors to upload content, and Employees to complete exams and earn certificates. The system does not directly manage core employee HR data; instead, it integrates with the HR System for user synchronization. Additionally, it interacts with external Email Systems for notifications and Certification Boards for regulatory reporting.
