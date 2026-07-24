# Swimlane Diagram — Headcount Planning System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Process"])

    subgraph DeptManagerLane["Department Manager"]
        D1["Create Headcount Request"]
        D2["Submit Request"]
    end

    subgraph SystemLane["Headcount Planning System"]
        S1["Validate Data"]
        S2{"Is Data Valid?"}
        S3["Show Error Message"]
        S4["Update Status to Pending HR"]
        S5["Update Status to Pending Finance"]
        S6["Mark as Fully Approved"]
    end

    subgraph HRLane["HR Manager"]
        H1["Review HR Alignment"]
        H2{"Approve HR?"}
    end

    subgraph FinanceLane["Finance Manager"]
        F1["Review Budget Impact"]
        F2{"Approve Budget?"}
    end

    Finish(["End Process"])

    Start --> D1 --> D2 --> S1
    S1 --> S2
    S2 -->|"No"| S3 --> D1
    S2 -->|"Yes"| S4 --> H1
    
    H1 --> H2
    H2 -->|"No"| S3
    H2 -->|"Yes"| S5 --> F1
    
    F1 --> F2
    F2 -->|"No"| S3
    F2 -->|"Yes"| S6 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Department Manager | Nguoi chu dong tao va nop yeu cau bo sung nhan su cho phong ban minh. |
| 2 | Headcount Planning System | He thong kiem tra tinh hop le cua don, cap nhat trang thai tung buoc va chuyen tiep cho cac ben lien quan. |
| 3 | HR Manager | Kiem tra yeu cau co phu hop voi chinh sach nhan su hay khong truoc khi den buoc tai chinh. |
| 4 | Finance Manager | Nguoi xet duyet cuoi cung ve mat ngan sach va chi phi cho yeu cau nhan su. |
