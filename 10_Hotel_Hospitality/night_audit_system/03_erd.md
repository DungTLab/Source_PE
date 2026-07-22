# Conceptual ERD — Night Audit System (Hotel)

## Mermaid Code

```mermaid
erDiagram
    NIGHT_AUDIT_RECORD {
        record_id PK
        guest_id FK
        service_code
        status
        created_at
    }
    NIGHT_AUDIT_DETAIL {
        detail_id PK
        record_id FK
        item_name
        quantity
        unit_price
    }
    NIGHT_AUDIT_CATALOG {
        catalog_id PK
        category_name
        base_price
        is_active
    }
    NIGHT_AUDIT_TRANSACTION {
        trans_id PK
        record_id FK
        payment_method
        amount
        trans_date
    }
    NIGHT_AUDIT_STAFF_ASSIGNMENT {
        assignment_id PK
        record_id FK
        staff_id
        assigned_time
        completion_time
    }
    NIGHT_AUDIT_AUDIT_LOG {
        log_id PK
        record_id FK
        user_id
        action_type
        timestamp
    }
    NIGHT_AUDIT_FEEDBACK {
        feedback_id PK
        record_id FK
        rating_score
        comment
        created_at
    }
    NIGHT_AUDIT_CONFIG {
        config_id PK
        param_key
        param_value
        description
    }

    NIGHT_AUDIT_RECORD ||--o{ NIGHT_AUDIT_DETAIL : "contains"
    NIGHT_AUDIT_RECORD ||--o{ NIGHT_AUDIT_TRANSACTION : "settles"
    NIGHT_AUDIT_CATALOG ||--o{ NIGHT_AUDIT_DETAIL : "applies to"
    NIGHT_AUDIT_RECORD ||--o{ NIGHT_AUDIT_STAFF_ASSIGNMENT : "tracks"
    NIGHT_AUDIT_RECORD ||--o{ NIGHT_AUDIT_AUDIT_LOG : "audits"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|--------------------|
| 1 | NIGHT_AUDIT_RECORD | Hồ sơ Audit | Bản ghi nghiệp vụ chính của Night Audit System (Hotel) | record_id PK, guest_id FK, service_code, status, created_at | contains NIGHT_AUDIT_DETAIL |
| 2 | NIGHT_AUDIT_DETAIL | Chi tiết Audit | Chi tiết từng hạng mục dịch vụ | detail_id PK, record_id FK, item_name, quantity, unit_price | belongs to NIGHT_AUDIT_RECORD |
| 3 | NIGHT_AUDIT_CATALOG | Danh mục dịch vụ | Danh mục bảng giá và cấu hình | catalog_id PK, category_name, base_price, is_active | applies to NIGHT_AUDIT_DETAIL |
| 4 | NIGHT_AUDIT_TRANSACTION | Giao dịch tài chính | Lịch sử thanh toán dịch vụ | trans_id PK, record_id FK, payment_method, amount, trans_date | settles NIGHT_AUDIT_RECORD |
| 5 | NIGHT_AUDIT_STAFF_ASSIGNMENT | Phân công nhân sự | Lịch phân công thực hiện công việc | assignment_id PK, record_id FK, staff_id, assigned_time, completion_time | tracks NIGHT_AUDIT_RECORD |
| 6 | NIGHT_AUDIT_AUDIT_LOG | Nhật ký kiểm toán | Lưu vết thao tác người dùng | log_id PK, record_id FK, user_id, action_type, timestamp | audits NIGHT_AUDIT_RECORD |
| 7 | NIGHT_AUDIT_FEEDBACK | Đánh giá dịch vụ | Phản hồi của khách hàng | feedback_id PK, record_id FK, rating_score, comment, created_at | evaluates NIGHT_AUDIT_RECORD |
| 8 | NIGHT_AUDIT_CONFIG | Cấu hình hệ thống | Tham số quy tắc vận hành | config_id PK, param_key, param_value, description | configures System |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | NIGHT_AUDIT_RECORD | one-to-many | NIGHT_AUDIT_DETAIL | contains | Một hồ sơ nghiệp vụ chứa nhiều hạng mục chi tiết |
| 2 | NIGHT_AUDIT_RECORD | one-to-many | NIGHT_AUDIT_TRANSACTION | settles | Một hồ sơ nghiệp vụ có thể thanh toán qua nhiều lần giao dịch |
| 3 | NIGHT_AUDIT_CATALOG | one-to-many | NIGHT_AUDIT_DETAIL | applies to | Danh mục áp dụng đơn giá cho chi tiết dịch vụ |
| 4 | NIGHT_AUDIT_RECORD | one-to-many | NIGHT_AUDIT_STAFF_ASSIGNMENT | tracks | Hồ sơ ghi nhận các đợt phân công nhân viên xử lý |
| 5 | NIGHT_AUDIT_RECORD | one-to-many | NIGHT_AUDIT_AUDIT_LOG | audits | Nhật ký lưu trữ tất cả thao tác biến động của hồ sơ |
