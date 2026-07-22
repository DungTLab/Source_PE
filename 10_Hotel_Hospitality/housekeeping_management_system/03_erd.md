# Conceptual ERD — Housekeeping Management System

## Mermaid Code

```mermaid
erDiagram
    HOUSEKEEPING_RECORD {
        record_id PK
        guest_id FK
        service_code
        status
        created_at
    }
    HOUSEKEEPING_DETAIL {
        detail_id PK
        record_id FK
        item_name
        quantity
        unit_price
    }
    HOUSEKEEPING_CATALOG {
        catalog_id PK
        category_name
        base_price
        is_active
    }
    HOUSEKEEPING_TRANSACTION {
        trans_id PK
        record_id FK
        payment_method
        amount
        trans_date
    }
    HOUSEKEEPING_STAFF_ASSIGNMENT {
        assignment_id PK
        record_id FK
        staff_id
        assigned_time
        completion_time
    }
    HOUSEKEEPING_AUDIT_LOG {
        log_id PK
        record_id FK
        user_id
        action_type
        timestamp
    }
    HOUSEKEEPING_FEEDBACK {
        feedback_id PK
        record_id FK
        rating_score
        comment
        created_at
    }
    HOUSEKEEPING_CONFIG {
        config_id PK
        param_key
        param_value
        description
    }

    HOUSEKEEPING_RECORD ||--o{ HOUSEKEEPING_DETAIL : "contains"
    HOUSEKEEPING_RECORD ||--o{ HOUSEKEEPING_TRANSACTION : "settles"
    HOUSEKEEPING_CATALOG ||--o{ HOUSEKEEPING_DETAIL : "applies to"
    HOUSEKEEPING_RECORD ||--o{ HOUSEKEEPING_STAFF_ASSIGNMENT : "tracks"
    HOUSEKEEPING_RECORD ||--o{ HOUSEKEEPING_AUDIT_LOG : "audits"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|--------------------|
| 1 | HOUSEKEEPING_RECORD | Hồ sơ Housekeeping | Bản ghi nghiệp vụ chính của Housekeeping Management System | record_id PK, guest_id FK, service_code, status, created_at | contains HOUSEKEEPING_DETAIL |
| 2 | HOUSEKEEPING_DETAIL | Chi tiết Housekeeping | Chi tiết từng hạng mục dịch vụ | detail_id PK, record_id FK, item_name, quantity, unit_price | belongs to HOUSEKEEPING_RECORD |
| 3 | HOUSEKEEPING_CATALOG | Danh mục dịch vụ | Danh mục bảng giá và cấu hình | catalog_id PK, category_name, base_price, is_active | applies to HOUSEKEEPING_DETAIL |
| 4 | HOUSEKEEPING_TRANSACTION | Giao dịch tài chính | Lịch sử thanh toán dịch vụ | trans_id PK, record_id FK, payment_method, amount, trans_date | settles HOUSEKEEPING_RECORD |
| 5 | HOUSEKEEPING_STAFF_ASSIGNMENT | Phân công nhân sự | Lịch phân công thực hiện công việc | assignment_id PK, record_id FK, staff_id, assigned_time, completion_time | tracks HOUSEKEEPING_RECORD |
| 6 | HOUSEKEEPING_AUDIT_LOG | Nhật ký kiểm toán | Lưu vết thao tác người dùng | log_id PK, record_id FK, user_id, action_type, timestamp | audits HOUSEKEEPING_RECORD |
| 7 | HOUSEKEEPING_FEEDBACK | Đánh giá dịch vụ | Phản hồi của khách hàng | feedback_id PK, record_id FK, rating_score, comment, created_at | evaluates HOUSEKEEPING_RECORD |
| 8 | HOUSEKEEPING_CONFIG | Cấu hình hệ thống | Tham số quy tắc vận hành | config_id PK, param_key, param_value, description | configures System |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | HOUSEKEEPING_RECORD | one-to-many | HOUSEKEEPING_DETAIL | contains | Một hồ sơ nghiệp vụ chứa nhiều hạng mục chi tiết |
| 2 | HOUSEKEEPING_RECORD | one-to-many | HOUSEKEEPING_TRANSACTION | settles | Một hồ sơ nghiệp vụ có thể thanh toán qua nhiều lần giao dịch |
| 3 | HOUSEKEEPING_CATALOG | one-to-many | HOUSEKEEPING_DETAIL | applies to | Danh mục áp dụng đơn giá cho chi tiết dịch vụ |
| 4 | HOUSEKEEPING_RECORD | one-to-many | HOUSEKEEPING_STAFF_ASSIGNMENT | tracks | Hồ sơ ghi nhận các đợt phân công nhân viên xử lý |
| 5 | HOUSEKEEPING_RECORD | one-to-many | HOUSEKEEPING_AUDIT_LOG | audits | Nhật ký lưu trữ tất cả thao tác biến động của hồ sơ |
