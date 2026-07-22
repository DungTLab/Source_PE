# Swimlane Diagram — Senior Living Facility Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Senior Resident / Sensor"]
        R1["Suffer Accidental Floor Fall Impact"]
        R2["Remain Immobile on Room Floor"]
        R3["Receive Immediate Nursing Care"]
    end

    subgraph Lane2["System"]
        S1["Ingest 3D Accelerometer Telemetry"]
        S2["Detect >2.5g Impact & Immobility Signature"]
        S3{"Fall Confidence Score > 95%?"}
        S4["Log Minor Movement & Discard"]
        S5["Trigger High-Priority Fall Alarm"]
        S6["Push Emergency Alert to Nurse Mobile App"]
    end

    subgraph Lane3["Wearable Fall & Vital Sensor"]
        W1["Measure Rapid G-Force Acceleration"]
        W2["Stream Real-Time BLE Fall Payload"]
    end

    subgraph Lane4["Caregiver & Nurse Staff"]
        N1["Receive Mobile Phone Alarm & Room Pin"]
        N2["Arrive at Room & Assess Resident Vitals"]
        N3["Clear Nurse Call & Log Incident Report"]
    end

    Finish(["End"])

    Start --> R1 --> W1 --> W2 --> S1 --> S2 --> S3
    S3 -->|"No"| S4 --> Finish
    S3 -->|"Yes"| S5 --> S6 --> N1 --> N2 --> R3 --> N3 --> Finish
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Senior Resident / Sensor | Suffers an accidental floor fall impact, remains immobile, and receives immediate nursing care upon responder arrival. |
| 2 | System | Ingests accelerometer telemetry, runs fall signature detection algorithms, checks confidence thresholds, triggers high-priority alarms, and pushes mobile alerts. |
| 3 | Wearable Fall & Vital Sensor | Measures rapid G-force acceleration, detects hard floor impact, and streams real-time BLE fall payload to system. |
| 4 | Caregiver & Nurse Staff | Receives loud mobile phone alarm with room location pin, arrives at resident room within seconds, assesses vitals, provides care, and logs fall incident report. |
