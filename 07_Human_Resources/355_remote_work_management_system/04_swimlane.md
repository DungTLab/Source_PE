# Swimlane Diagram — Remote Work Management System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Request Process"])

    subgraph EmployeeLane["Employee"]
        E1["Login to System"]
        E2["Submit Remote Request"]
        E3["Receive Final Status"]
    end

    subgraph SystemLane["Remote Work Management System"]
        S1["Verify Remote Policy Quota"]
        S2{"Quota Available?"}
        S3["Reject Request Automatically"]
        S4["Change Status to Pending"]
        S5["Update Database & Send Notification"]
    end

    subgraph ManagerLane["Department Manager"]
        M1["Review Pending Request"]
        M2{"Approve?"}
    end

    Finish(["End Process"])

    Start --> E1 --> E2 --> S1
    S1 --> S2
    S2 -->|"No"| S3 --> E3
    S2 -->|"Yes"| S4 --> M1
    
    M1 --> M2
    M2 -->|"Yes"| S5
    M2 -->|"No"| S5
    
    S5 --> E3 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Employee | Nguoi chu dong tao yeu cau lam viec tu xa tren he thong va nhan thong bao ket qua. |
| 2 | Remote Work Management System | He thong tu dong kiem tra dieu kien chinh sach (so ngay con lai), quan ly trang thai va thong bao. |
| 3 | Department Manager | Nguoi quan ly nhan duoc thong bao, vao xem xet va ra quyet dinh duyet hoac tu choi yeu cau. |
