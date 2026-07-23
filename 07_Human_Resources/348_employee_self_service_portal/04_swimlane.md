# Swimlane Diagram — Employee Self-Service Portal

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Expense Claim"])

    subgraph EmployeeLane["Employee"]
        E1["Login to Portal"]
        E2["Fill Expense Form"]
        E3["Upload Receipts & Submit"]
        E4["Receive Claim Status"]
    end

    subgraph PortalLane["Employee Self-Service Portal"]
        S1["Validate Data"]
        S2{"Is Data Valid?"}
        S3["Show Error Message"]
        S4["Save Claim as Pending & Notify Manager"]
        S5["Update Status to Approved/Rejected"]
        S6["Send Email Notification"]
    end

    subgraph ManagerLane["Department Manager"]
        M1["Review Expense Claim"]
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
| 1 | Employee | Nguoi nop don thanh toan chi phi, tai len chung tu va nhan thong bao cuoi cung. |
| 2 | Employee Self-Service Portal | He thong kiem tra du lieu, luu trang thai don va tu dong gui email dieu phuoi quy trinh. |
| 3 | Department Manager | Nguoi kiem tra tinh hop le cua khoan chi va ra quyet dinh phe duyet. |
