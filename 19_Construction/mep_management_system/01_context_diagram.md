# Context Diagram — MEP Management System

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
    System(("MEP Management System"))

    Actor1 -->|"submits Ductwork/Piping Routing plans"| System
    System -->|"receives  Load Balancing analytical reports"| Actor1
    Actor2 -->|"submits daily Ductwork/Piping Routing records"| System
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
| 1 | Project Manager | Primary | submits Ductwork/Piping Routing plans | receives  Load Balancing analytical reports | Key stakeholder in MEP Management System |
| 2 | Site Engineer | Primary | submits daily Ductwork/Piping Routing records | receives activity approvals and checklists | Key stakeholder in MEP Management System |
| 3 | Specialized Contractor | Primary | submits work execution data & certificates | receives package specifications & work orders | Key stakeholder in MEP Management System |
| 4 | Quality / Safety Inspector | Primary | submits compliance audit reports | receives inspection schedules & drawings | Key stakeholder in MEP Management System |
| 5 | Client / Owner Representative | Primary | submits review feedback and sign-offs | receives executive dashboards and status logs | Key stakeholder in MEP Management System |
| 6 | Enterprise ERP System | Supporting | returns financial ledger sync data | receives transaction data and cost allocations | Key stakeholder in MEP Management System |
| 7 | Regulatory Building Authority | Regulatory | submits statutory compliance approvals | receives official audit submission packages | Key stakeholder in MEP Management System |

## System Boundary Description | Mo ta Pham vi He thong

He thong He thong Quan ly Co Dien Nuoc (MEP) (MEP Management System) quan ly toan bo quy trinh nghiep vu cot loi trong pham vi du an. He thong tiep nhan du lieu tu cac ben lien quan, kiem tra tinh hop le va xu ly luu vet minh bach. Cac he thong ben ngoai va co quan quan ly tuong tac voi he thong thong qua giao dien ket noi va API duoc bao mat.
