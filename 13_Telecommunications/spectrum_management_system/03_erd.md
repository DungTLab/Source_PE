# Conceptual ERD — Spectrum Management System

## Mermaid Code

```mermaid
erDiagram
    SPECTRUMMANAGEMENTSYSTEM_ELEMENT {
        element_id PK
        element_name string
        serial_number string
        ip_address string
        status string
        created_at datetime
    }
    OPERATIONAL_SESSION {
        session_id PK
        element_id FK
        start_time datetime
        end_time datetime
        bandwidth_used decimal
        session_status string
    }
    FAULT_ALARM {
        alarm_id PK
        element_id FK
        severity string
        alarm_code string
        triggered_at datetime
        resolved_at datetime
    }
    MAINTENANCE_TICKET {
        ticket_id PK
        element_id FK
        assigned_engineer string
        work_description string
        ticket_status string
        created_at datetime
    }
    CONFIGURATION_POLICY {
        policy_id PK
        policy_name string
        threshold_value string
        active_flag boolean
        updated_at datetime
    }
    PERFORMANCE_METRIC {
        metric_id PK
        element_id FK
        cpu_load decimal
        latency_ms decimal
        throughput_mbps decimal
        timestamp datetime
    }
    AUDIT_LOG_ENTRY {
        log_id PK
        user_id string
        action_type string
        details string
        ip_address string
        timestamp datetime
    }
    SLA_REPORT {
        report_id PK
        period_name string
        availability_pct decimal
        total_outage_min int
        compliance_status string
        generated_at datetime
    }

    SPECTRUMMANAGEMENTSYSTEM_ELEMENT ||--o{ OPERATIONAL_SESSION : "handles"
    SPECTRUMMANAGEMENTSYSTEM_ELEMENT ||--o{ FAULT_ALARM : "triggers"
    SPECTRUMMANAGEMENTSYSTEM_ELEMENT ||--o{ MAINTENANCE_TICKET : "requires"
    SPECTRUMMANAGEMENTSYSTEM_ELEMENT ||--o{ PERFORMANCE_METRIC : "emits"
    CONFIGURATION_POLICY ||--o{ SPECTRUMMANAGEMENTSYSTEM_ELEMENT : "governs"
    MAINTENANCE_TICKET ||--o{ AUDIT_LOG_ENTRY : "generates"
    FAULT_ALARM ||--o{ SLA_REPORT : "analyzed_in"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|-------------------|
| 1 | SPECTRUMMANAGEMENTSYSTEM_ELEMENT | Phần tử Hệ Thống Quản Lý Tần Số Vô Tuyến | Main operational unit in Spectrum Management System | element_id PK, element_name string, serial_number string | handles, triggers, requires, emits, governs |
| 2 | OPERATIONAL_SESSION | Phiên Hoạt động | Active processing or monitoring session | session_id PK, element_id FK, start_time datetime | handles |
| 3 | FAULT_ALARM | Cảnh báo Lỗi | Incident and fault alarm alerts | alarm_id PK, element_id FK, severity string | triggers, analyzed_in |
| 4 | MAINTENANCE_TICKET | Phiếu Bảo trì | Field engineer work ticket | ticket_id PK, element_id FK, assigned_engineer string | requires, generates |
| 5 | CONFIGURATION_POLICY | Chính sách Cấu hình | System policy configuration rules | policy_id PK, policy_name string, threshold_value string | governs |
| 6 | PERFORMANCE_METRIC | Chỉ số Hiệu năng | Time-series telemetry performance data | metric_id PK, element_id FK, cpu_load decimal | emits |
| 7 | AUDIT_LOG_ENTRY | Nhật ký Kiểm toán | System access and transaction audit trail | log_id PK, user_id string, action_type string | generates |
| 8 | SLA_REPORT | Báo cáo SLA | Statutory compliance report record | report_id PK, period_name string, availability_pct decimal | analyzed_in |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | SPECTRUMMANAGEMENTSYSTEM_ELEMENT | one-to-many | OPERATIONAL_SESSION | handles | One element handles multiple operational sessions |
| 2 | SPECTRUMMANAGEMENTSYSTEM_ELEMENT | one-to-many | FAULT_ALARM | triggers | One element triggers multiple fault alarms |
| 3 | SPECTRUMMANAGEMENTSYSTEM_ELEMENT | one-to-many | MAINTENANCE_TICKET | requires | One element may require multiple maintenance tickets |
| 4 | SPECTRUMMANAGEMENTSYSTEM_ELEMENT | one-to-many | PERFORMANCE_METRIC | emits | One element emits time-series performance metrics |
| 5 | CONFIGURATION_POLICY | one-to-many | SPECTRUMMANAGEMENTSYSTEM_ELEMENT | governs | One policy governs multiple network elements |
| 6 | MAINTENANCE_TICKET | one-to-many | AUDIT_LOG_ENTRY | generates | Maintenance ticket activities generate audit entries |
| 7 | FAULT_ALARM | one-to-many | SLA_REPORT | analyzed_in | Fault alarms are analyzed in periodic SLA compliance reports |
