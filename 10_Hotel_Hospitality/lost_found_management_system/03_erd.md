# Conceptual ERD — Lost & Found Management System

## Mermaid Code

```mermaid
erDiagram
    LOST_FOUND_RECORD {
        record_id PK
        guest_id FK
        service_code
        status
        created_at
    }
    LOST_FOUND_DETAIL {
        detail_id PK
        record_id FK
        item_name
        quantity
        unit_price
    }
    LOST_FOUND_CATALOG {
        catalog_id PK
        category_name
        base_price
        is_active
    }
    LOST_FOUND_TRANSACTION {
        trans_id PK
        record_id FK
        payment_method
        amount
        trans_date
    }
    LOST_FOUND_STAFF_ASSIGNMENT {
        assignment_id PK
        record_id FK
        staff_id
        assigned_time
        completion_time
    }
    LOST_FOUND_AUDIT_LOG {
        log_id PK
        record_id FK
        user_id
        action_type
        timestamp
    }
    LOST_FOUND_FEEDBACK {
        feedback_id PK
        record_id FK
        rating_score
        comment
        created_at
    }
    LOST_FOUND_CONFIG {
        config_id PK
        param_key
        param_value
        description
    }

    LOST_FOUND_RECORD ||--o{ LOST_FOUND_DETAIL : "contains"
    LOST_FOUND_RECORD ||--o{ LOST_FOUND_TRANSACTION : "settles"
    LOST_FOUND_CATALOG ||--o{ LOST_FOUND_DETAIL : "applies to"
    LOST_FOUND_RECORD ||--o{ LOST_FOUND_STAFF_ASSIGNMENT : "tracks"
    LOST_FOUND_RECORD ||--o{ LOST_FOUND_AUDIT_LOG : "audits"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|--------------------|
| 1 | LOST_FOUND_RECORD | Hồ sơ Lost & Found | Bản ghi nghiệp vụ chính của Lost & Found Management System | record_id PK, guest_id FK, service_code, status, created_at | contains LOST_FOUND_DETAIL |
| 2 | LOST_FOUND_DETAIL | Chi tiết Lost & Found | Chi tiết từng hạng mục dịch vụ | detail_id PK, record_id FK, item_name, quantity, unit_price | belongs to LOST_FOUND_RECORD |
| 3 | LOST_FOUND_CATALOG | Danh mục dịch vụ | Danh mục bảng giá và cấu hình | catalog_id PK, category_name, base_price, is_active | applies to LOST_FOUND_DETAIL |
| 4 | LOST_FOUND_TRANSACTION | Giao dịch tài chính | Lịch sử thanh toán dịch vụ | trans_id PK, record_id FK, payment_method, amount, trans_date | settles LOST_FOUND_RECORD |
| 5 | LOST_FOUND_STAFF_ASSIGNMENT | Phân công nhân sự | Lịch phân công thực hiện công việc | assignment_id PK, record_id FK, staff_id, assigned_time, completion_time | tracks LOST_FOUND_RECORD |
| 6 | LOST_FOUND_AUDIT_LOG | Nhật ký kiểm toán | Lưu vết thao tác người dùng | log_id PK, record_id FK, user_id, action_type, timestamp | audits LOST_FOUND_RECORD |
| 7 | LOST_FOUND_FEEDBACK | Đánh giá dịch vụ | Phản hồi của khách hàng | feedback_id PK, record_id FK, rating_score, comment, created_at | evaluates LOST_FOUND_RECORD |
| 8 | LOST_FOUND_CONFIG | Cấu hình hệ thống | Tham số quy tắc vận hành | config_id PK, param_key, param_value, description | configures System |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | LOST_FOUND_RECORD | one-to-many | LOST_FOUND_DETAIL | contains | Một hồ sơ nghiệp vụ chứa nhiều hạng mục chi tiết |
| 2 | LOST_FOUND_RECORD | one-to-many | LOST_FOUND_TRANSACTION | settles | Một hồ sơ nghiệp vụ có thể thanh toán qua nhiều lần giao dịch |
| 3 | LOST_FOUND_CATALOG | one-to-many | LOST_FOUND_DETAIL | applies to | Danh mục áp dụng đơn giá cho chi tiết dịch vụ |
| 4 | LOST_FOUND_RECORD | one-to-many | LOST_FOUND_STAFF_ASSIGNMENT | tracks | Hồ sơ ghi nhận các đợt phân công nhân viên xử lý |
| 5 | LOST_FOUND_RECORD | one-to-many | LOST_FOUND_AUDIT_LOG | audits | Nhật ký lưu trữ tất cả thao tác biến động của hồ sơ |
