# Conceptual ERD — Hostel Management System

## Mermaid Code

```mermaid
erDiagram
    HOSTEL_RECORD {
        record_id PK
        guest_id FK
        service_code
        status
        created_at
    }
    HOSTEL_DETAIL {
        detail_id PK
        record_id FK
        item_name
        quantity
        unit_price
    }
    HOSTEL_CATALOG {
        catalog_id PK
        category_name
        base_price
        is_active
    }
    HOSTEL_TRANSACTION {
        trans_id PK
        record_id FK
        payment_method
        amount
        trans_date
    }
    HOSTEL_STAFF_ASSIGNMENT {
        assignment_id PK
        record_id FK
        staff_id
        assigned_time
        completion_time
    }
    HOSTEL_AUDIT_LOG {
        log_id PK
        record_id FK
        user_id
        action_type
        timestamp
    }
    HOSTEL_FEEDBACK {
        feedback_id PK
        record_id FK
        rating_score
        comment
        created_at
    }
    HOSTEL_CONFIG {
        config_id PK
        param_key
        param_value
        description
    }

    HOSTEL_RECORD ||--o{ HOSTEL_DETAIL : "contains"
    HOSTEL_RECORD ||--o{ HOSTEL_TRANSACTION : "settles"
    HOSTEL_CATALOG ||--o{ HOSTEL_DETAIL : "applies to"
    HOSTEL_RECORD ||--o{ HOSTEL_STAFF_ASSIGNMENT : "tracks"
    HOSTEL_RECORD ||--o{ HOSTEL_AUDIT_LOG : "audits"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|--------------------|
| 1 | HOSTEL_RECORD | Hồ sơ Hostel | Bản ghi nghiệp vụ chính của Hostel Management System | record_id PK, guest_id FK, service_code, status, created_at | contains HOSTEL_DETAIL |
| 2 | HOSTEL_DETAIL | Chi tiết Hostel | Chi tiết từng hạng mục dịch vụ | detail_id PK, record_id FK, item_name, quantity, unit_price | belongs to HOSTEL_RECORD |
| 3 | HOSTEL_CATALOG | Danh mục dịch vụ | Danh mục bảng giá và cấu hình | catalog_id PK, category_name, base_price, is_active | applies to HOSTEL_DETAIL |
| 4 | HOSTEL_TRANSACTION | Giao dịch tài chính | Lịch sử thanh toán dịch vụ | trans_id PK, record_id FK, payment_method, amount, trans_date | settles HOSTEL_RECORD |
| 5 | HOSTEL_STAFF_ASSIGNMENT | Phân công nhân sự | Lịch phân công thực hiện công việc | assignment_id PK, record_id FK, staff_id, assigned_time, completion_time | tracks HOSTEL_RECORD |
| 6 | HOSTEL_AUDIT_LOG | Nhật ký kiểm toán | Lưu vết thao tác người dùng | log_id PK, record_id FK, user_id, action_type, timestamp | audits HOSTEL_RECORD |
| 7 | HOSTEL_FEEDBACK | Đánh giá dịch vụ | Phản hồi của khách hàng | feedback_id PK, record_id FK, rating_score, comment, created_at | evaluates HOSTEL_RECORD |
| 8 | HOSTEL_CONFIG | Cấu hình hệ thống | Tham số quy tắc vận hành | config_id PK, param_key, param_value, description | configures System |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | HOSTEL_RECORD | one-to-many | HOSTEL_DETAIL | contains | Một hồ sơ nghiệp vụ chứa nhiều hạng mục chi tiết |
| 2 | HOSTEL_RECORD | one-to-many | HOSTEL_TRANSACTION | settles | Một hồ sơ nghiệp vụ có thể thanh toán qua nhiều lần giao dịch |
| 3 | HOSTEL_CATALOG | one-to-many | HOSTEL_DETAIL | applies to | Danh mục áp dụng đơn giá cho chi tiết dịch vụ |
| 4 | HOSTEL_RECORD | one-to-many | HOSTEL_STAFF_ASSIGNMENT | tracks | Hồ sơ ghi nhận các đợt phân công nhân viên xử lý |
| 5 | HOSTEL_RECORD | one-to-many | HOSTEL_AUDIT_LOG | audits | Nhật ký lưu trữ tất cả thao tác biến động của hồ sơ |
