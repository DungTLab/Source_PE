# Swimlane Diagram — Religious Organization Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Congregant / Member"]
        C1["Register Household Profile & Contact"]
        C2["Request Sacrament & Service Schedule"]
        C3["Submit Online Tithe / Offering"]
        C4["Sign Up for Volunteer Ministry Role"]
    end

    subgraph Lane2["System"]
        S1["Create Member Record & Link Household"]
        S2["Check Sanctuary & Clergy Schedule"]
        S3{"Online Donation Selected?"}
        S4["Route Encrypted Tithe Payload"]
        S5["Record Tithe & Issue Tax Receipt"]
        S6["Assign Volunteer Roster & Send Alert"]
    end

    subgraph Lane3["Payment Gateway"]
        P1["Process Payment Card / ACH"]
        P2["Return Transaction Settlement Code"]
    end

    subgraph Lane4["Clergy Leader"]
        L1["Review Sacrament & Officiate Service"]
        L2["Issue Official Sacrament Certificate"]
    end

    Finish(["End"])

    Start --> C1 --> S1 --> C2 --> S2 --> L1 --> L2 --> C3 --> S3
    S3 -->|"Yes"| S4 --> P1 --> P2 --> S5 --> C4 --> S6 --> Finish
    S3 -->|"No"| S5
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Congregant / Member | Registers profile and family household, requests sacrament appointments, submits online tithes/pledges, and volunteers for ministry shifts. |
| 2 | System | Automates household linking, checks venue/clergy schedules, routes encrypted payment payloads, records tax-deductible receipts, and manages ministry rosters. |
| 3 | Payment Gateway | Processes electronic credit card and ACH bank tithe transactions and returns settlement confirmation tokens. |
| 4 | Clergy Leader | Evaluates sacrament requests, officiates worship services, logs pastoral care notes, and approves official religious certificates. |
