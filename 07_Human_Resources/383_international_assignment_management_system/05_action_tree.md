# Action Tree — International Assignment Management System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
graph TD
    Root["International Assignment Management System"]

    Root --> M1["Assignment Requests"]
    Root --> M2["Visa & Compliance"]
    Root --> M3["Travel & Accommodation"]
    Root --> M4["Financial & Allowances"]
    Root --> M5["System Administration"]

    M1 --> A11["Apply for Assignment"]
    M1 --> A12["Review Application"]
    M1 --> A13["Track Status"]

    M2 --> A21["Process Visa"]
    M2 --> A22["Update Compliance Docs"]
    M2 --> A23["Monitor Expiry Dates"]

    M3 --> A31["Book Flights"]
    M3 --> A32["Reserve Hotel"]
    M3 --> A33["Share Itinerary"]

    M4 --> A41["Manage Allowances"]
    M4 --> A42["Process Expenses"]
    M4 --> A43["Sync with Payroll"]

    M5 --> A51["Manage Users"]
    M5 --> A52["Set System Policies"]
    M5 --> A53["Audit Logs"]
```

## Module Description | Mo ta Module

| # | Module | Description | Actions |
|---|--------|-------------|---------|
| 1 | Assignment Requests | Quan ly viec xin va duyet don cong tac quoc te | Apply for Assignment, Review Application, Track Status |
| 2 | Visa & Compliance | Quan ly ho so visa va cac quy dinh so tai | Process Visa, Update Compliance Docs, Monitor Expiry Dates |
| 3 | Travel & Accommodation| Ho tro viec dat ve di lai va luu tru cho nhan vien | Book Flights, Reserve Hotel, Share Itinerary |
| 4 | Financial & Allowances | Quan ly cac chi phi phat sinh va phu cap | Manage Allowances, Process Expenses, Sync with Payroll |
| 5 | System Administration | Quan tri he thong va thiet lap nguoi dung | Manage Users, Set System Policies, Audit Logs |
