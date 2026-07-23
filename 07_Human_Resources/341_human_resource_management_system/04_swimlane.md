# Swimlane Diagram — Human Resource Management System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Leave Process"])

    subgraph EmployeeLane["Employee"]
        E1["Login to System"]
        E2["Fill Leave Form"]
        E3["Submit Leave Request"]
        E4["Receive Notification"]
    end

    subgraph SystemLane["Human Resource Management System"]
        S1["Validate Leave Balance"]
        S2{"Is Balance Valid?"}
        S3["Show Error Message"]
        S4["Save as Pending & Notify Manager"]
        S5["Update Status & Leave Balance"]
        S6["Send Final Email Notification"]
    end

    subgraph ManagerLane["Department Manager"]
        M1["Review Leave Request"]
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
| 1 | Employee | Nguoi chu dong nop don xin nghi phep tren he thong va nhan ket qua cuoi cung. |
| 2 | Human Resource Management System | He thong kiem tra tinh hop le, luu tru trang thai, tru ngay phep va gui email thong bao cac ben. |
| 3 | Department Manager | Nguoi quan ly nhan duoc thong bao, vao he thong de xem xet va ra quyet dinh phe duyet hoac tu choi don. |
