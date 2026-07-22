# Swimlane Diagram — Autonomous Warehouse Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Warehouse Operations Manager"]
        M1["Ingest ERP Orders & Batch Wave Release"]
        M2["Review Pick Progress & Station Queues"]
        M3["Authorize Carrier Manifest Dispatch"]
    end

    subgraph Lane2["System"]
        S1["Allocate Optimal Storage Bins & SKUs"]
        S2["Dispatch ASRS Crane Retrieval Command"]
        S3{"AMR Robot Available in Zone?"}
        S4["Queue Task & Reroute Nearby AMR"]
        S5["Dispatch AMR Transport to G2P Station"]
        S6["Generate Shipping Label & Manifest"]
    end

    subgraph Lane3["ASRS Crane Hardware"]
        C1["Extract Tote Bin from High-Bay Rack"]
        C2["Deposit Tote onto Outbound Transfer Spur"]
    end

    subgraph Lane4["AGV / AMR Robot Fleet"]
        R1["Pick Up Tote from ASRS Spur"]
        R2["Transport Tote to G2P Packing Station"]
    end

    Finish(["End"])

    Start --> M1 --> S1 --> S2 --> C1 --> C2 --> S3
    S3 -->|"No"| S4 --> R1
    S3 -->|"Yes"| S5 --> R1 --> R2 --> M2 --> S6 --> M3 --> Finish
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Warehouse Operations Manager | Batches customer sales orders from ERP into wave releases, monitors real-time G2P station picking queues, and authorizes shipping manifest dispatch. |
| 2 | System | Calculates optimal SKU bin allocations, commands ASRS crane retrievals, checks AMR fleet availability, dispatches transport tasks to G2P stations, and generates carrier manifests. |
| 3 | ASRS Crane Hardware | Navigates high-bay rack aisles, extends extraction arm to retrieve target inventory totes, and deposits totes onto outbound transfer spurs. |
| 4 | AGV / AMR Robot Fleet | Navigates autonomously to ASRS transfer spurs, lifts retrieved totes, transports totes along warehouse travel lanes, and deposits them at G2P packing stations. |
