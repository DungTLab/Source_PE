# Swimlane Diagram — Social & Networking Event Platform

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Primary Director"]
        A1["Submit Request / Configuration"]
        A2["Review Operational Output"]
    end

    subgraph Lane2["System Core Engine"]
        S1["Validate Input & Parameters"]
        S2{"Validation Passed?"}
        S3["Process Business Rules"]
        S4["Generate Audit Ledger & Output"]
    end

    subgraph Lane3["Participant / End User"]
        B1["Execute On-Site / Service Action"]
        B2["Acknowledge Status Update"]
    end

    subgraph Lane4["On-Site Staff Lead"]
        C1["Approve Financial / Final Sign-off"]
    end

    Finish(["End"])

    Start --> A1 --> S1 --> S2
    S2 -->|"Yes"| S3 --> B1 --> S4 --> C1 --> A2 --> Finish
    S2 -->|"No"| A1

```

## Flow Description | Mô tả luồng

| Lane | Actor / System | Role in Operational Flow |
|------|----------------|--------------------------|
| 1 | Primary Director | Initiates process requests, configures parameters, and reviews final results. |
| 2 | System Core Engine | Validates business constraints, executes core logic, and produces output artifacts. |
| 3 | Participant / End User | Performs physical/service interactions and confirms status updates. |
| 4 | On-Site Staff Lead | Audits compliance, approves financial transactions, and locks completed records. |

