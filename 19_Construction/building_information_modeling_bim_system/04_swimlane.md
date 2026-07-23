# Swimlane Diagram — Building Information Modeling (BIM) System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start Process"])

    subgraph Lane1["Architect"]
        A1["Initialize Request / Action"]
        A2["Submit Operational Input Data"]
    end

    subgraph Lane2["BIM Manager"]
        B1["Audit & Review Submission"]
        B2{"Data & Quality Valid?"}
        B3["Issue Exception Notice / Revision"]
    end

    subgraph Lane3["MEP Engineer"]
        C1["Perform Field Verification"]
        C2["Execute Compliance Sign-off"]
    end

    subgraph Lane4["BIM Platform System"]
        D1["Process Automated Ledger Update"]
        D2["Generate Executive Summary Dashboard"]
    end

    Finish(["End Process Cycle"])

    Start --> A1 --> A2 --> B1 --> B2
    B2 -->|"No"| B3 --> A2
    B2 -->|"Yes"| C1 --> C2 --> D1 --> D2 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor / System | Role in Flow |
|------|----------------|--------------|
| 1 | Architect | Initiates requests and logs operational data into Building Information Modeling (BIM) System. |
| 2 | BIM Manager | Audits data validity, checks operational thresholds, and issues revision requests if needed. |
| 3 | MEP Engineer | Conducts physical or technical verification and grants formal sign-off. |
| 4 | BIM Platform System | Automatically updates database records, recalculates indicators, and displays executive dashboards. |
