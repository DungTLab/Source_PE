# Swimlane Diagram — Organizational Chart Management System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Restructure"])

    subgraph DeptLane["Department Head"]
        D1["Create Draft Proposal"]
        D2["Submit Proposal"]
        D3["Receive Final Decision"]
    end

    subgraph SystemLane["Organizational Chart System"]
        S1["Validate Draft Integrity"]
        S2{"Is Valid?"}
        S3["Display Error"]
        S4["Change Status to Pending"]
        S5["Update Final Status"]
    end

    subgraph HRLane["HR Manager"]
        H1["Review Proposal"]
        H2{"Approve?"}
    end

    Finish(["End Process"])

    Start --> D1 --> D2 --> S1
    S1 --> S2
    S2 -->|"No"| S3 --> D1
    S2 -->|"Yes"| S4 --> H1

    H1 --> H2
    H2 -->|"Yes"| S5
    H2 -->|"No"| S5

    S5 --> D3 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Department Head | Truong phong tao ban nhap (draft), chinh sua va de xuat thay doi co cau. Nhan ket qua phe duyet. |
| 2 | Organizational Chart System | He thong kiem tra tinh toan ven cua de xuat (khong loop, du thong tin) va luu tru trang thai. |
| 3 | HR Manager | Quan ly nhan su xem xet muc do phu hop, ngan sach va dua ra quyet dinh duyet/tu choi. |
