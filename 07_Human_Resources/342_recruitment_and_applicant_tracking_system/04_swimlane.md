# Swimlane Diagram — Recruitment & Applicant Tracking System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Screening"])

    subgraph RecruiterLane["Recruiter"]
        R1["Review Candidate Resume"]
        R2{"Shortlist?"}
        R3["Schedule Interview"]
        R4["Create Job Offer"]
    end

    subgraph SystemLane["Applicant Tracking System"]
        S1["Update Status: Rejected"]
        S2["Send Rejection Email"]
        S3["Send Interview Invite"]
        S4["Collect Feedback Form"]
    end

    subgraph HiringManagerLane["Hiring Manager"]
        H1["Conduct Interview"]
        H2["Submit Feedback"]
        H3{"Passed?"}
    end

    subgraph CandidateLane["Candidate"]
        C1["Accept Invite"]
        C2["Attend Interview"]
    end

    Start --> R1 --> R2
    R2 -->|"No"| S1 --> S2 --> FinishReject(["End Process"])
    R2 -->|"Yes"| R3 --> S3 --> C1 --> C2 --> H1
    
    H1 --> H2 --> S4 --> H3
    H3 -->|"No"| S1
    H3 -->|"Yes"| R4 --> FinishOffer(["Offer Pending"])
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Recruiter | Danh gia CV, quyet dinh loai hoac chon ung vien, sap xep lich phong van va len don Offer. |
| 2 | Applicant Tracking System | Tu dong hoa luong cong viec, cap nhat trang thai va gui email lien lac toi ung vien. |
| 3 | Candidate | Nhan email xac nhan, tham gia phong van cung phia cong ty. |
| 4 | Hiring Manager | Truc tiep phong van, ghi nhan danh gia/diem so len he thong de ra quyet dinh cuoi cung. |
