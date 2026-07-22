# Conceptual ERD — Motel & Budget Accommodation System

## Mermaid Code

```mermaid
erDiagram
    MOTEL_BUDGET_ACCOMMODATION_RECORD {
        record_id PK
        guest_id FK
        service_code
        status
        created_at
    }
    MOTEL_BUDGET_ACCOMMODATION_DETAIL {
        detail_id PK
        record_id FK
        item_name
        quantity
        unit_price
    }
    MOTEL_BUDGET_ACCOMMODATION_CATALOG {
        catalog_id PK
        category_name
        base_price
        is_active
    }
    MOTEL_BUDGET_ACCOMMODATION_TRANSACTION {
        trans_id PK
        record_id FK
        payment_method
        amount
        trans_date
    }
    MOTEL_BUDGET_ACCOMMODATION_STAFF_ASSIGNMENT {
        assignment_id PK
        record_id FK
        staff_id
        assigned_time
        completion_time
    }
    MOTEL_BUDGET_ACCOMMODATION_AUDIT_LOG {
        log_id PK
        record_id FK
        user_id
        action_type
        timestamp
    }
    MOTEL_BUDGET_ACCOMMODATION_FEEDBACK {
        feedback_id PK
        record_id FK
        rating_score
        comment
        created_at
    }
    MOTEL_BUDGET_ACCOMMODATION_CONFIG {
        config_id PK
        param_key
        param_value
        description
    }

    MOTEL_BUDGET_ACCOMMODATION_RECORD ||--o{ MOTEL_BUDGET_ACCOMMODATION_DETAIL : "contains"
    MOTEL_BUDGET_ACCOMMODATION_RECORD ||--o{ MOTEL_BUDGET_ACCOMMODATION_TRANSACTION : "settles"
    MOTEL_BUDGET_ACCOMMODATION_CATALOG ||--o{ MOTEL_BUDGET_ACCOMMODATION_DETAIL : "applies to"
    MOTEL_BUDGET_ACCOMMODATION_RECORD ||--o{ MOTEL_BUDGET_ACCOMMODATION_STAFF_ASSIGNMENT : "tracks"
    MOTEL_BUDGET_ACCOMMODATION_RECORD ||--o{ MOTEL_BUDGET_ACCOMMODATION_AUDIT_LOG : "audits"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|--------------------|
| 1 | MOTEL_BUDGET_ACCOMMODATION_RECORD | Hồ sơ Budget | Bản ghi nghiệp vụ chính của Motel & Budget Accommodation System | record_id PK, guest_id FK, service_code, status, created_at | contains MOTEL_BUDGET_ACCOMMODATION_DETAIL |
| 2 | MOTEL_BUDGET_ACCOMMODATION_DETAIL | Chi tiết Budget | Chi tiết từng hạng mục dịch vụ | detail_id PK, record_id FK, item_name, quantity, unit_price | belongs to MOTEL_BUDGET_ACCOMMODATION_RECORD |
| 3 | MOTEL_BUDGET_ACCOMMODATION_CATALOG | Danh mục dịch vụ | Danh mục bảng giá và cấu hình | catalog_id PK, category_name, base_price, is_active | applies to MOTEL_BUDGET_ACCOMMODATION_DETAIL |
| 4 | MOTEL_BUDGET_ACCOMMODATION_TRANSACTION | Giao dịch tài chính | Lịch sử thanh toán dịch vụ | trans_id PK, record_id FK, payment_method, amount, trans_date | settles MOTEL_BUDGET_ACCOMMODATION_RECORD |
| 5 | MOTEL_BUDGET_ACCOMMODATION_STAFF_ASSIGNMENT | Phân công nhân sự | Lịch phân công thực hiện công việc | assignment_id PK, record_id FK, staff_id, assigned_time, completion_time | tracks MOTEL_BUDGET_ACCOMMODATION_RECORD |
| 6 | MOTEL_BUDGET_ACCOMMODATION_AUDIT_LOG | Nhật ký kiểm toán | Lưu vết thao tác người dùng | log_id PK, record_id FK, user_id, action_type, timestamp | audits MOTEL_BUDGET_ACCOMMODATION_RECORD |
| 7 | MOTEL_BUDGET_ACCOMMODATION_FEEDBACK | Đánh giá dịch vụ | Phản hồi của khách hàng | feedback_id PK, record_id FK, rating_score, comment, created_at | evaluates MOTEL_BUDGET_ACCOMMODATION_RECORD |
| 8 | MOTEL_BUDGET_ACCOMMODATION_CONFIG | Cấu hình hệ thống | Tham số quy tắc vận hành | config_id PK, param_key, param_value, description | configures System |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | MOTEL_BUDGET_ACCOMMODATION_RECORD | one-to-many | MOTEL_BUDGET_ACCOMMODATION_DETAIL | contains | Một hồ sơ nghiệp vụ chứa nhiều hạng mục chi tiết |
| 2 | MOTEL_BUDGET_ACCOMMODATION_RECORD | one-to-many | MOTEL_BUDGET_ACCOMMODATION_TRANSACTION | settles | Một hồ sơ nghiệp vụ có thể thanh toán qua nhiều lần giao dịch |
| 3 | MOTEL_BUDGET_ACCOMMODATION_CATALOG | one-to-many | MOTEL_BUDGET_ACCOMMODATION_DETAIL | applies to | Danh mục áp dụng đơn giá cho chi tiết dịch vụ |
| 4 | MOTEL_BUDGET_ACCOMMODATION_RECORD | one-to-many | MOTEL_BUDGET_ACCOMMODATION_STAFF_ASSIGNMENT | tracks | Hồ sơ ghi nhận các đợt phân công nhân viên xử lý |
| 5 | MOTEL_BUDGET_ACCOMMODATION_RECORD | one-to-many | MOTEL_BUDGET_ACCOMMODATION_AUDIT_LOG | audits | Nhật ký lưu trữ tất cả thao tác biến động của hồ sơ |
