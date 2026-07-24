# Swimlane Diagram — Employee Recognition and Awards System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Nomination Process"])

    subgraph EmployeeLane["Employee"]
        E1["Login to System"]
        E2["Select Peer & Award Category"]
        E3["Submit Nomination Form"]
        E4["Receive Feedback"]
    end

    subgraph SystemLane["System"]
        S1["Validate Input & Budget"]
        S2{"Is Valid?"}
        S3["Show Error Message"]
        S4["Save Pending & Notify Manager"]
        S5["Update Status & Add Points"]
        S6["Send Award Certificate Email"]
    end

    subgraph ManagerLane["Department Manager"]
        M1["Review Nomination"]
        M2{"Approve?"}
    end

    Finish(["End Process"])

    Start --> E1 --> E2 --> E3 --> S1
    S1 --> S2
    S2 -->|"No"| S3 --> E2
    S2 -->|"Yes"| S4 --> M1
    
    M1 --> M2
    M2 -->|"No (Reject)"| S5
    M2 -->|"Yes (Approve)"| S5
    
    S5 --> S6 --> E4 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Employee | Nguoi khoi tao yeu cau de cu dong nghiep, nhap ly do va chon loai giai thuong phu hop. |
| 2 | System | He thong kiem tra ngan sach, cap nhat trang thai don, cong diem vao vi nguoi nhan va phat hanh the ghi nhan (email). |
| 3 | Department Manager | Nguoi quan ly nhan thong bao va xet duyet tinh xung dang cua phieu de cu. |
