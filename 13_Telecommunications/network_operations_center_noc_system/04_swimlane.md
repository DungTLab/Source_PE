# Swimlane Diagram — Network Operations Center (NOC) System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Operator / Engineer"]
        L1_S1["Detects fault alert in dashboard"]
        L1_S2["Analyzes root cause telemetry"]
        L1_S3["Submits maintenance ticket"]
        L1_S4["Confirms issue resolution"]
    end

    subgraph Lane2["Telecom System"]
        L2_S1["Aggregates network metrics"]
        L2_S2["Triggers severity alert"]
        L2_S3["Dispatches SMS to field team"]
        L2_S4["Updates system health state"]
        Decision{"Validation OK?"}
    end

    subgraph Lane3["Core Gateway"]
        L3_S1["Collects raw hardware metrics"]
        L3_S2["Executes automated failsafe"]
        L3_S3["Returns operational state"]
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
| 1 | Operator / Engineer | Detects fault alert in dashboard -> Analyzes root cause telemetry -> Submits maintenance ticket -> Confirms issue resolution |
| 2 | Telecom System | Aggregates network metrics -> Triggers severity alert -> Dispatches SMS to field team -> Updates system health state |
| 3 | Core Gateway | Collects raw hardware metrics -> Executes automated failsafe -> Returns operational state |
