# Swimlane Diagram — Health and Safety Incident Reporting System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start"])

    subgraph EmployeeLane["Employee"]
        E1["Login & Report Incident"]
        E2["Receive Updates"]
    end

    subgraph SystemLane["System"]
        S1["Validate Report"]
        S2{"Is Report Valid?"}
        S3["Return Error"]
        S4["Save & Notify Roles"]
        S5["Update Status"]
    end

    subgraph OfficerLane["Safety Officer"]
        O1["Review Incident"]
        O2{"Requires Investigation?"}
        O3["Investigate & Add Actions"]
        O4["Close Incident directly"]
    end

    Finish(["End"])

    Start --> E1 --> S1
    S1 --> S2
    S2 -->|"No"| S3 --> E1
    S2 -->|"Yes"| S4 --> O1

    O1 --> O2
    O2 -->|"Yes"| O3 --> S5
    O2 -->|"No"| O4 --> S5

    S5 --> E2 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Employee | Nguoi chu dong bao cao su co, nhap thong tin va nhan cap nhat ve qua trinh xu ly. |
| 2 | System | He thong kiem tra tinh hop le, luu tru, va thong bao cho cac ben lien quan. |
| 3 | Safety Officer | Nhan vien an toan tiep nhan bao cao, quyet dinh dieu tra hoac dong su co, va tao hanh dong khac phuc. |
