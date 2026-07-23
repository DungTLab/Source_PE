# Swimlane Diagram — Performance Appraisal System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Appraisal Cycle"])

    subgraph HRManagerLane["HR Manager"]
        H1["Create & Activate Cycle"]
        H2["Monitor Progress"]
        H3["Finalize Results & Export"]
    end

    subgraph SystemLane["Performance Appraisal System"]
        S1["Notify Employees"]
        S2["Save Draft / Finalize Form"]
        S3["Notify Manager"]
        S4["Calculate Final Scores"]
        S5["Publish Final Results"]
    end

    subgraph EmployeeLane["Employee"]
        E1["Receive Notification"]
        E2["Submit Self-Appraisal"]
        E3["Acknowledge Results"]
    end

    subgraph ManagerLane["Manager"]
        M1["Review Self-Appraisal"]
        M2["Conduct Manager Appraisal"]
    end

    Finish(["End Cycle"])

    Start --> H1 --> S1 --> E1
    E1 --> E2 --> S2
    S2 -->|"Form Submitted"| S3 --> M1
    M1 --> M2 --> S4
    S4 --> H2 --> H3 --> S5 --> E3 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | HR Manager | Nguoi khoi tao ky danh gia, theo doi tien do chung va chot ket qua cuoi cung. |
| 2 | Performance Appraisal System | He thong xu ly logic, luu tru du lieu, tinh toan diem so va gui thong bao tu dong. |
| 3 | Employee | Nhan vien thuc hien viec tu danh gia tren he thong va xac nhan ket qua cuoi cung. |
| 4 | Manager | Quan ly truc tiep xem xet phieu tu danh gia va cham diem, dua ra nhan xet cho nhan vien. |
