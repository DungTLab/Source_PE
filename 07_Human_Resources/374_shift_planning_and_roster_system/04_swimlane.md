# Swimlane Diagram — Shift Planning and Roster System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Shift Swap"])

    subgraph EmployeeLane["Employee"]
        E1["Select Assigned Shift"]
        E2["Submit Swap Request"]
        E3["Receive Approval Status"]
    end

    subgraph SystemLane["Shift Planning and Roster System"]
        S1["Validate Swap Rules"]
        S2{"Is Request Valid?"}
        S3["Show Error Message"]
        S4["Notify Target Colleague & Planner"]
        S5["Update Roster"]
        S6["Send Final Notification"]
    end

    subgraph PlannerLane["Shift Planner"]
        M1["Review Swap Request"]
        M2{"Approve?"}
    end

    Start --> E1 --> E2 --> S1
    S1 --> S2
    S2 -->|"No"| S3 --> E2
    S2 -->|"Yes"| S4 --> M1
    
    M1 --> M2
    M2 -->|"Yes"| S5
    M2 -->|"No"| S5
    
    S5 --> S6 --> E3 --> Finish(["End Process"])
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Employee | Nguoi chu dong chon ca va tao yeu cau doi ca tren he thong. Nhan ket qua xu ly cuoi cung. |
| 2 | Shift Planning and Roster System | He thong tu dong kiem tra quy tac, gui email/SMS thong bao, cap nhat lai lich neu yeu cau duoc duyet. |
| 3 | Shift Planner | Xem xet cac yeu cau doi ca hop le, ra quyet dinh dong y hoac tu choi de dam bao hoat dong. |
