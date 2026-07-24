# Swimlane Diagram — HR Audit and Compliance System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Audit Execution"])

    subgraph AuditorLane["Auditor"]
        A1["Initiate Audit Request"]
        A2["Review Audit Findings"]
    end

    subgraph SystemLane["HR Audit and Compliance System"]
        S1["Fetch HR Data from HRMS"]
        S2["Apply Audit Rules"]
        S3{"Any Compliance Breach?"}
        S4["Log Breach & Alert"]
        S5["Generate Clean Report"]
    end

    subgraph LegalLane["Legal Department"]
        L1["Review Severe Breaches"]
        L2["Provide Legal Advice"]
    end

    Finish(["End Process"])

    Start --> A1 --> S1 --> S2 --> S3
    S3 -->|"Yes"| S4 --> L1
    S3 -->|"No"| S5 --> A2
    
    L1 --> L2 --> A2
    A2 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Auditor | Nguoi chu dong khoi chay qua trinh kiem toan va xem xet ket qua cuoi cung. |
| 2 | HR Audit and Compliance System | He thong lay du lieu, ap dung quy tac, xac dinh vi pham va tu dong phan luong canh bao. |
| 3 | Legal Department | Phong ban tiep nhan thong bao ve cac vi pham tuan thu nghiem trong de dua ra tu van phap ly. |
