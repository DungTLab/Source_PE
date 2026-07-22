# Swimlane Diagram — Autonomous Robotics Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Fleet Operator"]
        O1["Dispatch Mission & Pickup Waypoints"]
        O2["Monitor Live LiDAR & Telemetry"]
        O3["Perform Manual Teleoperation Joystick"]
        O4["Review Task Completion Metrics"]
    end

    subgraph Lane2["System"]
        S1["Select Optimal AMR & Calculate Path"]
        S2["Send ROS 2 Action Goal Payload"]
        S3{"Obstacle or Low Battery Detected?"}
        S4["Auto-Route AMR to Charging Dock"]
        S5["Publish Task Receipt to WMS"]
    end

    subgraph Lane3["ROS 2 Middleware / Edge Gateway"]
        R1["Publish Velocity Command /cmd_vel"]
        R2["Filter LiDAR & IMU Sensor Streams"]
    end

    subgraph Lane4["Autonomous Robot (AMR)"]
        A1["Execute Motor Velocity & SLAM Pathing"]
        A2["Detect Obstacle / Trigger Local E-Stop"]
        A3["Dock into Charging Contacts"]
    end

    Finish(["End"])

    Start --> O1 --> S1 --> S2 --> R1 --> A1 --> O2 --> R2 --> S3
    S3 -->|"Obstacle Hazard"| A2 --> O3 --> S1
    S3 -->|"Low Battery (<20%)"| S4 --> A3 --> S5 --> Finish
    S3 -->|"No Hazard"| A1 --> S5 --> O4 --> Finish
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Fleet Operator | Dispatches material transport mission, monitors live 2D/3D LiDAR telemetry, performs teleoperation overrides when needed, and reviews task analytics. |
| 2 | System | Evaluates fleet proximity, calculates dynamic A* costmaps, publishes ROS 2 action goals, monitors battery thresholds, manages auto-docking, and posts receipts. |
| 3 | ROS 2 Middleware / Edge Gateway | Bridges cloud commands to hardware `/cmd_vel` topics, processes high-frequency sensor streams, and manages ROS node heartbeat parameters. |
| 4 | Autonomous Robot (AMR) | Executes physical motor velocity vectors, performs SLAM localization, triggers local safety E-Stops upon obstacle detection, and connects to charging docks. |
