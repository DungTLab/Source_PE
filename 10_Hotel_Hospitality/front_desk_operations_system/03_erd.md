# Conceptual ERD — Front Desk Operations System

## Mermaid Code

```mermaid
erDiagram
    FRONT_DESK_OPERATIONS_RECORD {
        record_id PK
        guest_id FK
        service_code
        status
        created_at
    }
    FRONT_DESK_OPERATIONS_DETAIL {
        detail_id PK
        record_id FK
        item_name
        quantity
        unit_price
    }
    FRONT_DESK_OPERATIONS_CATALOG {
        catalog_id PK
        category_name
        base_price
        is_active
    }
    FRONT_DESK_OPERATIONS_TRANSACTION {
        trans_id PK
        record_id FK
        payment_method
        amount
        trans_date
    }
    FRONT_DESK_OPERATIONS_STAFF_ASSIGNMENT {
        assignment_id PK
        record_id FK
        staff_id
        assigned_time
        completion_time
    }
    FRONT_DESK_OPERATIONS_AUDIT_LOG {
        log_id PK
        record_id FK
        user_id
        action_type
        timestamp
    }
    FRONT_DESK_OPERATIONS_FEEDBACK {
        feedback_id PK
        record_id FK
        rating_score
        comment
        created_at
    }
    FRONT_DESK_OPERATIONS_CONFIG {
        config_id PK
        param_key
        param_value
        description
    }

    FRONT_DESK_OPERATIONS_RECORD ||--o{ FRONT_DESK_OPERATIONS_DETAIL : "contains"
    FRONT_DESK_OPERATIONS_RECORD ||--o{ FRONT_DESK_OPERATIONS_TRANSACTION : "settles"
    FRONT_DESK_OPERATIONS_CATALOG ||--o{ FRONT_DESK_OPERATIONS_DETAIL : "applies to"
    FRONT_DESK_OPERATIONS_RECORD ||--o{ FRONT_DESK_OPERATIONS_STAFF_ASSIGNMENT : "tracks"
    FRONT_DESK_OPERATIONS_RECORD ||--o{ FRONT_DESK_OPERATIONS_AUDIT_LOG : "audits"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|--------------------|
| 1 | FRONT_DESK_OPERATIONS_RECORD | Hồ sơ Front Desk | Bản ghi nghiệp vụ chính của Front Desk Operations System | record_id PK, guest_id FK, service_code, status, created_at | contains FRONT_DESK_OPERATIONS_DETAIL |
| 2 | FRONT_DESK_OPERATIONS_DETAIL | Chi tiết Front Desk | Chi tiết từng hạng mục dịch vụ | detail_id PK, record_id FK, item_name, quantity, unit_price | belongs to FRONT_DESK_OPERATIONS_RECORD |
| 3 | FRONT_DESK_OPERATIONS_CATALOG | Danh mục dịch vụ | Danh mục bảng giá và cấu hình | catalog_id PK, category_name, base_price, is_active | applies to FRONT_DESK_OPERATIONS_DETAIL |
| 4 | FRONT_DESK_OPERATIONS_TRANSACTION | Giao dịch tài chính | Lịch sử thanh toán dịch vụ | trans_id PK, record_id FK, payment_method, amount, trans_date | settles FRONT_DESK_OPERATIONS_RECORD |
| 5 | FRONT_DESK_OPERATIONS_STAFF_ASSIGNMENT | Phân công nhân sự | Lịch phân công thực hiện công việc | assignment_id PK, record_id FK, staff_id, assigned_time, completion_time | tracks FRONT_DESK_OPERATIONS_RECORD |
| 6 | FRONT_DESK_OPERATIONS_AUDIT_LOG | Nhật ký kiểm toán | Lưu vết thao tác người dùng | log_id PK, record_id FK, user_id, action_type, timestamp | audits FRONT_DESK_OPERATIONS_RECORD |
| 7 | FRONT_DESK_OPERATIONS_FEEDBACK | Đánh giá dịch vụ | Phản hồi của khách hàng | feedback_id PK, record_id FK, rating_score, comment, created_at | evaluates FRONT_DESK_OPERATIONS_RECORD |
| 8 | FRONT_DESK_OPERATIONS_CONFIG | Cấu hình hệ thống | Tham số quy tắc vận hành | config_id PK, param_key, param_value, description | configures System |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | FRONT_DESK_OPERATIONS_RECORD | one-to-many | FRONT_DESK_OPERATIONS_DETAIL | contains | Một hồ sơ nghiệp vụ chứa nhiều hạng mục chi tiết |
| 2 | FRONT_DESK_OPERATIONS_RECORD | one-to-many | FRONT_DESK_OPERATIONS_TRANSACTION | settles | Một hồ sơ nghiệp vụ có thể thanh toán qua nhiều lần giao dịch |
| 3 | FRONT_DESK_OPERATIONS_CATALOG | one-to-many | FRONT_DESK_OPERATIONS_DETAIL | applies to | Danh mục áp dụng đơn giá cho chi tiết dịch vụ |
| 4 | FRONT_DESK_OPERATIONS_RECORD | one-to-many | FRONT_DESK_OPERATIONS_STAFF_ASSIGNMENT | tracks | Hồ sơ ghi nhận các đợt phân công nhân viên xử lý |
| 5 | FRONT_DESK_OPERATIONS_RECORD | one-to-many | FRONT_DESK_OPERATIONS_AUDIT_LOG | audits | Nhật ký lưu trữ tất cả thao tác biến động của hồ sơ |
