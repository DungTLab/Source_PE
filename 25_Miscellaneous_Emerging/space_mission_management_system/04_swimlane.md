# Swimlane Diagram — Space Mission Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Flight Director"]
        F1["Schedule Launch Window & Trajectory"]
        F2["Execute Two-Person Burn Approval"]
        F3["Monitor Live Telemetry & Alarms"]
        F4["Review Science Data & Mission Logs"]
    end

    subgraph Lane2["System"]
        S1["Calculate Orbital Ephemeris"]
        S2["Format Signed CCSDS Command Sequence"]
        S3{"Spacecraft Telemetry Nominal?"}
        S4["Execute Emergency Safe-Mode Protocol"]
        S5["Process Downlinked Science Data Files"]
    end

    subgraph Lane3["Deep Space Ground Station"]
        G1["Lock RF Carrier Signal & Point Antenna"]
        G2["Uplink Command Packets over RF"]
        G3["Downlink Raw Telemetry & Science Frames"]
    end

    subgraph Lane4["Spacecraft Hardware"]
        SC1["Execute Ignition & Orbital Burn"]
        SC2["Deploy Solar Arrays & Transmit Telemetry"]
    end

    Finish(["End"])

    Start --> F1 --> S1 --> F2 --> S2 --> G1 --> G2 --> SC1 --> SC2 --> G3 --> S3
    S3 -->|"No (Anomaly)"| S4 --> F3
    S3 -->|"Yes (Nominal)"| S5 --> F4 --> Finish
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Flight Director | Schedules launch windows, executes mandatory two-person burn command sign-offs, monitors live spacecraft telemetry consoles, and reviews downlinked science data. |
| 2 | System | Calculates orbital mechanics ephemerides, packages cryptographically signed CCSDS command sequences, evaluates real-time telemetry limits, executes safe-mode protocols upon anomaly, and processes science data. |
| 3 | Deep Space Ground Station | Establishes RF carrier signal lock, aligns dish antennas, uplinks command sequence packages, and downlinks raw telemetry and science data frames. |
| 4 | Spacecraft Hardware | Executes delta-v thruster ignition burns, deploys solar array wings, manages attitude orientation, and streams telemetry packets back to Earth. |
