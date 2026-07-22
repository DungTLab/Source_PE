# Swimlane Diagram — Charity & Donation Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane_Beneficiary["Beneficiary"]
        B1["Submit Relief Aid Application & Documents"]
        B2["Receive Disbursement Notification & Bank Credit"]
    end

    subgraph Lane_Admin["Charity Admin"]
        A1["Review Application & Verify Hardship Documents"]
        A2["Approve Aid Grant & Specify Payout Amount"]
    end

    subgraph Lane_System["Charity System"]
        S1["Verify Active Campaign Fund Balance"]
        S2{"Sufficient Funds Available?"}
        S3["Queue Payout & Hold Pending Replenishment"]
        S4["Format Bank Wire Payload & Transmit"]
        S5["Log Disbursement Ledger & Update Campaign Net Balance"]
        S6["Send SMS Notification & Receipt to Beneficiary"]
    end

    subgraph Lane_Banking["Banking Gateway"]
        P1["Process Wire Transfer to Beneficiary Account"]
        P2{"Transfer Successful?"}
        P3["Return Bank Clearing Reference Code"]
    end

    Finish(["End"])

    Start --> B1
    B1 --> A1
    A1 --> A2
    A2 --> S1
    S1 --> S2
    S2 -->|"No"| S3
    S3 --> A2
    S2 -->|"Yes"| S4
    S4 --> P1
    P1 --> P2
    P2 -->|"No"| S3
    P2 -->|"Yes"| P3
    P3 --> S5
    S5 --> S6
    S6 --> B2
    B2 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Beneficiary | Initiates aid request by submitting medical/hardship documentation and receives SMS notification and bank credit upon successful payout. |
| 2 | Charity Admin | Reviews beneficiary applications, verifies document authenticity, and signs off on aid grant approvals and payout amounts. |
| 3 | Charity System | Checks available unallocated campaign balances, formats automated bank wire payloads, updates financial ledgers, and dispatches notices. |
| 4 | Banking Gateway | External banking integration that executes direct bank wire transfers to beneficiary accounts and returns transaction settlement references. |
