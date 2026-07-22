# Swimlane Diagram — Disaster Preparedness & Simulation System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Emergency Operations Analyst"]
        A1["Configure Scenario Magnitude & Epicenter"]
        A2["Review 3D Shaking & Inundation Map"]
        A3["Authorize Emergency Evacuation Alert"]
    end

    subgraph Lane2["System"]
        S1["Detect P-Wave Early Warning Telemetry"]
        S2["Format Simulation Grid & Boundary Conditions"]
        S3{"Seismic PGA > 0.15g / Tsunami > 2m?"}
        S4["Log Low-Hazard Sensor Event"]
        S5["Render 3D Hazard Overlays & Risk Density"]
        S6["Dispatch Cell Broadcast WEA / Siren Alert"]
    end

    subgraph Lane3["Seismic & Tsunami Sensor Network"]
        N1["Detect Primary P-Wave Acceleration"]
        N2["Transmit Waveform & Buoy Pressure Data"]
    end

    subgraph Lane4["High-Performance Simulation Solver"]
        E1["Solve Elastodynamic Wave Propagation"]
        E2["Generate 3D Inundation Time-Steps"]
    end

    Finish(["End"])

    Start --> A1 --> N1 --> N2 --> S1 --> S2 --> E1 --> E2 --> S3
    S3 -->|"No"| S4 --> Finish
    S3 -->|"Yes"| S5 --> A2 --> A3 --> S6 --> Finish
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Emergency Operations Analyst | Configures disaster scenario magnitude and epicenter coordinates, reviews 3D ground shaking and inundation map overlays, and authorizes emergency mass evacuation alerts. |
| 2 | System | Detects P-wave early warning telemetry, formats simulation grid boundary conditions, checks hazard threshold limits, renders 3D hazard overlays, and dispatches wireless emergency alerts. |
| 3 | Seismic & Tsunami Sensor Network | Seismometers detect primary P-wave ground acceleration and deep-ocean DART buoys measure ocean water pressure changes, streaming real-time telemetry. |
| 4 | High-Performance Simulation Solver | Solves 3D elastodynamic wave equations and shallow water hydrodynamic equations, generating time-series 3D hazard impact grids. |
