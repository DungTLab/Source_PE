# Swimlane Diagram — Co-working Space Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Project Manager"]
        L1_S1["Submit Request Payload"]
        L1_S2["Upload Documentation"]
        L1_S3["Receive Status Notification"]
        L1_S4["Acknowledge Completion"]
    end

    subgraph Lane2["Co-working Space Management System Processing Engine"]
        L2_S1["Validate Payload & Format"]
        L2_S2["Store Core Record"]
        L2_S3{"Evaluate Rules & Check?"}
        L2_S4["Trigger Downstream Dispatch"]
    end

    subgraph Lane3["Asset Manager"]
        L3_S1["Receive Task Assignment"]
        L3_S2["Inspect Specs & Files"]
        L3_S3["Perform Operational Action"]
    end

    subgraph Lane4["Operational Staff"]
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
| 1 | Project Manager | Initiates operation, uploads inputs, monitors status, receives results. |
| 2 | Co-working Space Management System Processing Engine | Validates inputs, executes core logic, checks compliance, updates state. |
| 3 | Asset Manager | Reviews request, inspects details, executes operational processing. |
| 4 | Operational Staff | Inspects high-level compliance and signs final approval. |

