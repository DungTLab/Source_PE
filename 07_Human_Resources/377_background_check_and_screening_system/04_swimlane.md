# Swimlane Diagram — Background Check and Screening System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Background Check"])

    subgraph HRManagerLane["HR Manager"]
        H1["Initiate Request"]
        H2["Review Final Report"]
        H3{"Clear candidate?"}
    end

    subgraph SystemLane["Background Check and Screening System"]
        S1["Notify Candidate for Consent"]
        S2["Validate Documents"]
        S3["Send Data to Agency"]
        S4["Compile Screening Results"]
        S5["Update Candidate Status"]
    end

    subgraph CandidateLane["Candidate"]
        C1["Submit Consent & Docs"]
    end
    
    subgraph AgencyLane["Third-Party Screening Agency"]
        A1["Process Verifications"]
        A2["Return Results"]
    end

    Finish(["End Process"])

    Start --> H1 --> S1 --> C1 --> S2 --> S3 --> A1 --> A2 --> S4 --> H2
    H2 --> H3
    H3 -->|"Yes"| S5
    H3 -->|"No"| S5
    S5 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | HR Manager | Nguoi bat dau quy trinh kiem tra, doc ket qua tong hop va dua ra quyet dinh cuoi cung. |
| 2 | Background Check and Screening System | He thong dieu pho luong, xac thuc du lieu, ket noi voi ben thu ba va tong hop bao cao. |
| 3 | Candidate | Ung vien nhan thong bao, cung cap su dong y phap ly va nop giay to xac minh. |
| 4 | Third-Party Screening Agency | Ben thu ba tiep nhan yeu cau, thuc hien kiem tra ly lich va tra ket qua ve he thong. |
