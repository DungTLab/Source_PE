# Conceptual ERD — Mini-Bar & In-Room Service Management System

## Mermaid Code

```mermaid
erDiagram
    MINIBAR_INROOM_SERVICE_RECORD {
        record_id PK
        guest_id FK
        service_code
        status
        created_at
    }
    MINIBAR_INROOM_SERVICE_DETAIL {
        detail_id PK
        record_id FK
        item_name
        quantity
        unit_price
    }
    MINIBAR_INROOM_SERVICE_CATALOG {
        catalog_id PK
        category_name
        base_price
        is_active
    }
    MINIBAR_INROOM_SERVICE_TRANSACTION {
        trans_id PK
        record_id FK
        payment_method
        amount
        trans_date
    }
    MINIBAR_INROOM_SERVICE_STAFF_ASSIGNMENT {
        assignment_id PK
        record_id FK
        staff_id
        assigned_time
        completion_time
    }
    MINIBAR_INROOM_SERVICE_AUDIT_LOG {
        log_id PK
        record_id FK
        user_id
        action_type
        timestamp
    }
    MINIBAR_INROOM_SERVICE_FEEDBACK {
        feedback_id PK
        record_id FK
        rating_score
        comment
        created_at
    }
    MINIBAR_INROOM_SERVICE_CONFIG {
        config_id PK
        param_key
        param_value
        description
    }

    MINIBAR_INROOM_SERVICE_RECORD ||--o{ MINIBAR_INROOM_SERVICE_DETAIL : "contains"
    MINIBAR_INROOM_SERVICE_RECORD ||--o{ MINIBAR_INROOM_SERVICE_TRANSACTION : "settles"
    MINIBAR_INROOM_SERVICE_CATALOG ||--o{ MINIBAR_INROOM_SERVICE_DETAIL : "applies to"
    MINIBAR_INROOM_SERVICE_RECORD ||--o{ MINIBAR_INROOM_SERVICE_STAFF_ASSIGNMENT : "tracks"
    MINIBAR_INROOM_SERVICE_RECORD ||--o{ MINIBAR_INROOM_SERVICE_AUDIT_LOG : "audits"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|--------------------|
| 1 | MINIBAR_INROOM_SERVICE_RECORD | Hồ sơ Room Service | Bản ghi nghiệp vụ chính của Mini-Bar & In-Room Service Management System | record_id PK, guest_id FK, service_code, status, created_at | contains MINIBAR_INROOM_SERVICE_DETAIL |
| 2 | MINIBAR_INROOM_SERVICE_DETAIL | Chi tiết Room Service | Chi tiết từng hạng mục dịch vụ | detail_id PK, record_id FK, item_name, quantity, unit_price | belongs to MINIBAR_INROOM_SERVICE_RECORD |
| 3 | MINIBAR_INROOM_SERVICE_CATALOG | Danh mục dịch vụ | Danh mục bảng giá và cấu hình | catalog_id PK, category_name, base_price, is_active | applies to MINIBAR_INROOM_SERVICE_DETAIL |
| 4 | MINIBAR_INROOM_SERVICE_TRANSACTION | Giao dịch tài chính | Lịch sử thanh toán dịch vụ | trans_id PK, record_id FK, payment_method, amount, trans_date | settles MINIBAR_INROOM_SERVICE_RECORD |
| 5 | MINIBAR_INROOM_SERVICE_STAFF_ASSIGNMENT | Phân công nhân sự | Lịch phân công thực hiện công việc | assignment_id PK, record_id FK, staff_id, assigned_time, completion_time | tracks MINIBAR_INROOM_SERVICE_RECORD |
| 6 | MINIBAR_INROOM_SERVICE_AUDIT_LOG | Nhật ký kiểm toán | Lưu vết thao tác người dùng | log_id PK, record_id FK, user_id, action_type, timestamp | audits MINIBAR_INROOM_SERVICE_RECORD |
| 7 | MINIBAR_INROOM_SERVICE_FEEDBACK | Đánh giá dịch vụ | Phản hồi của khách hàng | feedback_id PK, record_id FK, rating_score, comment, created_at | evaluates MINIBAR_INROOM_SERVICE_RECORD |
| 8 | MINIBAR_INROOM_SERVICE_CONFIG | Cấu hình hệ thống | Tham số quy tắc vận hành | config_id PK, param_key, param_value, description | configures System |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | MINIBAR_INROOM_SERVICE_RECORD | one-to-many | MINIBAR_INROOM_SERVICE_DETAIL | contains | Một hồ sơ nghiệp vụ chứa nhiều hạng mục chi tiết |
| 2 | MINIBAR_INROOM_SERVICE_RECORD | one-to-many | MINIBAR_INROOM_SERVICE_TRANSACTION | settles | Một hồ sơ nghiệp vụ có thể thanh toán qua nhiều lần giao dịch |
| 3 | MINIBAR_INROOM_SERVICE_CATALOG | one-to-many | MINIBAR_INROOM_SERVICE_DETAIL | applies to | Danh mục áp dụng đơn giá cho chi tiết dịch vụ |
| 4 | MINIBAR_INROOM_SERVICE_RECORD | one-to-many | MINIBAR_INROOM_SERVICE_STAFF_ASSIGNMENT | tracks | Hồ sơ ghi nhận các đợt phân công nhân viên xử lý |
| 5 | MINIBAR_INROOM_SERVICE_RECORD | one-to-many | MINIBAR_INROOM_SERVICE_AUDIT_LOG | audits | Nhật ký lưu trữ tất cả thao tác biến động của hồ sơ |
