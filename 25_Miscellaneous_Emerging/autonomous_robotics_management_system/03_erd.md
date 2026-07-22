# Conceptual ERD — Autonomous Robotics Management System

## Mermaid Code

```mermaid
erDiagram
    ROBOT_MODEL {
        int model_id PK
        string model_name
        string drive_kinematics
        decimal payload_capacity_kg
        decimal max_speed_mps
    }

    ROBOT_UNIT {
        int robot_id PK
        int model_id FK
        string robot_name
        string serial_number
        string ros_domain_id
        string ip_address
        string status
    }

    FLEET_OPERATOR {
        int operator_id PK
        string full_name
        string role_title
        string shift_schedule
    }

    WAYPOINT_MAP {
        int map_id PK
        string map_name
        string cad_file_url
        decimal resolution_mpx
        string occupancy_grid_url
    }

    MISSION_TASK {
        int task_id PK
        int robot_id FK
        int operator_id FK
        int map_id FK
        string task_name
        string pickup_waypoint
        string dropoff_waypoint
        string priority
        string task_status
        datetime dispatched_at
    }

    DOCKING_STATION {
        int dock_id PK
        int map_id FK
        string dock_code
        string charging_type
        decimal max_current_amps
        string occupancy_status
    }

    BATTERY_STATUS {
        int battery_id PK
        int robot_id FK
        decimal state_of_charge_pct
        decimal voltage_volts
        decimal temperature_celsius
        int charge_cycles
        datetime updated_at
    }

    TELEMETRY_LOG {
        int telemetry_id PK
        int robot_id FK
        decimal pose_x
        decimal pose_y
        decimal pose_orientation
        decimal linear_velocity
        datetime logged_at
    }

    COLLISION_EVENT {
        int event_id PK
        int robot_id FK
        int task_id FK
        string trigger_source
        decimal location_x
        decimal location_y
        datetime incident_time
    }

    MAINTENANCE_LOG {
        int maintenance_id PK
        int robot_id FK
        string technician_name
        string service_type
        string components_replaced
        datetime service_date
    }

    FIRMWARE_RELEASE {
        int firmware_id PK
        int model_id FK
        string version_code
        string container_image_uri
        datetime release_date
    }

    ROBOT_MODEL ||--o{ ROBOT_UNIT : "defines_specs"
    ROBOT_UNIT ||--o{ MISSION_TASK : "executes"
    FLEET_OPERATOR ||--o{ MISSION_TASK : "dispatches"
    WAYPOINT_MAP ||--o{ MISSION_TASK : "provides_routes"
    WAYPOINT_MAP ||--o{ DOCKING_STATION : "contains_docks"
    ROBOT_UNIT ||--|| BATTERY_STATUS : "monitors_power"
    ROBOT_UNIT ||--o{ TELEMETRY_LOG : "streams"
    ROBOT_UNIT ||--o{ COLLISION_EVENT : "triggers"
    MISSION_TASK ||--o{ COLLISION_EVENT : "occurs_during"
    ROBOT_UNIT ||--o{ MAINTENANCE_LOG : "services"
    ROBOT_MODEL ||--o{ FIRMWARE_RELEASE : "receives_updates"
    ROBOT_UNIT ||--o{ DOCKING_STATION : "charges_at"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|-------------------|
| 1 | ROBOT_MODEL | Dòng / Model Robot | Hardware model specifications (Differential, Ackerman, Omni) defining payload and top speed. | model_id (PK), model_name, drive_kinematics, payload_capacity_kg | Defines specs for Robot Units, receives Firmware Releases |
| 2 | ROBOT_UNIT | Đơn vị Robot (AMR) | Individual autonomous robot instance operating on facility floors with IP and status. | robot_id (PK), model_id (FK), robot_name, serial_number, status | Defined by Model, executes Tasks, streams Telemetry, charges at Docking Stations |
| 3 | FLEET_OPERATOR | Điều hành Viên | Human operator or dispatcher creating transport missions and monitoring telemetry. | operator_id (PK), full_name, role_title, shift_schedule | Dispatches Mission Tasks |
| 4 | WAYPOINT_MAP | Bản đồ SLAM / CAD | Digital facility map containing occupancy grid tiles, coordinate anchors, and docking spots. | map_id (PK), map_name, cad_file_url, resolution_mpx | Provides routes for Tasks, contains Docking Stations |
| 5 | MISSION_TASK | Nhiệm vụ Vận chuyển | Material transport, picking, or inspection mission assigned to a specific robot. | task_id (PK), robot_id (FK), operator_id (FK), pickup_waypoint, task_status | Assigned to Robot Unit, dispatched by Operator, routed on Waypoint Map |
| 6 | DOCKING_STATION | Trạm Sạc Tự động | IoT charging station managing inductive or contact battery charging for robots. | dock_id (PK), map_id (FK), dock_code, charging_type, occupancy_status | Located on Waypoint Map, charges Robot Units |
| 7 | BATTERY_STATUS | Trạng thái Pin | Real-time battery monitoring record tracking State of Charge (SOC), voltage, and health cycles. | battery_id (PK), robot_id (FK), state_of_charge_pct, voltage_volts, charge_cycles | Monitors Robot Unit power |
| 8 | TELEMETRY_LOG | Nhật ký Sensor Telemetry | High-frequency telemetry log recording robot pose (X, Y, Theta), velocity, and sensor health. | telemetry_id (PK), robot_id (FK), pose_x, pose_y, linear_velocity, logged_at | Streamed from Robot Unit |
| 9 | COLLISION_EVENT | Sự cố Báo động Safety | Emergency stop or safety field breach event recording incident location and trigger source. | event_id (PK), robot_id (FK), task_id (FK), trigger_source, location_x | Triggered by Robot Unit during Mission Task |
| 10 | MAINTENANCE_LOG | Nhật ký Bảo trì | Technical service log recording motor repairs, wheel replacements, and sensor tuning. | maintenance_id (PK), robot_id (FK), technician_name, service_type, service_date | Services Robot Unit |
| 11 | FIRMWARE_RELEASE | Bản cập nhật Firmware | OTA container image package or ROS 2 node software build deployed across robot fleets. | firmware_id (PK), model_id (FK), version_code, container_image_uri | Updates Robot Model |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | ROBOT_MODEL | one-to-many | ROBOT_UNIT | defines_specs | A Robot Model defines hardware specifications for multiple Robot Units. |
| 2 | ROBOT_UNIT | one-to-many | MISSION_TASK | executes | A Robot Unit executes multiple Mission Tasks over time. |
| 3 | FLEET_OPERATOR | one-to-many | MISSION_TASK | dispatches | A Fleet Operator dispatches multiple Mission Tasks. |
| 4 | WAYPOINT_MAP | one-to-many | MISSION_TASK | provides_routes | A Waypoint Map provides route waypoints for multiple Mission Tasks. |
| 5 | WAYPOINT_MAP | one-to-many | DOCKING_STATION | contains_docks | A Waypoint Map contains multiple physical Docking Stations. |
| 6 | ROBOT_UNIT | one-to-one | BATTERY_STATUS | monitors_power | A Robot Unit monitors its power via a unique Battery Status record. |
| 7 | ROBOT_UNIT | one-to-many | TELEMETRY_LOG | streams | A Robot Unit streams high-frequency sensor Telemetry Logs. |
| 8 | ROBOT_UNIT | one-to-many | COLLISION_EVENT | triggers | A Robot Unit can trigger Collision Events upon safety breaches. |
| 9 | MISSION_TASK | one-to-many | COLLISION_EVENT | occurs_during | A Collision Event occurs during a specific Mission Task execution. |
| 10 | ROBOT_UNIT | one-to-many | MAINTENANCE_LOG | services | A Robot Unit receives multiple Maintenance Logs over its lifespan. |
| 11 | ROBOT_MODEL | one-to-many | FIRMWARE_RELEASE | receives_updates | A Robot Model receives multiple OTA Firmware Releases. |
| 12 | ROBOT_UNIT | many-to-many | DOCKING_STATION | charges_at | Robot Units charge at multiple Docking Stations. |
