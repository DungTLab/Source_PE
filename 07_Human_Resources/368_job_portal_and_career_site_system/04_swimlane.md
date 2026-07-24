# Swimlane Diagram — Job Portal and Career Site System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Application Process"])

    subgraph JobSeekerLane["Job Seeker"]
        J1["Login & Search Jobs"]
        J2["Select Job & Apply"]
        J3["Receive Status Update"]
    end

    subgraph SystemLane["Job Portal System"]
        S1["Verify Job Status"]
        S2{"Is Job Open?"}
        S3["Reject Application"]
        S4["Save Application & Notify Employer"]
        S5["Update Application Status"]
    end

    subgraph EmployerLane["Employer"]
        E1["Review Candidate Application"]
        E2{"Accept Candidate?"}
    end

    Finish(["End Process"])

    Start --> J1 --> J2 --> S1
    S1 --> S2
    S2 -->|"No"| S3 --> Finish
    S2 -->|"Yes"| S4 --> E1
    
    E1 --> E2
    E2 -->|"Yes (Shortlist/Interview)"| S5
    E2 -->|"No (Reject)"| S5
    
    S5 --> J3 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Job Seeker | Nguoi dung chu dong tim kiem cong viec, nop don ung tuyen va theo doi ket qua. |
| 2 | Job Portal System | He thong kiem tra tinh trang cong viec, luu tru don ung tuyen va dieu phoi thong bao giua cac ben. |
| 3 | Employer | Nha tuyen dung nhan thong bao, xem xet ho so ung vien va quyet dinh thay doi trang thai ung tuyen. |
