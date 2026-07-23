# Swimlane Diagram — Employee Referral Program System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Application Process"])

    subgraph EmployeeLane["Employee"]
        E1["Generate Referral Link"]
        E2["Share Link with Candidate"]
        E3["Check Referral Status"]
        E4["Receive Bonus Notification"]
    end

    subgraph CandidateLane["Referred Candidate"]
        C1["Open Link"]
        C2["Submit Application"]
    end

    subgraph SystemLane["System"]
        S1["Track Link Usage"]
        S2["Save Application Data"]
        S3{"Is Application Valid?"}
        S4["Notify HR & Employee"]
        S5["Update Status to Rejected"]
        S6["Calculate & Approve Bonus"]
    end

    subgraph HRLane["HR Recruiter"]
        H1["Review Application"]
        H2{"Shortlist Candidate?"}
    end

    Finish(["End Process"])

    Start --> E1 --> E2 --> C1 --> C2 --> S1 --> S2 --> S3
    
    S3 -->|"No"| S5 --> Finish
    S3 -->|"Yes"| S4 --> H1
    
    H1 --> H2
    H2 -->|"No"| S5
    H2 -->|"Yes (Hired)"| S6 --> E4 --> E3 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Employee | Nguoi tao link, gui cho ung vien va theo doi trang thai de nhan thuong. |
| 2 | Referred Candidate | Nguoi su dung link de nop don ung tuyen vao he thong. |
| 3 | System | He thong theo doi link, kiem tra form hop le, cap nhat trang thai va tinh thuong. |
| 4 | HR Recruiter | Nguoi xem xet ho so do he thong gui toi va ra quyet dinh tuyen dung. |
