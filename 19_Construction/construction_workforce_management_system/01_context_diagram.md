# Context Diagram — Construction Workforce Management System

## Mermaid Code

```mermaid
flowchart LR
    Actor1["Project Manager"]
    Actor2["Site Engineer"]
    Actor3["Specialized Contractor"]
    Actor4["Quality / Safety Inspector"]
    Actor5["Client / Owner Representative"]
    Actor6["Enterprise ERP System"]
    Actor7["Regulatory Building Authority"]
    System(("Construction Workforce Management System"))

    Actor1 -->|"submits Biometric Attendance plans"| System
    System -->|"receives  Trade Licenses analytical reports"| Actor1
    Actor2 -->|"submits daily Biometric Attendance records"| System
    System -->|"receives activity approvals and checklists"| Actor2
    Actor3 -->|"submits work execution data & certificates"| System
    System -->|"receives package specifications & work orders"| Actor3
    Actor4 -->|"submits compliance audit reports"| System
    System -->|"receives inspection schedules & drawings"| Actor4
    Actor5 -->|"submits review feedback and sign-offs"| System
    System -->|"receives executive dashboards and status logs"| Actor5
    Actor6 -->|"returns financial ledger sync data"| System
    System -->|"receives transaction data and cost allocations"| Actor6
    Actor7 -->|"submits statutory compliance approvals"| System
    System -->|"receives official audit submission packages"| Actor7
```

## Actor & Interaction Table | Bang Actor & Tuong tac

| # | Actor | Actor Type | Data Sent TO System | Data Received FROM System | Notes |
|---|-------|------------|---------------------|---------------------------|-------|
| 1 | Project Manager | Primary | submits Biometric Attendance plans | receives  Trade Licenses analytical reports | Key stakeholder in Construction Workforce Management System |
| 2 | Site Engineer | Primary | submits daily Biometric Attendance records | receives activity approvals and checklists | Key stakeholder in Construction Workforce Management System |
| 3 | Specialized Contractor | Primary | submits work execution data & certificates | receives package specifications & work orders | Key stakeholder in Construction Workforce Management System |
| 4 | Quality / Safety Inspector | Primary | submits compliance audit reports | receives inspection schedules & drawings | Key stakeholder in Construction Workforce Management System |
| 5 | Client / Owner Representative | Primary | submits review feedback and sign-offs | receives executive dashboards and status logs | Key stakeholder in Construction Workforce Management System |
| 6 | Enterprise ERP System | Supporting | returns financial ledger sync data | receives transaction data and cost allocations | Key stakeholder in Construction Workforce Management System |
| 7 | Regulatory Building Authority | Regulatory | submits statutory compliance approvals | receives official audit submission packages | Key stakeholder in Construction Workforce Management System |

## System Boundary Description | Mo ta Pham vi He thong

He thong He thong Quan ly Nhan luc Xay dung (Construction Workforce Management System) quan ly toan bo quy trinh nghiep vu cot loi trong pham vi du an. He thong tiep nhan du lieu tu cac ben lien quan, kiem tra tinh hop le va xu ly luu vet minh bach. Cac he thong ben ngoai va co quan quan ly tuong tac voi he thong thong qua giao dien ket noi va API duoc bao mat.
