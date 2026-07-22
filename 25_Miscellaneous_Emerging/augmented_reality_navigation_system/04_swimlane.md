# Swimlane Diagram — Augmented Reality Navigation System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["AR Headset User"]
        U1["Search Destination & Select AR Mode"]
        U2["Follow 3D Pathway & AR Turn Arrows"]
        U3["Arrive at Target Destination"]
    end

    subgraph Lane2["System"]
        S1["Calculate 3D Waypoint Path"]
        S2["Query VPS & BLE Localization"]
        S3{"Visual Pose Aligned Sub-Meter?"}
        S4["Re-Align Camera Pose via QR / VPS"]
        S5["Render 3D Overlay & HUD Display"]
    end

    subgraph Lane3["Visual Positioning System (VPS)"]
        V1["Extract Camera Visual Feature Descriptors"]
        V2["Match Point Cloud & Return 6DOF Pose"]
    end

    subgraph Lane4["AR Smart Glasses / Mobile Hardware"]
        H1["Stream IMU Telemetry & Camera Frames"]
        H2["Detect Surface Planes & Floor Meshes"]
        H3["Trigger Haptic Vibration Warning"]
    end

    Finish(["End"])

    Start --> U1 --> S1 --> H1 --> V1 --> V2 --> S2 --> S3
    S3 -->|"No (Tracking Drift)"| S4 --> H1
    S3 -->|"Yes (Aligned)"| H2 --> S5 --> U2 --> H3 --> U3 --> Finish
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | AR Headset User | Searches for navigation destinations, selects walking/driving mode, follows 3D AR pathway ribbons and turn arrows, and arrives at the target. |
| 2 | System | Computes 3D spatial routes, queries cloud VPS and BLE beacon positioning, checks pose alignment precision, handles re-alignment, and renders 3D graphics. |
| 3 | Visual Positioning System (VPS) | Extracts visual feature point descriptors (ORB/SIFT) from camera frames, matches them against 3D spatial maps, and returns 6DOF pose correction matrices. |
| 4 | AR Smart Glasses / Mobile Hardware | Streams live camera frames and IMU 6DOF telemetry, detects physical floor surface planes via LiDAR, and triggers haptic vibration alerts. |
