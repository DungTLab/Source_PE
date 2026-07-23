# Swimlane Diagram — Construction Procurement System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start Process"])

    subgraph Lane1["Site Engineer"]
        A1["Initialize Request / Action"]
        A2["Submit Operational Input Data"]
    end

    subgraph Lane2["Specialized Contractor"]
        B1["Audit & Review Submission"]
        B2{"Data & Quality Valid?"}
        B3["Issue Exception Notice / Revision"]
    end

    subgraph Lane3["Quality / Safety Inspector"]
        C1["Perform Field Verification"]
        C2["Execute Compliance Sign-off"]
    end

    subgraph Lane4["System / PM"]
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
| 1 | Site Engineer | Initiates requests and logs operational data into Construction Procurement System. |
| 2 | Specialized Contractor | Audits data validity, checks operational thresholds, and issues revision requests if needed. |
| 3 | Quality / Safety Inspector | Conducts physical or technical verification and grants formal sign-off. |
| 4 | System / PM | Automatically updates database records, recalculates indicators, and displays executive dashboards. |
