# Swimlane Diagram — Sick Leave and Medical Certificate System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Request"])

    subgraph EmployeeLane["Employee"]
        E1["Fill Sick Leave Form"]
        E2{"Duration > 2 days?"}
        E3["Upload Medical Certificate"]
        E4["Submit Request"]
        E5["Receive Status Update"]
    end

    subgraph SystemLane["Sick Leave System"]
        S1["Check Leave Balance"]
        S2["Save Request as Pending"]
        S3["Notify HR Manager"]
        S4["Update Leave Balance"]
        S5["Send Final Email"]
    end

    subgraph HRLane["HR Manager"]
        H1["Review Sick Leave Request"]
        H2{"Has Certificate?"}
        H3["Verify Certificate Authenticity"]
        H4{"Approve?"}
    end

    Start --> E1 --> E2
    E2 -->|"Yes"| E3 --> E4
    E2 -->|"No"| E4
    
    E4 --> S1 --> S2 --> S3 --> H1
    
    H1 --> H2
    H2 -->|"Yes"| H3 --> H4
    H2 -->|"No"| H4
    
    H4 -->|"Yes (Approve)"| S4
    H4 -->|"No (Reject)"| S5
    
    S4 --> S5 --> E5 --> Finish(["End Request"])
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Employee | Nguoi chu dong nop don xin nghi om va cung cap giay chung nhan y te neu can. |
| 2 | Sick Leave System | He thong kiem tra so ngay phep, luu tru don, tru phep va gui email thong bao den cac ben. |
| 3 | HR Manager | Nhan su kiem tra the le, xac thuc tinh hop le cua giay kham benh va dua ra quyet dinh duyet. |
