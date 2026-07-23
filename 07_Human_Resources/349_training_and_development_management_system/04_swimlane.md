# Swimlane Diagram — Training and Development Management System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Enrollment"])

    subgraph EmployeeLane["Employee"]
        E1["Browse Catalog"]
        E2["Submit Enrollment Request"]
        E3["Receive Confirmation"]
    end

    subgraph SystemLane["Training System"]
        S1["Verify Prerequisites & Capacity"]
        S2{"Is Eligible?"}
        S3["Reject Enrollment"]
        S4["Save as Pending Approval"]
        S5["Update Enrollment Status"]
        S6["Send Final Notification"]
    end

    subgraph ManagerLane["Department Manager"]
        M1["Review Request & Budget"]
        M2{"Approve?"}
    end

    Finish(["End Enrollment Process"])

    Start --> E1 --> E2 --> S1
    S1 --> S2
    S2 -->|"No"| S3 --> E3
    S2 -->|"Yes"| S4 --> M1
    
    M1 --> M2
    M2 -->|"Yes (Approve)"| S5
    M2 -->|"No (Reject)"| S5
    
    S5 --> S6 --> E3 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Employee | Nguoi chon khoa hoc, tao don dang ky va cho nhan ket qua dang ky cuoi cung. |
| 2 | Training System | He thong kiem tra dieu kien tien quyet, suc chua cua lop, quan ly trang thai don, va gui thong bao email. |
| 3 | Department Manager | Nguoi quan ly xem xet su phu hop cua khoa hoc, ngan sach va ra quyet dinh duyet hoac tu choi. |
