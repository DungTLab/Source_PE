# Swimlane Diagram — Talent Management System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Evaluation Cycle"])

    subgraph HRLane["HR Manager"]
        H1["Initiate Performance Cycle"]
        H2["Monitor Overall Progress"]
    end

    subgraph SystemLane["Talent Management System"]
        S1["Send Notifications to Employees"]
        S2["Validate Form Submission"]
        S3{"Is Form Complete?"}
        S4["Notify Department Manager"]
        S5["Calculate Final Score"]
        S6["Archive Record"]
    end

    subgraph EmployeeLane["Employee"]
        E1["Receive Notification"]
        E2["Fill Self-Review Form"]
        E3["Submit Self-Review"]
    end

    subgraph ManagerLane["Department Manager"]
        M1["Review Employee Submission"]
        M2["Input Manager Ratings"]
        M3["Submit Final Review"]
    end

    Finish(["End Process"])

    Start --> H1 --> S1 --> E1
    E1 --> E2 --> E3 --> S2
    S2 --> S3
    
    S3 -->|"No"| E2
    S3 -->|"Yes"| S4 --> M1
    
    M1 --> M2 --> M3 --> S5
    S5 --> S6 --> H2 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | HR Manager | Nguoi khoi tao ky danh gia va theo doi toan bo tien do thuc hien tren quy mo toan cong ty. |
| 2 | Talent Management System | He thong quan ly luong, thong bao, tinh toan diem so va luu tru ban ghi phieu danh gia. |
| 3 | Employee | Nguoi nhan thong bao va chu dong hoan thanh bieu mau tu danh gia tren he thong. |
| 4 | Department Manager | Nguoi danh gia cuoi cung, dua ra diem so va nhan xet xac dang cho nhan vien thuoc quyen quan ly cua minh. |
