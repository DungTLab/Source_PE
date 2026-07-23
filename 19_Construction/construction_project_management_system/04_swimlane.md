# Swimlane Diagram — Construction Project Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start Billing & Progress Audit"])

    subgraph Lane1["Subcontractor"]
        A1["Submit Monthly Progress Claim & Site Logs"]
        A2["Adjust Claimed Quantities"]
        A3["Receive Approved IPC & Disbursement"]
    end

    subgraph Lane2["Site Engineer"]
        B1["Audit Field Work & Verify Inspection Logs"]
        B2{"Quality & Safety OK?"}
        B3["Issue Non-Conformance Report (NCR)"]
        B4["Sign Off Daily Progress Verification"]
    end

    subgraph Lane3["Project Manager"]
        C1["Review Certified IPC & Financial S-Curve"]
        C2{"Budget & Retention OK?"}
        C3["Apply Retention & Generate IPC Document"]
    end

    subgraph Lane4["Client / Owner & System"]
        D1["System Syncs IPC with ERP Payment Gateway"]
        D2["Owner Approves Disbursement Release"]
    end

    Finish(["End Billing Cycle Process"])

    Start --> A1 --> B1 --> B2
    B2 -->|"No"| B3 --> A2 --> A1
    B2 -->|"Yes"| B4 --> C1 --> C2
    C2 -->|"No"| A2
    C2 -->|"Yes"| C3 --> D1 --> D2 --> A3 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor / System | Role in Flow |
|------|----------------|--------------|
| 1 | Subcontractor | Submits monthly work progress claims, adjusts claimed quantities upon feedback, and receives certified interim payments. |
| 2 | Site Engineer | Audits physical work on site against inspection logs, verifies safety compliance, issues NCRs for non-conforming work, and signs off progress logs. |
| 3 | Project Manager | Reviews audited progress claims against master baseline budget, validates retention deductions, and issues formal Interim Payment Certificates. |
| 4 | Client / Owner & System | System syncs IPC data payload with enterprise ERP financial backend; Client/Owner grants final disbursement approval. |
