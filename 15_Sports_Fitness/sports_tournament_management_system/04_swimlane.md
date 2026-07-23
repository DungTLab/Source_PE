# Swimlane Diagram — Sports Tournament Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Sports Tournament User"]
        A1["Initiate Request"]
        A2["Provide Required Details"]
    end

    subgraph Lane2["System Core Engine"]
        S1["Validate Input Credentials"]
        S2{"Validation Passed?"}
        S3["Execute Core Business Logic"]
    end

    subgraph Lane3["Sports Tournament Administrator"]
        B1["Review & Authorize Action"]
    end

    Finish(["End"])

    Start --> A1 --> A2 --> S1 --> S2
    S2 -->|"Yes"| S3 --> B1 --> Finish
    S2 -->|"No"| A1
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Sports Tournament User | Initiates process and inputs payload |
| 2 | System Core Engine | Validates parameters, evaluates decisions, executes logic |
| 3 | Sports Tournament Administrator | Reviews final outcomes and grants supervisor authorization |

