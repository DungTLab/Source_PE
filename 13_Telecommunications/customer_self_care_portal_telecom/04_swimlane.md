# Swimlane Diagram — Customer Self-Care Portal (Telecom)

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Customer"]
        L1_S1["Opens self-care portal"]
        L1_S2["Selects Top-Up amount"]
        L1_S3["Submits payment credentials"]
        L1_S4["Views updated account balance"]
    end

    subgraph Lane2["Self-Care Portal"]
        L2_S1["Validates input details"]
        L2_S2["Routes payment payload"]
        L2_S3["Notifies Billing Engine"]
        L2_S4["Renders instant success screen"]
        Decision{"Validation OK?"}
    end

    subgraph Lane3["Billing Backend"]
        L3_S1["Credits main balance"]
        L3_S2["Extends account validity"]
        L3_S3["Triggers notification SMS"]
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
| 1 | Customer | Opens self-care portal -> Selects Top-Up amount -> Submits payment credentials -> Views updated account balance |
| 2 | Self-Care Portal | Validates input details -> Routes payment payload -> Notifies Billing Engine -> Renders instant success screen |
| 3 | Billing Backend | Credits main balance -> Extends account validity -> Triggers notification SMS |
