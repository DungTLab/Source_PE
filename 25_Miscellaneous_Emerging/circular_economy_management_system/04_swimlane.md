# Swimlane Diagram — Circular Economy Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Product Consumer / Enterprise"]
        C1["Scan Product DPP QR & Request Return"]
        C2["Hand Over Sealed Box to Courier"]
        C3["Receive Deposit Refund & Eco Credit"]
    end

    subgraph Lane2["System"]
        S1["Verify DPP Product Passport Identity"]
        S2["Dispatch Reverse Logistics Transport"]
        S3{"Material Purity Audit Passed?"}
        S4["Flag Contaminated Lot & Re-Route"]
        S5["Issue Deposit Refund & Credit Tokens"]
        S6["List Reclaimed Lot on Secondary Market"]
    end

    subgraph Lane3["Reverse Logistics Provider"]
        L1["Pick Up Item & Verify Chain-of-Custody"]
        L2["Deliver Consolidated Freight to Facility"]
    end

    subgraph Lane4["Recycling Processor"]
        R1["Conduct NIR Spectroscopy Material Scan"]
        R2["Process Shredding & Pelletizing Batch"]
    end

    Finish(["End"])

    Start --> C1 --> S1 --> S2 --> L1 --> L2 --> R1 --> S3
    S3 -->|"No"| S4 --> Finish
    S3 -->|"Yes"| R2 --> S5 --> C3 --> S6 --> Finish
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Product Consumer / Enterprise | Scans Digital Product Passport (DPP) QR code, submits take-back return request, hands over packaged item to carrier, and receives deposit refunds and eco-credits. |
| 2 | System | Validates DPP identity tokens, dispatches reverse logistics pick-up orders, checks material purity audit results, issues deposit refunds, and lists reclaimed secondary materials on the B2B marketplace. |
| 3 | Reverse Logistics Provider | Executes pick-up, verifies chain-of-custody signatures, consolidates return shipments at regional hubs, and delivers freight to recycling facilities. |
| 4 | Recycling Processor | Scans incoming items using NIR spectroscopy, verifies polymer/metal purity grades, and executes mechanical shredding, sorting, and pelletizing into secondary raw materials. |
