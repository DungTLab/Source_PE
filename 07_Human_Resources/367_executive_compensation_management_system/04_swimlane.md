# Swimlane Diagram — Executive Compensation Management System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Plan Design"])

    subgraph ManagerLane["Compensation Manager"]
        M1["Login & Create Draft Plan"]
        M2["Configure Bonuses & Stocks"]
        M3["Submit Plan for Approval"]
        M4["Revise Plan"]
    end

    subgraph SystemLane["Executive Compensation Management System"]
        S1["Validate Plan Details"]
        S2{"Is Data Valid?"}
        S3["Show Error Message"]
        S4["Change Status to Pending & Notify Board"]
        S5["Update Status & Notify Manager"]
    end

    subgraph BoardLane["Board of Directors"]
        B1["Review Compensation Plan"]
        B2{"Approve?"}
    end

    Finish(["End Process"])

    Start --> M1 --> M2 --> M3 --> S1
    S1 --> S2
    S2 -->|"No"| S3 --> M2
    S2 -->|"Yes"| S4 --> B1
    
    B1 --> B2
    B2 -->|"Yes (Approve)"| S5
    B2 -->|"No (Reject)"| S5
    
    S5 --> Finish
    S5 -.->|"If Rejected"| M4 -.-> M3
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Compensation Manager | Nguoi thiet ke che do luong thuong va gui yeu cau phe duyet len Hoi dong quan tri. |
| 2 | Executive Compensation Management System | He thong kiem tra tinh hop le cua thong tin, cap nhat trang thai va gui thong bao. |
| 3 | Board of Directors | Xem xet va quyet dinh phe duyet hoac tu choi ke hoach luong thuong cua lanh dao. |
