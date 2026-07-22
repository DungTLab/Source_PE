# Swimlane Diagram — Know Your Customer (KYC) System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start Operation"])

    subgraph UserLane["End User"]
        U1["Access System and Input Parameters"]
        U2["Review Breakdown and Confirm with OTP"]
        U3["Receive Final Confirmation Receipt"]
    end

    subgraph OpsLane["Operations Staff"]
        O1["Receive High-Value Flag Notification"]
        O2{"Approve Request Override?"}
        O3["Reject Request and Enter Reason"]
    end

    subgraph SystemLane["Know Your Customer (KYC) System"]
        S1["Validate Credentials and Check Limits"]
        S2{"Requires Manual Override?"}
        S3["Execute Core Calculation Engine"]
        S4["Post Accounting Ledger Entries"]
        S5["Dispatch Real-time Alert Notification"]
    end

    Finish(["End Operation"])

    Start --> U1 --> S1 --> S2
    S2 -->|"No"| S3
    S2 -->|"Yes"| O1 --> O2
    O2 -->|"Yes"| S3
    O2 -->|"No"| O3 --> Finish
    S3 --> S4 --> S5 --> U2 --> U3 --> Finish
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | End User | Submits domain service request parameters, inputs authentication tokens (OTP/Biometrics), and receives execution status receipts |
| 2 | Operations Staff | Supervises system queue alerts, reviews operational exception requests, and grants or denies administrative overrides |
| 3 | Know Your Customer (KYC) System | Performs automated parameter validation, computes business logic, coordinates balance postings, dispatches alert notifications, and records audit logs |
