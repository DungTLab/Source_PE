# Conceptual ERD — OTA Integration System

## Mermaid Code

```mermaid
erDiagram
    OTA_INTEGRATION_RECORD {
        record_id PK
        guest_id FK
        service_code
        status
        created_at
    }
    OTA_INTEGRATION_DETAIL {
        detail_id PK
        record_id FK
        item_name
        quantity
        unit_price
    }
    OTA_INTEGRATION_CATALOG {
        catalog_id PK
        category_name
        base_price
        is_active
    }
    OTA_INTEGRATION_TRANSACTION {
        trans_id PK
        record_id FK
        payment_method
        amount
        trans_date
    }
    OTA_INTEGRATION_STAFF_ASSIGNMENT {
        assignment_id PK
        record_id FK
        staff_id
        assigned_time
        completion_time
    }
    OTA_INTEGRATION_AUDIT_LOG {
        log_id PK
        record_id FK
        user_id
        action_type
        timestamp
    }
    OTA_INTEGRATION_FEEDBACK {
        feedback_id PK
        record_id FK
        rating_score
        comment
        created_at
    }
    OTA_INTEGRATION_CONFIG {
        config_id PK
        param_key
        param_value
        description
    }

    OTA_INTEGRATION_RECORD ||--o{ OTA_INTEGRATION_DETAIL : "contains"
    OTA_INTEGRATION_RECORD ||--o{ OTA_INTEGRATION_TRANSACTION : "settles"
    OTA_INTEGRATION_CATALOG ||--o{ OTA_INTEGRATION_DETAIL : "applies to"
    OTA_INTEGRATION_RECORD ||--o{ OTA_INTEGRATION_STAFF_ASSIGNMENT : "tracks"
    OTA_INTEGRATION_RECORD ||--o{ OTA_INTEGRATION_AUDIT_LOG : "audits"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|--------------------|
| 1 | OTA_INTEGRATION_RECORD | Hồ sơ Distribution | Bản ghi nghiệp vụ chính của OTA Integration System | record_id PK, guest_id FK, service_code, status, created_at | contains OTA_INTEGRATION_DETAIL |
| 2 | OTA_INTEGRATION_DETAIL | Chi tiết Distribution | Chi tiết từng hạng mục dịch vụ | detail_id PK, record_id FK, item_name, quantity, unit_price | belongs to OTA_INTEGRATION_RECORD |
| 3 | OTA_INTEGRATION_CATALOG | Danh mục dịch vụ | Danh mục bảng giá và cấu hình | catalog_id PK, category_name, base_price, is_active | applies to OTA_INTEGRATION_DETAIL |
| 4 | OTA_INTEGRATION_TRANSACTION | Giao dịch tài chính | Lịch sử thanh toán dịch vụ | trans_id PK, record_id FK, payment_method, amount, trans_date | settles OTA_INTEGRATION_RECORD |
| 5 | OTA_INTEGRATION_STAFF_ASSIGNMENT | Phân công nhân sự | Lịch phân công thực hiện công việc | assignment_id PK, record_id FK, staff_id, assigned_time, completion_time | tracks OTA_INTEGRATION_RECORD |
| 6 | OTA_INTEGRATION_AUDIT_LOG | Nhật ký kiểm toán | Lưu vết thao tác người dùng | log_id PK, record_id FK, user_id, action_type, timestamp | audits OTA_INTEGRATION_RECORD |
| 7 | OTA_INTEGRATION_FEEDBACK | Đánh giá dịch vụ | Phản hồi của khách hàng | feedback_id PK, record_id FK, rating_score, comment, created_at | evaluates OTA_INTEGRATION_RECORD |
| 8 | OTA_INTEGRATION_CONFIG | Cấu hình hệ thống | Tham số quy tắc vận hành | config_id PK, param_key, param_value, description | configures System |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | OTA_INTEGRATION_RECORD | one-to-many | OTA_INTEGRATION_DETAIL | contains | Một hồ sơ nghiệp vụ chứa nhiều hạng mục chi tiết |
| 2 | OTA_INTEGRATION_RECORD | one-to-many | OTA_INTEGRATION_TRANSACTION | settles | Một hồ sơ nghiệp vụ có thể thanh toán qua nhiều lần giao dịch |
| 3 | OTA_INTEGRATION_CATALOG | one-to-many | OTA_INTEGRATION_DETAIL | applies to | Danh mục áp dụng đơn giá cho chi tiết dịch vụ |
| 4 | OTA_INTEGRATION_RECORD | one-to-many | OTA_INTEGRATION_STAFF_ASSIGNMENT | tracks | Hồ sơ ghi nhận các đợt phân công nhân viên xử lý |
| 5 | OTA_INTEGRATION_RECORD | one-to-many | OTA_INTEGRATION_AUDIT_LOG | audits | Nhật ký lưu trữ tất cả thao tác biến động của hồ sơ |
