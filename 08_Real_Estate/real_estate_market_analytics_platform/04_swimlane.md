# Swimlane Diagram — Real Estate Market Analytics Platform

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Platform User / Client"]
        L1_S1["Submit Request Payload"]
        L1_S2["Upload Documentation"]
        L1_S3["Receive Status Notification"]
        L1_S4["Acknowledge Completion"]
    end

    subgraph Lane2["Real Estate Market Analytics Platform Processing Engine"]
        L2_S1["Validate Payload & Format"]
        L2_S2["Store Core Record"]
        L2_S3{"Evaluate Rules & Check?"}
        L2_S4["Trigger Downstream Dispatch"]
    end

    subgraph Lane3["Service Provider / Agent"]
        L3_S1["Receive Task Assignment"]
        L3_S2["Inspect Specs & Files"]
        L3_S3["Perform Operational Action"]
    end

    subgraph Lane4["System Administrator"]
        L4_S1["Access Approval Queue"]
        L4_S2["Verify Compliance"]
        L4_S3["Sign Executive Approval"]
    end

    Finish(["End"])

    Start --> L1_S1 --> L2_S1 --> L2_S2
    L2_S2 -->|"Valid / Approved"| L2_S3 --> L3_S1 --> L4_S1 --> Finish
    L2_S2 -->|"Invalid / Rejected"| L1_S2 --> L2_S1
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Platform User / Client | Initiates operation, uploads inputs, monitors status, receives results. |
| 2 | Real Estate Market Analytics Platform Processing Engine | Validates inputs, executes core logic, checks compliance, updates state. |
| 3 | Service Provider / Agent | Reviews request, inspects details, executes operational processing. |
| 4 | System Administrator | Inspects high-level compliance and signs final approval. |

