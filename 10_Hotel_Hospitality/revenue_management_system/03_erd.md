# Conceptual ERD — Revenue Management System (Hotel)

## Mermaid Code

```mermaid
erDiagram
    REVENUE_RECORD {
        record_id PK
        guest_id FK
        service_code
        status
        created_at
    }
    REVENUE_DETAIL {
        detail_id PK
        record_id FK
        item_name
        quantity
        unit_price
    }
    REVENUE_CATALOG {
        catalog_id PK
        category_name
        base_price
        is_active
    }
    REVENUE_TRANSACTION {
        trans_id PK
        record_id FK
        payment_method
        amount
        trans_date
    }
    REVENUE_STAFF_ASSIGNMENT {
        assignment_id PK
        record_id FK
        staff_id
        assigned_time
        completion_time
    }
    REVENUE_AUDIT_LOG {
        log_id PK
        record_id FK
        user_id
        action_type
        timestamp
    }
    REVENUE_FEEDBACK {
        feedback_id PK
        record_id FK
        rating_score
        comment
        created_at
    }
    REVENUE_CONFIG {
        config_id PK
        param_key
        param_value
        description
    }

    REVENUE_RECORD ||--o{ REVENUE_DETAIL : "contains"
    REVENUE_RECORD ||--o{ REVENUE_TRANSACTION : "settles"
    REVENUE_CATALOG ||--o{ REVENUE_DETAIL : "applies to"
    REVENUE_RECORD ||--o{ REVENUE_STAFF_ASSIGNMENT : "tracks"
    REVENUE_RECORD ||--o{ REVENUE_AUDIT_LOG : "audits"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|--------------------|
| 1 | REVENUE_RECORD | Hồ sơ Revenue | Bản ghi nghiệp vụ chính của Revenue Management System (Hotel) | record_id PK, guest_id FK, service_code, status, created_at | contains REVENUE_DETAIL |
| 2 | REVENUE_DETAIL | Chi tiết Revenue | Chi tiết từng hạng mục dịch vụ | detail_id PK, record_id FK, item_name, quantity, unit_price | belongs to REVENUE_RECORD |
| 3 | REVENUE_CATALOG | Danh mục dịch vụ | Danh mục bảng giá và cấu hình | catalog_id PK, category_name, base_price, is_active | applies to REVENUE_DETAIL |
| 4 | REVENUE_TRANSACTION | Giao dịch tài chính | Lịch sử thanh toán dịch vụ | trans_id PK, record_id FK, payment_method, amount, trans_date | settles REVENUE_RECORD |
| 5 | REVENUE_STAFF_ASSIGNMENT | Phân công nhân sự | Lịch phân công thực hiện công việc | assignment_id PK, record_id FK, staff_id, assigned_time, completion_time | tracks REVENUE_RECORD |
| 6 | REVENUE_AUDIT_LOG | Nhật ký kiểm toán | Lưu vết thao tác người dùng | log_id PK, record_id FK, user_id, action_type, timestamp | audits REVENUE_RECORD |
| 7 | REVENUE_FEEDBACK | Đánh giá dịch vụ | Phản hồi của khách hàng | feedback_id PK, record_id FK, rating_score, comment, created_at | evaluates REVENUE_RECORD |
| 8 | REVENUE_CONFIG | Cấu hình hệ thống | Tham số quy tắc vận hành | config_id PK, param_key, param_value, description | configures System |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | REVENUE_RECORD | one-to-many | REVENUE_DETAIL | contains | Một hồ sơ nghiệp vụ chứa nhiều hạng mục chi tiết |
| 2 | REVENUE_RECORD | one-to-many | REVENUE_TRANSACTION | settles | Một hồ sơ nghiệp vụ có thể thanh toán qua nhiều lần giao dịch |
| 3 | REVENUE_CATALOG | one-to-many | REVENUE_DETAIL | applies to | Danh mục áp dụng đơn giá cho chi tiết dịch vụ |
| 4 | REVENUE_RECORD | one-to-many | REVENUE_STAFF_ASSIGNMENT | tracks | Hồ sơ ghi nhận các đợt phân công nhân viên xử lý |
| 5 | REVENUE_RECORD | one-to-many | REVENUE_AUDIT_LOG | audits | Nhật ký lưu trữ tất cả thao tác biến động của hồ sơ |
