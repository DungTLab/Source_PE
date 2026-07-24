# Swimlane Diagram — Bonus and Incentive Management System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Recommendation"])

    subgraph DeptLane["Department Manager"]
        D1["Login to System"]
        D2["Create Bonus Recommendation"]
        D3["Submit to HR"]
    end

    subgraph SystemLane["Bonus & Incentive System"]
        S1["Verify Budget Limit"]
        S2{"Is Budget Valid?"}
        S3["Show Budget Exceeded Error"]
        S4["Save as Pending & Notify HR"]
        S5["Update Status & Deduct Budget"]
        S6["Send Payout Data to Payroll"]
    end

    subgraph HRLane["HR Manager"]
        H1["Review Pending Recommendations"]
        H2{"Approve?"}
    end

    Finish(["End Process"])

    Start --> D1 --> D2 --> D3 --> S1
    S1 --> S2
    S2 -->|"No"| S3 --> D2
    S2 -->|"Yes"| S4 --> H1
    
    H1 --> H2
    H2 -->|"Yes (Approve)"| S5
    H2 -->|"No (Reject)"| S5
    
    S5 --> S6 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Department Manager | Nguoi chu dong de xuat cac khoan thuong cho nhan vien trong ngan sach cho phep. |
| 2 | Bonus & Incentive System | He thong kiem tra tinh hop le cua ngan sach, luu tru, chuyen trang thai, va dong bo du lieu cho tinh luong. |
| 3 | HR Manager | Nguoi quan ly nhan su kiem tra va ra quyet dinh phe duyet cuoi cung. |
