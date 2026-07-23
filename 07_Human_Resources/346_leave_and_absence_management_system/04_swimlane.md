# Swimlane Diagram — Leave and Absence Management System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Request Process"])

    subgraph EmployeeLane["Employee"]
        E1["Login to System"]
        E2["Select Leave Type & Dates"]
        E3["Submit Leave Request"]
        E4["Receive Notification"]
    end

    subgraph SystemLane["Leave and Absence Management System"]
        S1["Check Leave Balance"]
        S2{"Balance Valid?"}
        S3["Show Error Message"]
        S4["Change Status to Pending"]
        S5["Notify Department Manager"]
        S6["Update Balance & Status"]
        S7["Send Final Notification"]
    end

    subgraph ManagerLane["Department Manager"]
        M1["Review Pending Request"]
        M2{"Approve?"}
    end

    Finish(["End Process"])

    Start --> E1 --> E2 --> E3 --> S1
    S1 --> S2
    S2 -->|"No"| S3 --> E2
    S2 -->|"Yes"| S4 --> S5 --> M1
    
    M1 --> M2
    M2 -->|"Yes"| S6
    M2 -->|"No"| S6
    
    S6 --> S7 --> E4 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Employee | Nguoi chu dong chon ngay, loai phep de nop don va nhan thong bao ket qua cuoi cung. |
| 2 | Leave and Absence Management System | He thong kiem tra quy phep hop le, quan ly trang thai, tru phep khi duyet va gui thong bao. |
| 3 | Department Manager | Nguoi quan ly nhan thong bao, xem xet li do va dua ra quyet dinh phe duyet hoac tu choi. |
