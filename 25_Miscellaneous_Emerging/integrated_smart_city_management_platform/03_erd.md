# Conceptual ERD — Integrated Smart City Management Platform

## Mermaid Code

```mermaid
erDiagram
    CITY_COMMANDER_USER {
        int commander_id PK
        string full_name
        string agency_department
        string clearance_level
        string email
    }

    CITY_INFRASTRUCTURE_SECTOR {
        int sector_id PK
        string sector_code
        string sector_name
        string geographic_boundary_geojson
        int total_active_iot_devices
    }

    SMART_CITY_IOT_DEVICE {
        int device_id PK
        int sector_id FK
        string hardware_serial_number
        string device_category
        decimal latitude
        decimal longitude
        string device_status
        datetime installed_at
    }

    CITY_OPERATIONS_INCIDENT {
        int incident_id PK
        int sector_id FK
        int commander_id FK
        string incident_type
        string severity_level
        string incident_status
        datetime reported_at
    }

    TRAFFIC_SIGNAL_CONTROLLER {
        int controller_id PK
        int device_id FK
        string intersection_name
        int active_signal_plan_id
        decimal current_queue_length_m
        boolean emergency_green_wave_active
    }

    POWER_GRID_SUBSTATION {
        int substation_id PK
        int device_id FK
        string substation_name
        decimal load_capacity_mw
        decimal current_load_mw
        decimal solar_generation_input_mw
    }

    WASTE_CONTAINER_SENSOR {
        int sensor_id PK
        int device_id FK
        string container_code
        int fill_percentage
        decimal temperature_celsius
        datetime last_emptied_at
    }

    PUBLIC_TRANSIT_VEHICLE {
        int vehicle_id PK
        int device_id FK
        string vehicle_fleet_code
        string route_number
        decimal current_latitude
        decimal current_longitude
        int passenger_count
    }

    AIR_QUALITY_MONITOR {
        int monitor_id PK
        int device_id FK
        decimal pm25_concentration
        decimal pm10_concentration
        decimal no2_ppm
        int air_quality_index_aqi
    }

    EMERGENCY_DISPATCH_CALL {
        int call_id PK
        int incident_id FK
        string cad_reference_number
        string responding_agency
        int responding_units_count
        datetime dispatched_at
    }

    MUNICIPAL_UTILITY_TARIFF {
        int tariff_id PK
        int sector_id FK
        string utility_type
        decimal peak_rate_per_kwh
        decimal offpeak_rate_per_kwh
        datetime effective_date
    }

    CITY_INFRASTRUCTURE_SECTOR ||--o{ SMART_CITY_IOT_DEVICE : "contains_devices"
    CITY_INFRASTRUCTURE_SECTOR ||--o{ CITY_OPERATIONS_INCIDENT : "occurs_in"
    CITY_COMMANDER_USER ||--o{ CITY_OPERATIONS_INCIDENT : "manages_incident"
    SMART_CITY_IOT_DEVICE ||--|| TRAFFIC_SIGNAL_CONTROLLER : "controls_traffic"
    SMART_CITY_IOT_DEVICE ||--|| POWER_GRID_SUBSTATION : "monitors_power"
    SMART_CITY_IOT_DEVICE ||--|| WASTE_CONTAINER_SENSOR : "measures_waste"
    SMART_CITY_IOT_DEVICE ||--|| PUBLIC_TRANSIT_VEHICLE : "tracks_transit"
    SMART_CITY_IOT_DEVICE ||--|| AIR_QUALITY_MONITOR : "measures_air"
    CITY_OPERATIONS_INCIDENT ||--o{ EMERGENCY_DISPATCH_CALL : "triggers_cad"
    CITY_INFRASTRUCTURE_SECTOR ||--o{ MUNICIPAL_UTILITY_TARIFF : "applies_tariff"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|-------------------|
| 1 | CITY_COMMANDER_USER | Cán bộ Điều hành Thành phố | Municipal operations commander, city manager, or emergency coordinator user profile. | commander_id (PK), full_name, agency_department, clearance_level | Manages Incidents |
| 2 | CITY_INFRASTRUCTURE_SECTOR | Phân khu Hạ tầng Thành phố | Geographic urban district or sector boundary (Downtown, Industrial Park, Waterfront). | sector_id (PK), sector_code, sector_name, geographic_boundary_geojson | Contains Devices, occurs Incidents, applies Tariffs |
| 3 | SMART_CITY_IOT_DEVICE | Thiết bị IoT Thành phố | Physical IoT gateway or sensor node deployed across city infrastructure. | device_id (PK), sector_id (FK), hardware_serial_number, device_category, latitude, longitude | Contained in Sector, specializes into Traffic/Power/Waste/Transit/Air |
| 4 | CITY_OPERATIONS_INCIDENT | Sự cố Điều hành Thành phố | Urban operational incident record (Traffic Jam, Power Outage, Water Burst, Chemical Spill). | incident_id (PK), sector_id (FK), commander_id (FK), incident_type, severity_level | Occurs in Sector, managed by Commander, triggers CAD Calls |
| 5 | TRAFFIC_SIGNAL_CONTROLLER | Bộ Điều khiển Đèn Giao thông | Smart traffic signal controller managing intersection signal phases and green-wave overrides. | controller_id (PK), device_id (FK), intersection_name, active_signal_plan_id, current_queue_length_m | Specialized from Smart City IoT Device |
| 6 | POWER_GRID_SUBSTATION | Trạm Biến áp Lưới Điện | Electrical power substation monitoring grid load, solar input MW, and transformer status. | substation_id (PK), device_id (FK), substation_name, load_capacity_mw, current_load_mw | Specialized from Smart City IoT Device |
| 7 | WASTE_CONTAINER_SENSOR | Cảm biến Thùng Rác Thông minh | Ultrasonic sensor inside municipal trash container tracking fill level % and temperature. | sensor_id (PK), device_id (FK), container_code, fill_percentage, temperature_celsius | Specialized from Smart City IoT Device |
| 8 | PUBLIC_TRANSIT_VEHICLE | Xe Giao thông Công cộng | Municipal bus or light-rail vehicle tracking GPS coordinates, route number, and passenger counts. | vehicle_id (PK), device_id (FK), vehicle_fleet_code, route_number, current_latitude | Specialized from Smart City IoT Device |
| 9 | AIR_QUALITY_MONITOR | Cảm biến Chất lượng Không khí | Environmental sensor station measuring PM2.5, PM10, NO2, and computing Air Quality Index (AQI). | monitor_id (PK), device_id (FK), pm25_concentration, no2_ppm, air_quality_index_aqi | Specialized from Smart City IoT Device |
| 10 | EMERGENCY_DISPATCH_CALL | Cuộc gọi Điều động Khẩn cấp | Inter-agency emergency CAD dispatch record linking police/fire calls to city incidents. | call_id (PK), incident_id (FK), cad_reference_number, responding_agency, responding_units_count | Triggered by City Operations Incident |
| 11 | MUNICIPAL_UTILITY_TARIFF | Biểu giá Tiện ích Đô thị | Municipal tariff structure defining peak/off-peak power rates and water pricing for sectors. | tariff_id (PK), sector_id (FK), utility_type, peak_rate_per_kwh, offpeak_rate_per_kwh | Applied to City Infrastructure Sector |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | CITY_INFRASTRUCTURE_SECTOR | one-to-many | SMART_CITY_IOT_DEVICE | contains_devices | A City Infrastructure Sector contains multiple Smart City IoT Devices. |
| 2 | CITY_INFRASTRUCTURE_SECTOR | one-to-many | CITY_OPERATIONS_INCIDENT | occurs_in | A City Infrastructure Sector has multiple City Operations Incidents. |
| 3 | CITY_COMMANDER_USER | one-to-many | CITY_OPERATIONS_INCIDENT | manages_incident | A City Commander User manages multiple City Operations Incidents. |
| 4 | SMART_CITY_IOT_DEVICE | one-to-one | TRAFFIC_SIGNAL_CONTROLLER | controls_traffic | A Smart City IoT Device specializes as a Traffic Signal Controller. |
| 5 | SMART_CITY_IOT_DEVICE | one-to-one | POWER_GRID_SUBSTATION | monitors_power | A Smart City IoT Device specializes as a Power Grid Substation. |
| 6 | SMART_CITY_IOT_DEVICE | one-to-one | WASTE_CONTAINER_SENSOR | measures_waste | A Smart City IoT Device specializes as a Waste Container Sensor. |
| 7 | SMART_CITY_IOT_DEVICE | one-to-one | PUBLIC_TRANSIT_VEHICLE | tracks_transit | A Smart City IoT Device specializes as a Public Transit Vehicle. |
| 8 | SMART_CITY_IOT_DEVICE | one-to-one | AIR_QUALITY_MONITOR | measures_air | A Smart City IoT Device specializes as an Air Quality Monitor. |
| 9 | CITY_OPERATIONS_INCIDENT | one-to-many | EMERGENCY_DISPATCH_CALL | triggers_cad | A City Operations Incident triggers multiple Emergency Dispatch Calls. |
| 10 | CITY_INFRASTRUCTURE_SECTOR | one-to-many | MUNICIPAL_UTILITY_TARIFF | applies_tariff | A City Infrastructure Sector applies multiple Municipal Utility Tariffs. |
