# Swimlane Diagram — Expense Reimbursement System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Claim Process"])

    subgraph EmployeeLane["Employee"]
        E1["Submit Claim & Receipts"]
        E2["Receive Rejection"]
        E3["Receive Payment Confirmation"]
    end

    subgraph SystemLane["Expense Reimbursement System"]
        S1["Validate Claim Data"]
        S2{"Is Data Valid?"}
        S3["Return Error"]
        S4["Save as Pending & Notify Manager"]
        S5["Update to Pending Audit & Notify Finance"]
        S6["Update to Paid & Notify Employee"]
    end

    subgraph ManagerLane["Manager"]
        M1["Review Claim"]
        M2{"Approve?"}
    end
    
    subgraph FinanceLane["Finance Officer"]
        F1["Audit Claim"]
        F2{"Policy Matched?"}
        F3["Process Payment"]
    end

    Finish(["End Process"])

    Start --> E1 --> S1
    S1 --> S2
    S2 -->|"No"| S3 --> E1
    S2 -->|"Yes"| S4 --> M1
    
    M1 --> M2
    M2 -->|"No"| E2
    M2 -->|"Yes"| S5 --> F1
    
    F1 --> F2
    F2 -->|"No"| E2
    F2 -->|"Yes"| F3 --> S6 --> E3 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Employee | Nguoi nop don hoan tien cung cac hoa don va nhan thong bao ket qua cuoi cung. |
| 2 | Expense Reimbursement System | He thong kiem tra du lieu, dieu phoi luong trang thai va gui thong bao toi cac ben lien quan. |
| 3 | Manager | Kiem tra su phu hop cua chi phi voi muc tieu cong viec va duyet don cho nhan vien thuoc quyen. |
| 4 | Finance Officer | Kiem toan don dua tren chinh sach tai chinh, kiem tra hoa don va thuc hien thanh toan thuc te. |
