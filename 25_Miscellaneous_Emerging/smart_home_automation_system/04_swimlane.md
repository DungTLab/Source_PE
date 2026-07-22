# Swimlane Diagram — Smart Home Automation System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Home Resident"]
        R1["Configure Motion Automation Routine"]
        R2["Walk into Hallway at Night"]
        R3["Verify Light Turn ON & Receive Alert"]
    end

    subgraph Lane2["System"]
        S1["Store Routine Rule Parameters"]
        S2["Evaluate Sensor Motion Event Payload"]
        S3{"After Sunset AND Motion Active?"}
        S4["Ignore Sensor Event (Daytime)"]
        S5["Dispatch Light ON 30% Command"]
        S6["Send Mobile Push Notification"]
    end

    subgraph Lane3["Matter & Zigbee Hub Gateway"]
        H1["Ingest Zigbee Motion Cluster State"]
        H2["Transmit Matter Light Cluster Command"]
    end

    subgraph Lane4["Smart IoT Sensors & Actuators"]
        A1["PIR Motion Sensor Detects Movement"]
        A2["Smart Light Relay Turns ON 30% Warm"]
    end

    Finish(["End"])

    Start --> R1 --> S1 --> R2 --> A1 --> H1 --> S2 --> S3
    S3 -->|"No"| S4 --> Finish
    S3 -->|"Yes"| S5 --> H2 --> A2 --> R3 --> S6 --> Finish
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Home Resident | Configures hallway motion automation routines, walks into the hallway at night, and observes automatic warm light activation and notifications. |
| 2 | System | Persists routine rule triggers, evaluates incoming sensor telemetry, verifies time-of-day condition filters, dispatches execution commands, and sends push alerts. |
| 3 | Matter & Zigbee Hub Gateway | Ingests Zigbee PIR motion sensor cluster state updates and transmits Matter light control cluster commands over the local wireless mesh. |
| 4 | Smart IoT Sensors & Actuators | PIR motion sensor detects physical movement, and smart light relay actuates to turn ON at 30% warm color temperature. |
