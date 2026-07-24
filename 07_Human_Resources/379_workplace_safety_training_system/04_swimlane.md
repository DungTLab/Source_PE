# Swimlane Diagram — Workplace Safety Training System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Training Process"])

    subgraph EmployeeLane["Employee"]
        E1["Login to System"]
        E2["Enroll in Course"]
        E3["Study Course Modules"]
        E4["Take Online Exam"]
        E5["Download Certificate"]
    end

    subgraph SystemLane["Workplace Safety Training System"]
        S1["Track Enrollment Status"]
        S2["Auto-grade Exam"]
        S3{"Passed?"}
        S4["Update Course to Incomplete"]
        S5["Generate Certificate"]
        S6["Update Compliance Record"]
    end

    subgraph ManagerLane["Safety Manager"]
        M1["Review Compliance Report"]
    end

    Finish(["End Process"])

    Start --> E1 --> E2 --> S1 --> E3 --> E4 --> S2
    S2 --> S3
    S3 -->|"No"| S4 --> E4
    S3 -->|"Yes"| S5 --> S6
    
    S6 --> M1
    S5 --> E5 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Employee | Nguoi tiep nhan khoa hoc, hoc cac module, lam bai kiem tra va tai chung chi sau khi dat. |
| 2 | Workplace Safety Training System | He thong theo doi tien do, tu dong cham diem thi, phat hanh chung chi va luu tru du lieu tuan thu. |
| 3 | Safety Manager | Nguoi quan ly nhan bao cao tuan thu sau khi he thong cap nhat ket qua cua nhan vien. |
