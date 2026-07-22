# Swimlane Diagram — Digital Twin City Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["City Urban Planner"]
        P1["Select District & Trigger Flood Scenario"]
        P2["Review 3D Flood Inundation Overlay"]
        P3["Approve Emergency Evacuation Route"]
    end

    subgraph Lane2["System"]
        S1["Ingest Real-Time River Gauge Telemetry"]
        S2["Build 3D Elevation Mesh & BIM Barriers"]
        S3{"Water Inundation Depth > 0.5m?"}
        S4["Flag Minor Water Accumulation"]
        S5["Render Dynamic 3D Inundation Overlay"]
        S6["Calculate Hazard-Free Evacuation Route"]
    end

    subgraph Lane3["Smart City IoT Sensor Network"]
        I1["Measure Storm Drain & River Level"]
        I2["Transmit Water Depth Telemetry"]
    end

    subgraph Lane4["Urban Simulation Engine"]
        E1["Compute Hydrodynamic Water Solver"]
        E2["Generate Inundation Depth Grid Time-Steps"]
    end

    Finish(["End"])

    Start --> P1 --> I1 --> I2 --> S1 --> S2 --> E1 --> E2 --> S3
    S3 -->|"No"| S4 --> Finish
    S3 -->|"Yes"| S5 --> P2 --> S6 --> P3 --> Finish
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | City Urban Planner | Selects target city district, configures 100-year rainfall parameters, reviews 3D flood inundation depth overlays, and approves emergency evacuation routing plans. |
| 2 | System | Ingests real-time IoT river gauge telemetry, builds 3D terrain elevation and building obstacle meshes, evaluates flood depth thresholds, renders 3D inundation layers, and computes evacuation routes. |
| 3 | Smart City IoT Sensor Network | Measures river water levels and storm drain flow rates, transmitting real-time telematics packets over the municipal network. |
| 4 | Urban Simulation Engine | Computes 2D/3D shallow water hydrodynamic solver equations and generates time-series inundation depth grid matrices for rendering. |
