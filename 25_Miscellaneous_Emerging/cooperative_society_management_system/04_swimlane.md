# Swimlane Diagram — Co-operative Society Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Co-op Member / Farmer"]
        M1["Submit Micro-Credit Loan Request"]
        M2["Select Co-Signor Share Guarantors"]
        M3["Receive Mobile Money Loan Payout"]
    end

    subgraph Lane2["System"]
        S1["Verify Share Capital Multiplier Limit"]
        S2["Check Guarantor Share Pledge Balance"]
        S3{"Credit Underwriting Approved?"}
        S4["Issue Loan Rejection SMS Alert"]
        S5["Generate Loan Agreement & Payment Plan"]
        S6["Dispatch Mobile Payout Instruction"]
    end

    subgraph Lane3["Loan Officer / Accountant"]
        L1["Review Member Credit & Yield History"]
        L2["Sign Off Loan Underwriting Approval"]
    end

    subgraph Lane4["Commercial Bank Gateway"]
        B1["Process Mobile Money Disbursal (M-Pesa)"]
        B2["Return Settlement Confirmation ACK"]
    end

    Finish(["End"])

    Start --> M1 --> M2 --> S1 --> S2 --> L1 --> L2 --> S3
    S3 -->|"No"| S4 --> Finish
    S3 -->|"Yes"| S5 --> S6 --> B1 --> B2 --> M3 --> Finish
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Co-op Member / Farmer | Submits micro-credit loan request, selects co-signor share guarantors, signs loan agreement, and receives mobile money cash payout. |
| 2 | System | Verifies member share capital leverage multiplier (max 3x), checks guarantor share pledge balances, generates payment agreements, dispatches mobile payout requests, and sends alerts. |
| 3 | Loan Officer / Accountant | Reviews member credit history, farm crop yield records, and guarantor pledges, signing off on underwriting approval. |
| 4 | Commercial Bank Gateway | Processes electronic mobile money transfer (e.g. M-Pesa / Bank ACH), dispatches funds to member wallet, and returns settlement ACK. |
