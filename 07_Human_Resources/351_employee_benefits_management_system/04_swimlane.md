# Swimlane Diagram — Employee Benefits Management System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Enrollment Process"])

    subgraph EmployeeLane["Employee"]
        E1["Login to System"]
        E2["Select Benefit Plan"]
        E3["Submit Enrollment Form"]
        E4["Receive Status Notification"]
    end

    subgraph SystemLane["Employee Benefits Management System"]
        S1["Validate Eligibility & Costs"]
        S2{"Is Valid?"}
        S3["Show Error Message"]
        S4["Save as Pending"]
        S5["Update Enrollment Status"]
        S6["Generate Deduction Record"]
    end

    subgraph ManagerLane["HR Manager"]
        M1["Review Enrollment"]
        M2{"Approve?"}
    end

    Finish(["End Process"])

    Start --> E1 --> E2 --> E3 --> S1
    S1 --> S2
    S2 -->|"No"| S3 --> E2
    S2 -->|"Yes"| S4 --> M1
    
    M1 --> M2
    M2 -->|"Yes (Approve)"| S5
    M2 -->|"No (Reject)"| S5
    
    S5 --> S6 --> E4 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Employee | Nguoi bat dau quy trinh chon goi phuc loi, dien form va nhan ket qua dang ky. |
| 2 | Employee Benefits Management System | He thong xac thuc dieu kien hop le, luu ho so, cap nhat trang thai va tao du lieu khau tru luong. |
| 3 | HR Manager | Nguoi quan ly chiu trach nhiem xet duyet hoac tu choi yeu cau dang ky cua nhan vien. |
