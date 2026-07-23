# Swimlane Diagram — Product Lifecycle Management (PLM) System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Production Manager"]
        L1_S1["Scan Work Order & Badge"]
        L1_S2["Load Machine Recipe"]
        L1_S3["Monitor Live Line Counter"]
        L1_S4["Report Completion"]
    end

    subgraph Lane2["Product Lifecycle Management (PLM) System Control Core"]
        L2_S1["Validate Credentials & Order"]
        L2_S2["Send SCADA Start Command"]
        L2_S3{"Evaluate Telemetry & Check?"}
        L2_S4["Update Order State & OEE"]
    end

    subgraph Lane3["Shop Floor Supervisor"]
        L3_S1["Inspect Workstation Output"]
        L3_S2["Measure Quality Parameters"]
        L3_S3["Log Defect / Quarantine"]
    end

    subgraph Lane4["Assembly Operator"]
        L4_S1["Review Line Performance"]
        L4_S2["Audit Batch Record"]
        L4_S3["Sign Executive Release"]
    end

    Finish(["End"])

    Start --> L1_S1 --> L2_S1 --> L2_S2
    L2_S2 -->|"Valid / Approved"| L2_S3 --> L3_S1 --> L4_S1 --> Finish
    L2_S2 -->|"Invalid / Rejected"| L1_S2 --> L2_S1
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Production Manager | Initiates production run, monitors workstation, reports status. |
| 2 | Product Lifecycle Management (PLM) System Control Core | Validates inputs, controls machinery interfaces, computes OEE, records state. |
| 3 | Shop Floor Supervisor | Performs line inspection, logs defects, routes quarantined units. |
| 4 | Assembly Operator | Reviews operational metrics, audits compliance, approves release. |

