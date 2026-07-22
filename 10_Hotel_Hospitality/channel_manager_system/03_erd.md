# Conceptual ERD — Channel Manager System (Hotel)

## Mermaid Code

```mermaid
erDiagram
    CHANNEL_MANAGER_RECORD {
        record_id PK
        guest_id FK
        service_code
        status
        created_at
    }
    CHANNEL_MANAGER_DETAIL {
        detail_id PK
        record_id FK
        item_name
        quantity
        unit_price
    }
    CHANNEL_MANAGER_CATALOG {
        catalog_id PK
        category_name
        base_price
        is_active
    }
    CHANNEL_MANAGER_TRANSACTION {
        trans_id PK
        record_id FK
        payment_method
        amount
        trans_date
    }
    CHANNEL_MANAGER_STAFF_ASSIGNMENT {
        assignment_id PK
        record_id FK
        staff_id
        assigned_time
        completion_time
    }
    CHANNEL_MANAGER_AUDIT_LOG {
        log_id PK
        record_id FK
        user_id
        action_type
        timestamp
    }
    CHANNEL_MANAGER_FEEDBACK {
        feedback_id PK
        record_id FK
        rating_score
        comment
        created_at
    }
    CHANNEL_MANAGER_CONFIG {
        config_id PK
        param_key
        param_value
        description
    }

    CHANNEL_MANAGER_RECORD ||--o{ CHANNEL_MANAGER_DETAIL : "contains"
    CHANNEL_MANAGER_RECORD ||--o{ CHANNEL_MANAGER_TRANSACTION : "settles"
    CHANNEL_MANAGER_CATALOG ||--o{ CHANNEL_MANAGER_DETAIL : "applies to"
    CHANNEL_MANAGER_RECORD ||--o{ CHANNEL_MANAGER_STAFF_ASSIGNMENT : "tracks"
    CHANNEL_MANAGER_RECORD ||--o{ CHANNEL_MANAGER_AUDIT_LOG : "audits"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|--------------------|
| 1 | CHANNEL_MANAGER_RECORD | Hồ sơ Distribution | Bản ghi nghiệp vụ chính của Channel Manager System (Hotel) | record_id PK, guest_id FK, service_code, status, created_at | contains CHANNEL_MANAGER_DETAIL |
| 2 | CHANNEL_MANAGER_DETAIL | Chi tiết Distribution | Chi tiết từng hạng mục dịch vụ | detail_id PK, record_id FK, item_name, quantity, unit_price | belongs to CHANNEL_MANAGER_RECORD |
| 3 | CHANNEL_MANAGER_CATALOG | Danh mục dịch vụ | Danh mục bảng giá và cấu hình | catalog_id PK, category_name, base_price, is_active | applies to CHANNEL_MANAGER_DETAIL |
| 4 | CHANNEL_MANAGER_TRANSACTION | Giao dịch tài chính | Lịch sử thanh toán dịch vụ | trans_id PK, record_id FK, payment_method, amount, trans_date | settles CHANNEL_MANAGER_RECORD |
| 5 | CHANNEL_MANAGER_STAFF_ASSIGNMENT | Phân công nhân sự | Lịch phân công thực hiện công việc | assignment_id PK, record_id FK, staff_id, assigned_time, completion_time | tracks CHANNEL_MANAGER_RECORD |
| 6 | CHANNEL_MANAGER_AUDIT_LOG | Nhật ký kiểm toán | Lưu vết thao tác người dùng | log_id PK, record_id FK, user_id, action_type, timestamp | audits CHANNEL_MANAGER_RECORD |
| 7 | CHANNEL_MANAGER_FEEDBACK | Đánh giá dịch vụ | Phản hồi của khách hàng | feedback_id PK, record_id FK, rating_score, comment, created_at | evaluates CHANNEL_MANAGER_RECORD |
| 8 | CHANNEL_MANAGER_CONFIG | Cấu hình hệ thống | Tham số quy tắc vận hành | config_id PK, param_key, param_value, description | configures System |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | CHANNEL_MANAGER_RECORD | one-to-many | CHANNEL_MANAGER_DETAIL | contains | Một hồ sơ nghiệp vụ chứa nhiều hạng mục chi tiết |
| 2 | CHANNEL_MANAGER_RECORD | one-to-many | CHANNEL_MANAGER_TRANSACTION | settles | Một hồ sơ nghiệp vụ có thể thanh toán qua nhiều lần giao dịch |
| 3 | CHANNEL_MANAGER_CATALOG | one-to-many | CHANNEL_MANAGER_DETAIL | applies to | Danh mục áp dụng đơn giá cho chi tiết dịch vụ |
| 4 | CHANNEL_MANAGER_RECORD | one-to-many | CHANNEL_MANAGER_STAFF_ASSIGNMENT | tracks | Hồ sơ ghi nhận các đợt phân công nhân viên xử lý |
| 5 | CHANNEL_MANAGER_RECORD | one-to-many | CHANNEL_MANAGER_AUDIT_LOG | audits | Nhật ký lưu trữ tất cả thao tác biến động của hồ sơ |
