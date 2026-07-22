# Swimlane Diagram — Global Remittance Platform

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Remittance Sender"]
        S1["Enter Amount & Lock FX Rate Quote"]
        S2["Authorize Debit Card / Bank Payment"]
        S3["Receive 10-Digit MTCN Tracking Code"]
    end

    subgraph Lane2["System"]
        P1["Verify eKYC & Debit Sender Account"]
        P2["Submit Names for AML Screening"]
        P3{"Sanctions Match Score > 75%?"}
        P4["Freeze Transaction & Alert Compliance"]
        P5["Generate 10-Digit MTCN Number"]
        P6["Dispatch Payment Payload to Partner"]
    end

    subgraph Lane3["AML & Sanctions Engine"]
        A1["Fuzzy Match OFAC & UN Sanctions"]
        A2["Check Velocity Structuring Rules"]
    end

    subgraph Lane4["Payout Partner Network"]
        N1["Verify Beneficiary Photo ID & MTCN"]
        N2["Disburse Cash / Mobile Wallet Payout"]
    end

    Finish(["End"])

    Start --> S1 --> S2 --> P1 --> P2 --> A1 --> A2 --> P3
    P3 -->|"Yes (Match)"| P4 --> Finish
    P3 -->|"No (Clear)"| P5 --> P6 --> N1 --> N2 --> S3 --> Finish
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Remittance Sender | Enters transfer amount, locks guaranteed FX rate quote, authorizes debit card/bank payment funding, and receives 10-digit MTCN tracking code. |
| 2 | System | Verifies eKYC identity status, debits sender's funding account, dispatches names for AML screening, handles compliance freezes, generates MTCN codes, and dispatches payment payloads. |
| 3 | AML & Sanctions Engine | Performs automated fuzzy matching against global OFAC, UN, and EU sanctions watchlists, and checks velocity transaction structuring rules. |
| 4 | Payout Partner Network | Verifies recipient photo ID and 10-digit MTCN code at retail counter (or executes automated mobile wallet deposit), disbursing local currency funds. |
