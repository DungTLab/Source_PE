# Context Diagram — Compensation Benchmarking System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    HRAnalyst["HR Analyst"]
    HRManager["HR Manager"]
    MarketDataProvider["Market Data Provider"]
    PayrollSystem["Payroll System"]
    RecruitmentPortal["Recruitment Portal"]
    SystemAdmin["System Admin"]

    System(("Compensation Benchmarking System"))

    HRAnalyst -->|"inputs company salary data"| System
    HRAnalyst -->|"runs benchmark comparisons"| System
    
    HRManager -->|"approves compensation strategies"| System
    HRManager -->|"views compensation reports"| System
    
    MarketDataProvider -->|"supplies industry salary trends"| System
    
    System -->|"sends updated salary bands"| PayrollSystem
    System -->|"provides competitive salary ranges"| RecruitmentPortal
    
    SystemAdmin -->|"configures integration settings"| System
    SystemAdmin -->|"manages users & roles"| System
```

## Actor & Interaction Table | Bang Actor & Tuong tac

| # | Actor | Actor Type | Data Sent TO System | Data Received FROM System | Notes |
|---|-------|------------|---------------------|---------------------------|-------|
| 1 | HR Analyst | Primary | Internal salary data, job descriptions | Benchmark reports, market comparisons | Nhan vien phan tich nhan su |
| 2 | HR Manager | Primary | Approval of compensation adjustments | Summary dashboards, compensation strategies | Quan ly nhan su |
| 3 | Market Data Provider | Supporting | Industry salary surveys, market trends | Subscription verifications | Cung cap du lieu thi truong |
| 4 | Payroll System | Supporting | Current employee salary data | Updated salary bands | He thong tinh luong |
| 5 | Recruitment Portal | Supporting | Candidate expected salary | Competitive salary ranges | He thong tuyen dung |
| 6 | System Admin | Primary | System configurations, user access rules | System logs, error alerts | Quan tri he thong |

## System Boundary Description | Mo ta Pham vi He thong

The Compensation Benchmarking System is designed to analyze and compare an organization's internal salary structures against external market data. It allows HR Analysts and HR Managers to make data-driven decisions regarding compensation strategies and salary bands. The system directly integrates with Market Data Providers to fetch industry trends, but it does not process actual payroll transactions or recruit candidates. Instead, it supplies the defined salary ranges to the internal Payroll System and Recruitment Portal.
