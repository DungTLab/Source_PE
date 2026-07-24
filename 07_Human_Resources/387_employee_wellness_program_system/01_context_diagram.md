# Context Diagram — Employee Wellness Program System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Employee["Employee"]
    Coordinator["Wellness Coordinator"]
    Admin["System Admin"]
    HRSystem["HR Management System"]
    PayrollSystem["Payroll System"]
    FitnessApp["Fitness Tracking App"]
    Insurance["Health Insurance Provider"]
    PartnerGym["Partner Gym"]

    System(("Employee Wellness Program System"))

    Employee -->|"registers for programs"| System
    Employee -->|"logs fitness activities"| System
    System -->|"sends wellness alerts"| Employee
    
    Coordinator -->|"creates wellness challenges"| System
    Coordinator -->|"reviews wellness reports"| System
    
    Admin -->|"manages users & system settings"| System
    
    HRSystem -->|"syncs employee data"| System
    
    System -->|"requests reward payouts"| PayrollSystem
    
    FitnessApp -->|"sends activity data"| System
    
    System -->|"reports wellness scores"| Insurance
    
    System -->|"verifies gym check-ins"| PartnerGym
```

## Actor & Interaction Table | Bang Actor & Tuong tac

| # | Actor | Actor Type | Data Sent TO System | Data Received FROM System | Notes |
|---|-------|------------|---------------------|---------------------------|-------|
| 1 | Employee | Primary | Activity logs, challenge registrations | Wellness alerts, point balance | Nhan vien tham gia |
| 2 | Wellness Coordinator | Primary | Challenge configurations, wellness content | Participation reports | Dieu phoi vien chuong trinh |
| 3 | System Admin | Primary | System configurations, user roles | System logs, audit reports | Quan tri he thong |
| 4 | HR Management System | Supporting | Employee profile data, department info | Sync status | He thong quan ly nhan su |
| 5 | Payroll System | Supporting | Payout confirmation | Reward deduction/payout requests | He thong tinh luong |
| 6 | Fitness Tracking App | Supporting | Steps, heart rate, burned calories | API connection status | Ung dung theo doi suc khoe |
| 7 | Health Insurance Provider | Regulatory | Premium discount policies | Aggregated wellness scores | Nha cung cap bao hiem |
| 8 | Partner Gym | Supporting | Member check-in data | Membership verification | Phong gym doi tac |

## System Boundary Description | Mo ta Pham vi He thong

The Employee Wellness Program System manages health and fitness initiatives for employees, allowing them to participate in challenges, track physical activities, and redeem rewards. It provides tools for Wellness Coordinators to create and monitor wellness campaigns. The system does not directly manage core employee HR records or process financial rewards; it integrates with the HR Management System for employee data and the Payroll System for reward fulfillment. External fitness apps and partner gyms feed activity data into the system.
