# Swimlane Diagram — Skills Inventory and Competency Management System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Assessment Process"])

    subgraph EmployeeLane["Employee"]
        E1["Login to System"]
        E2["Complete Self-Assessment Form"]
        E3["Submit Assessment"]
        E4["View Final Results"]
    end

    subgraph SystemLane["Skills Inventory and Competency Management System"]
        S1["Save Self-Assessment Draft"]
        S2["Calculate Initial Skill Gap"]
        S3["Notify Department Manager"]
        S4["Update Employee Skill Profile"]
        S5["Generate Training Recommendations"]
    end

    subgraph ManagerLane["Department Manager"]
        M1["Review Self-Assessment"]
        M2{"Agree with Rating?"}
        M3["Adjust Competency Rating"]
        M4["Approve Skill Validation"]
    end

    Start --> E1 --> E2 --> E3 --> S1
    S1 --> S2 --> S3 --> M1
    
    M1 --> M2
    M2 -->|"No"| M3 --> M4
    M2 -->|"Yes"| M4
    
    M4 --> S4 --> S5 --> E4
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Employee | Nguoi chu dong vao he thong thuc hien tu danh gia nang luc ca nhan minh so voi yeu cau cong viec. |
| 2 | Skills Inventory and Competency Management System | He thong luu tru thong tin, tinh toan khoang trong ky nang (skill gap), gui thong bao va tu dong de xuat cac khoa dao tao. |
| 3 | Department Manager | Nguoi quan ly nhan thong bao, xem xet diem tu danh gia cua nhan vien, dieu chinh neu can va xac nhan ket qua cuoi cung. |
