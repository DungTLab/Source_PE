# Swimlane Diagram — Core Banking System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start Transaction"])

    subgraph CustomerLane["Customer"]
        C1["Present National ID and Cash/Transfer Request"]
        C2["Review and Sign Receipt"]
        C3["Receive Cash and Confirmation Receipt"]
    end

    subgraph TellerLane["Bank Teller"]
        T1["Verify Customer Identity and Query Account"]
        T2["Input Transaction Details into System"]
        T3["Count Cash and Confirm Deposit/Withdrawal Amount"]
        T4["Print Receipt and Hand to Customer"]
    end

    subgraph ManagerLane["Branch Manager"]
        M1["Receive High-Value Alert Notification"]
        M2{"Approve Transaction Override?"}
        M3["Reject Transaction and Record Reason"]
    end

    subgraph SystemLane["Core Banking System"]
        S1["Validate Account Status and Daily Limits"]
        S2{"Exceeds Teller Limit?"}
        S3["Update Account Balance and Post GL Entries"]
        S4["Send SMS Alert to Customer"]
    end

    Finish(["End Transaction"])

    Start --> C1 --> T1 --> T2 --> S1 --> S2
    S2 -->|"No"| T3
    S2 -->|"Yes"| M1 --> M2
    M2 -->|"Yes"| T3
    M2 -->|"No"| M3 --> Finish
    T3 --> S3 --> S4 --> T4 --> C2 --> C3 --> Finish
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Customer | Initiates financial request at counter by presenting valid national identity documents, verifies printed receipt terms, signs document, and receives physical cash or digital balance update confirmation |
| 2 | Bank Teller | Inspects customer identity documents, queries target account state, enters operational parameters into Core Banking, counts physical cash banknotes, and prints final customer receipt |
| 3 | Branch Manager | Monitored electronically for high-value counter transactions exceeding standard teller authorization limits (>100M VND), evaluates risk parameters, and executes electronic sign-off or rejection decision |
| 4 | Core Banking System | Performs real-time automated rule checks (account lock status, balance availability, limit validation), computes dynamic fee/interest, posts balanced General Ledger entries, updates database state, and dispatches SMS alerts |
