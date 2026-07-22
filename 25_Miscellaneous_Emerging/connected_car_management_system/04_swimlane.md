# Swimlane Diagram — Connected Car Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Vehicle Owner"]
        O1["Select Remote Lock / Climate Action"]
        O2["Authenticate Biometric / PIN Token"]
        O3["Receive Door Lock Confirmation ACK"]
    end

    subgraph Lane2["System"]
        S1["Verify User Permissions & Command Format"]
        S2["Check Vehicle Connection Status"]
        S3{"Vehicle Cellular Network Online?"}
        S4["Queue Remote Command in Buffer"]
        S5["Dispatch Encrypted MQTT Command Payload"]
        S6["Update Mobile App Dashboard State"]
    end

    subgraph Lane3["Cellular Telematics Network"]
        C1["Transmit Carrier IP Packet to TCU"]
        C2["Return Execution ACK Packet to Cloud"]
    end

    subgraph Lane4["Vehicle TCU & CAN Bus ECU"]
        T1["Verify SecOC Cryptographic Token"]
        T2["Actuate Door Lock Actuator via BCM"]
    end

    Finish(["End"])

    Start --> O1 --> O2 --> S1 --> S2 --> S3
    S3 -->|"No (Offline)"| S4 --> Finish
    S3 -->|"Yes (Online)"| S5 --> C1 --> T1 --> T2 --> C2 --> S6 --> O3 --> Finish
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Vehicle Owner | Selects remote command (e.g. Lock Doors / Pre-Climate) on mobile app, authenticates via biometric PIN, and receives execution ACK. |
| 2 | System | Validates owner permissions, checks vehicle cellular connection state, handles command queue buffering if offline, dispatches encrypted MQTT payloads, and updates mobile app UI. |
| 3 | Cellular Telematics Network | Routes encrypted carrier IP packets over 4G/5G mobile networks to the vehicle's eSIM, and returns execution ACK packets back to the cloud. |
| 4 | Vehicle TCU & CAN Bus ECU | Verifies SecOC cryptographic security tokens, passes command over CAN bus to Body Control Module (BCM), and actuates door lock motors. |
