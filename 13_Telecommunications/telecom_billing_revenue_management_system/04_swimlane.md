# Swimlane Diagram — Telecom Billing & Revenue Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Subscriber"]
        L1_S1["Accesses billing portal"]
        L1_S2["Selects unpaid invoice"]
        L1_S3["Submits payment details"]
        L1_S4["Receives digital receipt"]
    end

    subgraph Lane2["Telecom System"]
        L2_S1["Validates invoice status"]
        L2_S2["Routes to Payment Gateway"]
        L2_S3["Updates account balance"]
        L2_S4["Triggers confirmation SMS"]
        Decision{"Validation OK?"}
    end

    subgraph Lane3["Payment Gateway"]
        L3_S1["Verifies credit card"]
        L3_S2["Executes fund transfer"]
        L3_S3["Returns auth confirmation"]
    end

    Finish(["End"])

    Start --> L1_S1
    L1_S1 --> L1_S2 --> L2_S1 --> Decision
    Decision -->|"Yes"| L2_S2 --> L3_S1 --> L3_S2 --> L2_S3 --> L1_S4 --> Finish
    Decision -->|"No"| L2_S4["Log Error & Reject"] --> L1_S3 --> Finish
```

## Flow Description | Mô tả luồng

| Lane | Actor / System | Role in Flow |
|------|----------------|--------------|
| 1 | Subscriber | Accesses billing portal -> Selects unpaid invoice -> Submits payment details -> Receives digital receipt |
| 2 | Telecom System | Validates invoice status -> Routes to Payment Gateway -> Updates account balance -> Triggers confirmation SMS |
| 3 | Payment Gateway | Verifies credit card -> Executes fund transfer -> Returns auth confirmation |
