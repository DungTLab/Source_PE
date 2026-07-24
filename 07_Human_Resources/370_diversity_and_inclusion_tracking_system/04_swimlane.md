# Swimlane Diagram — Diversity and Inclusion Tracking System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Incident Reporting"])

    subgraph EmployeeLane["Employee"]
        E1["Login to System"]
        E2["Fill Incident Report Form"]
        E3["Submit Report"]
        E4["Receive Resolution Notification"]
    end

    subgraph SystemLane["Diversity and Inclusion Tracking System"]
        S1["Validate Form Data"]
        S2{"Is Data Valid?"}
        S3["Show Error & Prompt Revision"]
        S4["Save Report securely & Anonymize (if requested)"]
        S5["Notify Diversity Officer"]
        S6["Update Report Status"]
        S7["Send Notification to Employee"]
    end

    subgraph OfficerLane["Diversity Officer"]
        O1["Review Incident Details"]
        O2{"Requires Action?"}
        O3["Initiate Investigation/Mediation"]
        O4["Close Report with Notes"]
    end

    Finish(["End Reporting Process"])

    Start --> E1 --> E2 --> E3 --> S1
    S1 --> S2
    S2 -->|"No"| S3 --> E2
    S2 -->|"Yes"| S4 --> S5 --> O1
    
    O1 --> O2
    O2 -->|"Yes"| O3 --> S6
    O2 -->|"No"| O4 --> S6
    
    S6 --> S7 --> E4 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Employee | Nguoi chu dong bao cao mot su co lien quan toi van de thieu hoa nhap, phan biet hoac bat cong. |
| 2 | Diversity and Inclusion Tracking System | He thong kiem tra tinh hop le, bao mat du lieu (co the an danh hoa), luu tru va tu dong thong bao cac ben. |
| 3 | Diversity Officer | Chuyen vien chiu trach nhiem xem xet bao cao, quyet dinh co can tien hanh dieu tra hoac hoa giai khong, va dong bao cao sau khi xu ly. |
