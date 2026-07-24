# Swimlane Diagram — Contractor and Freelancer Management System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Invoice Process"])

    subgraph ContractorLane["Contractor"]
        C1["Login to System"]
        C2["Select Approved Timesheets"]
        C3["Submit Invoice"]
        C4["Receive Payment Confirmation"]
    end

    subgraph SystemLane["Contractor and Freelancer Management System"]
        S1["Validate Invoice Total"]
        S2{"Is Total Valid?"}
        S3["Show Error Message"]
        S4["Save as Pending & Notify PM"]
        S5["Update Status to Approved"]
        S6["Trigger Payment Gateway"]
        S7["Send Final Email Notification"]
    end

    subgraph ManagerLane["Project Manager"]
        M1["Review Invoice Details"]
        M2{"Approve?"}
    end

    Finish(["End Process"])

    Start --> C1 --> C2 --> C3 --> S1
    S1 --> S2
    S2 -->|"No"| S3 --> C2
    S2 -->|"Yes"| S4 --> M1
    
    M1 --> M2
    M2 -->|"Yes (Approve)"| S5
    M2 -->|"No (Reject)"| S5
    
    S5 --> S6 --> S7 --> C4 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Contractor | Nguoi chu dong tao va nop hoa don dua tren bang cham cong da duyet, va nhan thong bao ket qua. |
| 2 | Contractor and Freelancer Management System | He thong kiem tra tinh hop le cua hoa don, quan ly trang thai, va goi cong thanh toan neu duoc duyet. |
| 3 | Project Manager | Nguoi quan ly nhan duoc thong bao, vao he thong de xem xet chi tiet va phe duyet/tu choi hoa don. |
