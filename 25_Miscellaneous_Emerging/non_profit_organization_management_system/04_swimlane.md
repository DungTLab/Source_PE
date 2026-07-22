# Swimlane Diagram — Non-Profit Organization Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Donor / Financial Sponsor"]
        D1["Select Campaign & Pledge Gift"]
        D2["Submit Payment Details"]
        D3["Receive Tax Receipt & Impact Update"]
    end

    subgraph Lane2["System"]
        S1["Verify Campaign & Process Payment"]
        S2["Post Restricted/Unrestricted Ledger"]
        S3{"Beneficiary Aid Approved?"}
        S4["Execute Payment Wire Disbursement"]
        S5["Compile Form 990 Tax Return"]
    end

    subgraph Lane3["NPO Program Officer"]
        P1["Configure Program & Eligibility Rules"]
        P2["Review Beneficiary Aid Application"]
        P3["Authorize Grant Payout"]
    end

    subgraph Lane4["Financial ERP System"]
        F1["Update Fund Balance Ledger"]
        F2["Generate Annual Statutory Tax File"]
    end

    Finish(["End"])

    Start --> D1 --> D2 --> S1 --> S2 --> F1 --> P1 --> P2 --> P3 --> S3
    S3 -->|"Yes"| S4 --> D3 --> S5 --> F2 --> Finish
    S3 -->|"No"| P2
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Donor / Financial Sponsor | Selects fundraising campaign, pledges monetary gift, submits credit card or bank details, and receives tax-deductible receipts and impact reports. |
| 2 | System | Automates payment processing, posts fund accounting ledger entries, executes electronic aid payouts to beneficiaries, and compiles annual tax return files. |
| 3 | NPO Program Officer | Defines social program budgets, establishes eligibility rules, evaluates beneficiary aid applications, and authorizes grant disbursements. |
| 4 | Financial ERP System | Maintains fund accounting general ledgers, enforces restricted vs unrestricted fund rules, and generates statutory Form 990 tax files. |
