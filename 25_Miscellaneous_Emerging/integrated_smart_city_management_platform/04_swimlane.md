# Swimlane Diagram — Integrated Smart City Management Platform

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Smart City Resident / IoT Device"]
        D1["AI Camera Detects Multi-Car Collision"]
        D2["Stream High-Definition Incident Video"]
        D3["Receive Public Cell Broadcast Alert"]
    end

    subgraph Lane2["System"]
        S1["Ingest Video Analytics AI Collision Event"]
        S2["Correlate Spatial GIS & Wind Vectors"]
        S3{"High-Severity Multi-Agency Incident?"}
        S4["Log Minor Congestion Delay Event"]
        S5["Trigger Emergency Vehicle Green Wave"]
        S6["Dispatch Cross-Agency Emergency CAD Alert"]
    end

    subgraph Lane3["Intelligent Traffic Controller"]
        T1["Preempt Intersections Ahead of Ambulance"]
        T2["Hold Cross-Traffic Signals Red"]
    end

    subgraph Lane4["Emergency Services Dispatch CAD"]
        E1["Receive Incident CAD Payload & Video"]
        E2["Dispatch Fire, Police, & EMS Units"]
    end

    Finish(["End"])

    Start --> D1 --> D2 --> S1 --> S2 --> S3
    S3 -->|"No"| S4 --> Finish
    S3 -->|"Yes"| S5 --> T1 --> T2 --> S6 --> E1 --> E2 --> D3 --> Finish
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Smart City Resident / IoT Device | Smart CCTV camera with AI computer vision detects a major multi-vehicle highway collision, streams high-definition video telemetry, and citizens receive public emergency cell broadcast alerts. |
| 2 | System | Ingests video analytics event, correlates 3D spatial GIS layers, validates incident severity threshold, triggers traffic signal emergency green wave, and dispatches cross-agency emergency CAD alert. |
| 3 | Intelligent Traffic Controller | Receives green-wave priority command, holds cross-traffic signals red, and clears green-light corridor for approaching fire trucks and ambulances. |
| 4 | Emergency Services Dispatch CAD | Receives cross-agency CAD payload and live video feeds, dispatches police/fire/EMS field units, and resolves the urban emergency incident. |
