# Swimlane Diagram — Succession Planning System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start"])

    subgraph Lane1["Department Manager"]
        M1["Identify Potential Candidate"]
        M2["Submit Nomination & Eval"]
    end

    subgraph Lane2["System"]
        S1["Notify HR Manager"]
        S2["Validate Nomination"]
        S3{"Meets Criteria?"}
        S4["Add to Talent Pool"]
        S5["Reject Nomination"]
        S6["Update Succession Plan"]
    end

    subgraph Lane3["HR Manager"]
        H1["Review Candidate Profile"]
        H2["Rank Candidate in Plan"]
    end

    subgraph Lane4["Executive"]
        E1["Review Succession Plan"]
        E2{"Approved?"}
    end

    Finish(["End"])

    Start --> M1 --> M2 --> S2 --> S3
    S3 -->|"No"| S5 --> Finish
    S3 -->|"Yes"| S4 --> S1 --> H1 --> H2 --> S6 --> E1 --> E2
    E2 -->|"Yes"| Finish
    E2 -->|"No"| H1
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Department Manager | Phat hien nhan tai, thuc hien de cu va danh gia nang luc ban dau |
| 2 | System | Kiem tra dieu kien, cap nhat trang thai va gui cac thong bao lien quan |
| 3 | HR Manager | Kiem tra ho so ung vien, dua vao nhom tai nang va xep hang trong ke hoach ke nhiem |
| 4 | Executive | Xem xet va phe duyet ke hoach ke nhiem do HR de xuat |
