# Swimlane Diagram — Brain-Computer Interface (BCI) Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["BCI Patient / End User"]
        P1["Put On Headset & Verify Impedance"]
        P2["Perform Motor Imagery Mental Task"]
        P3["Observe Neuro-Feedback & Tactile Response"]
    end

    subgraph Lane2["System"]
        S1["Acquire Multi-Channel Raw EEG Streams"]
        S2["Apply Notch & Bandpass Filtering"]
        S3{"Intent Confidence > 75%?"}
        S4["Output Neutral / Hold Command"]
        S5["Dispatch Joint Command to Prosthetic"]
    end

    subgraph Lane3["Neural Signal ML Pipeline"]
        M1["Extract Common Spatial Patterns CSP"]
        M2["Classify Mental Intent Class"]
    end

    subgraph Lane4["External Assistive Device"]
        D1["Actuate Robotic Prosthetic Motors"]
        D2["Return Tactile Pressure Sensor Data"]
    end

    Finish(["End"])

    Start --> P1 --> S1 --> S2 --> M1 --> M2 --> S3
    S3 -->|"No (Ambiguous)"| S4 --> P2
    S3 -->|"Yes (Confident)"| S5 --> D1 --> D2 --> P3 --> Finish
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | BCI Patient / End User | Wears BCI headset, performs imagined motor imagery tasks (e.g. imagined hand clench), and observes real-time visual neuro-feedback and tactile responses. |
| 2 | System | Ingests multi-channel raw EEG streams, applies 50 Hz notch filtering and bandpass filters (0.5-40 Hz), evaluates intent decoding confidence scores, dispatches commands, or holds state. |
| 3 | Neural Signal ML Pipeline | Extracts Common Spatial Pattern (CSP) band-power features and runs machine learning classification (SVM/EEGNet) to determine intended class (e.g. Reach Left, Grasp). |
| 4 | External Assistive Device | Receives decoded joint actuation vectors, drives bionic robotic prosthetic motors, and returns real-time tactile gripping pressure sensor feedback. |
