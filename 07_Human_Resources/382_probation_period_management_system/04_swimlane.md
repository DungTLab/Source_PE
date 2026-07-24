# Swimlane Diagram — Probation Period Management System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Final Evaluation"])

    subgraph ProbationerLane["Probationary Employee"]
        E1["Submit Self-Evaluation"]
    end

    subgraph ManagerLane["Line Manager"]
        M1["Review Self-Evaluation & Mentor Feedback"]
        M2["Submit Final Review & Recommendation"]
    end

    subgraph SystemLane["Probation Period Management System"]
        S1["Notify Line Manager"]
        S2["Calculate Total Scores"]
        S3["Update Status to Pending HR Approval"]
        S4{"Is Result Passed?"}
        S5["Notify Payroll & Sync Data"]
        S6["Trigger Offboarding Process"]
    end

    subgraph HRLane["HR Manager"]
        H1["Review Final Recommendation"]
        H2{"Approve?"}
        H3["Finalize Decision"]
    end

    Finish(["End Evaluation"])

    Start --> E1 --> S1 --> M1
    M1 --> M2 --> S2 --> S3 --> H1
    H1 --> H2
    H2 -->|"Yes"| H3
    H2 -->|"No (Reject & Revise)"| M1
    
    H3 --> S4
    S4 -->|"Yes"| S5 --> Finish
    S4 -->|"No"| S6 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Probationary Employee | Nguoi chu dong nop bang tu danh gia de bat dau quy trinh danh gia cuoi ky. |
| 2 | Line Manager | Tiep nhan cac danh gia, thuc hien danh gia cuoi cung va dua ra de xuat (Pass/Fail/Extend). |
| 3 | Probation Period Management System | He thong xu ly logic, tinh toan diem so, gui thong bao va dong bo du lieu cho he thong khac (Payroll). |
| 4 | HR Manager | Nguoi kiem duyet cuoi cung, xac nhan de xuat cua Line Manager de chot ket qua thu viec. |
