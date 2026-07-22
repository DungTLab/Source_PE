# Swimlane Diagram — Cemetery & Burial Services Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Rights Holder"]
        F1["Browse GIS Map & Select Plot"]
        F2["Purchase Plot Rights & Sign Deed"]
        F3["Order Monument & Inscription"]
        F4["View Digital Memorial & Directions"]
    end

    subgraph Lane2["System"]
        S1["Verify Plot Availability & Tier Pricing"]
        S2["Validate Payment & Issue Digital Deed"]
        S3{"Death Permit Verified?"}
        S4["Dispatch Grave Digging Work Order"]
        S5["Approve Monument Permit & Specs"]
        S6["Render GPS Coordinates & Search Pin"]
    end

    subgraph Lane3["Funeral Director"]
        D1["Submit Death Certificate & Permit"]
        D2["Schedule Committal Service & Vault"]
    end

    subgraph Lane4["GIS Mapping Engine"]
        G1["Render Interactive Cemetery Spatial Tiles"]
        G2["Update Plot Status Layer to Sold"]
    end

    Finish(["End"])

    Start --> F1 --> G1 --> S1 --> F2 --> S2 --> G2 --> D1 --> S3
    S3 -->|"Yes"| D2 --> S4 --> F3 --> S5 --> F4 --> S6 --> Finish
    S3 -->|"No"| D1
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Rights Holder | Browses interactive GIS plot map, selects burial plot, completes payment for deed rights, orders headstone monuments, and accesses online memorial pages. |
| 2 | System | Automates plot inventory status checks, processes payments, issues digital deeds, validates death certificates, dispatches grave excavation work orders, and updates GIS pins. |
| 3 | Funeral Director | Submits verified municipal death certificates, coordinates committal service times, specifies vault dimensions, and oversees burial ceremony logistics. |
| 4 | GIS Mapping Engine | Renders 2D/3D cemetery map layers, updates plot status polygons from "Available" to "Sold", and provides GPS pin navigation for visitors. |
