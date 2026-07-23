# Conceptual ERD — Manufacturing Cost Analysis System

## Mermaid Code

```mermaid
erDiagram
    USER_OPERATOR {
        operator_id PK
        full_name
        badge_number
        role_code
        skill_level
        shift_id FK
        status
    }
    MANUFACTURING_WORK_ORDER {
        order_id PK
        order_number
        product_id FK
        planned_qty
        completed_qty
        scrap_qty
        line_id FK
        status
        start_time
        end_time
    }
    PRODUCT_CATALOG {
        product_id PK
        sku_code
        product_name
        revision_id
        target_cycle_time_sec
        standard_bom_id FK
    }
    EQUIPMENT_ASSET {
        equipment_id PK
        asset_code
        line_id FK
        equipment_name
        serial_number
        status
        oee_score
        last_maintenance_date
    }
    BATCH_RUN {
        batch_id PK
        order_id FK
        batch_number
        start_time
        end_time
        total_yield
        status
    }
    QUALITY_INSPECTION {
        inspection_id PK
        batch_id FK
        operator_id FK
        sample_size
        defect_qty
        ucl_value
        lcl_value
        result_status
        inspected_at
    }
    DOWNTIME_EVENT {
        downtime_id PK
        equipment_id FK
        reason_code
        start_timestamp
        end_timestamp
        duration_minutes
        technician_id FK
    }
    TELEMETRY_LOG {
        telemetry_id PK
        equipment_id FK
        sensor_name
        read_value
        unit_of_measure
        is_anomaly
        timestamp
    }

    PRODUCT_CATALOG ||--o{ MANUFACTURING_WORK_ORDER : "defines"
    USER_OPERATOR ||--o{ MANUFACTURING_WORK_ORDER : "executes"
    MANUFACTURING_WORK_ORDER ||--o{ BATCH_RUN : "divides_into"
    BATCH_RUN ||--o{ QUALITY_INSPECTION : "inspected_by"
    USER_OPERATOR ||--o{ QUALITY_INSPECTION : "conducts"
    EQUIPMENT_ASSET ||--o{ TELEMETRY_LOG : "streams"
    EQUIPMENT_ASSET ||--o{ DOWNTIME_EVENT : "incurs"
    MANUFACTURING_WORK_ORDER }o--o{ EQUIPMENT_ASSET : "assigned_to"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|--------------------|
| 1 | USER_OPERATOR | Người vận hành / Nhân sự | Stores factory personnel credentials, roles, shift assignments, and certifications. | operator_id PK, full_name, badge_number, role_code, skill_level, shift_id FK, status | has many WORK_ORDER_LOG, has many QUALITY_INSPECTION |
| 2 | MANUFACTURING_WORK_ORDER | Đơn hàng Sản xuất | Master production work order tracking product, target quantity, line, and status in Manufacturing Cost Analysis System. | order_id PK, order_number, product_id FK, planned_qty, completed_qty, scrap_qty, line_id FK, status, start_time, end_time | belongs to PRODUCT_CATALOG, has many BATCH_RUN, has many QUALITY_INSPECTION |
| 3 | PRODUCT_CATALOG | Danh mục Sản phẩm / SKU | Finished goods, assemblies, and SKU specifications. | product_id PK, sku_code, product_name, revision_id, target_cycle_time_sec, standard_bom_id FK | has many MANUFACTURING_WORK_ORDER |
| 4 | EQUIPMENT_ASSET | Thiết bị / Máy móc | Production line machinery, PLC units, robots, and workstations. | equipment_id PK, asset_code, line_id FK, equipment_name, serial_number, status, oee_score, last_maintenance_date | has many TELEMETRY_LOG, has many DOWNTIME_EVENT |
| 5 | BATCH_RUN | Lô Sản xuất | Granular production batch run details, lot numbers, and execution logs. | batch_id PK, order_id FK, batch_number, start_time, end_time, total_yield, status | belongs to MANUFACTURING_WORK_ORDER, has many QUALITY_INSPECTION |
| 6 | QUALITY_INSPECTION | Kiểm tra Chất lượng | Inspection records, measurements, pass/fail results, and defect counts. | inspection_id PK, batch_id FK, operator_id FK, sample_size, defect_qty, ucl_value, lcl_value, result_status, inspected_at | belongs to BATCH_RUN, belongs to USER_OPERATOR |
| 7 | DOWNTIME_EVENT | Sự cố Dừng máy | Unplanned and planned downtime events, failure codes, and duration. | downtime_id PK, equipment_id FK, reason_code, start_timestamp, end_timestamp, duration_minutes, technician_id FK | belongs to EQUIPMENT_ASSET |
| 8 | TELEMETRY_LOG | Nhật ký Telemetry / Sensor | Timeseries sensor data (vibration, temp, pressure, speed) streamed from PLC. | telemetry_id PK, equipment_id FK, sensor_name, read_value, unit_of_measure, is_anomaly, timestamp | belongs to EQUIPMENT_ASSET |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | PRODUCT_CATALOG | ||--o{ | MANUFACTURING_WORK_ORDER | defines | Một mã sản phẩm SKU có thể được sản xuất qua nhiều đơn hàng sản xuất. |
| 2 | USER_OPERATOR | ||--o{ | MANUFACTURING_WORK_ORDER | executes | Người vận hành thực thi công việc trên các đơn hàng sản xuất. |
| 3 | MANUFACTURING_WORK_ORDER | ||--o{ | BATCH_RUN | divides_into | Một đơn hàng sản xuất được chia thành nhiều lô sản xuất. |
| 4 | BATCH_RUN | ||--o{ | QUALITY_INSPECTION | inspected_by | Một lô sản xuất trải qua nhiều lượt kiểm tra chất lượng. |
| 5 | USER_OPERATOR | ||--o{ | QUALITY_INSPECTION | conducts | Nhân viên chất lượng thực hiện các bài kiểm tra. |
| 6 | EQUIPMENT_ASSET | ||--o{ | TELEMETRY_LOG | streams | Một thiết bị máy móc liên tục truyền dữ liệu sensor telemetry. |
| 7 | EQUIPMENT_ASSET | ||--o{ | DOWNTIME_EVENT | incurs | Một máy móc ghi nhận các sự kiện dừng máy và hỏng hóc. |
| 8 | MANUFACTURING_WORK_ORDER | }o--o{ | EQUIPMENT_ASSET | assigned_to | Đơn hàng sản xuất được gán vào các dây chuyền thiết bị. |

