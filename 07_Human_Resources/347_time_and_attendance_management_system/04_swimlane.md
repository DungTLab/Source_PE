# Swimlane Diagram — Time and Attendance Management System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Timesheet Process"])

    subgraph EmployeeLane["Employee"]
        E1["Clock In/Out"]
        E2["Submit Timesheet"]
        E3["Fix Errors"]
    end

    subgraph SystemLane["System"]
        S1["Record Punch Logs"]
        S2["Calculate Daily Hours"]
        S3{"Any Discrepancies?"}
        S4["Flag as Pending Approval"]
        S5["Update Status to Approved"]
    end

    subgraph ManagerLane["Department Manager"]
        M1["Review Timesheet"]
        M2{"Approve?"}
    end

    Finish(["End Process"])

    Start --> E1 --> S1 --> S2 --> S3
    S3 -->|"Yes"| E3 --> E2
    S3 -->|"No"| E2 --> S4 --> M1
    
    M1 --> M2
    M2 -->|"No (Reject)"| E3
    M2 -->|"Yes (Approve)"| S5 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Employee | Ghi nhan thoi gian lam viec, sua chua sai sot, va xac nhan/nop timesheet vao cuoi ky. |
| 2 | System | Tu dong luu log cham cong, tinh toan so gio, phat hien loi va cap nhat trang thai sau cung. |
| 3 | Department Manager | Kiem tra, xac nhan va phe duyet (hoac tu choi) timesheet cua nhan vien thuoc pham vi quan ly. |
