# Conceptual ERD — Vacation Rental Management System

## Mermaid Code

```mermaid
erDiagram
    VACATION_RENTAL_RECORD {
        record_id PK
        guest_id FK
        service_code
        status
        created_at
    }
    VACATION_RENTAL_DETAIL {
        detail_id PK
        record_id FK
        item_name
        quantity
        unit_price
    }
    VACATION_RENTAL_CATALOG {
        catalog_id PK
        category_name
        base_price
        is_active
    }
    VACATION_RENTAL_TRANSACTION {
        trans_id PK
        record_id FK
        payment_method
        amount
        trans_date
    }
    VACATION_RENTAL_STAFF_ASSIGNMENT {
        assignment_id PK
        record_id FK
        staff_id
        assigned_time
        completion_time
    }
    VACATION_RENTAL_AUDIT_LOG {
        log_id PK
        record_id FK
        user_id
        action_type
        timestamp
    }
    VACATION_RENTAL_FEEDBACK {
        feedback_id PK
        record_id FK
        rating_score
        comment
        created_at
    }
    VACATION_RENTAL_CONFIG {
        config_id PK
        param_key
        param_value
        description
    }

    VACATION_RENTAL_RECORD ||--o{ VACATION_RENTAL_DETAIL : "contains"
    VACATION_RENTAL_RECORD ||--o{ VACATION_RENTAL_TRANSACTION : "settles"
    VACATION_RENTAL_CATALOG ||--o{ VACATION_RENTAL_DETAIL : "applies to"
    VACATION_RENTAL_RECORD ||--o{ VACATION_RENTAL_STAFF_ASSIGNMENT : "tracks"
    VACATION_RENTAL_RECORD ||--o{ VACATION_RENTAL_AUDIT_LOG : "audits"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|--------------------|
| 1 | VACATION_RENTAL_RECORD | Hồ sơ Vacation Rental | Bản ghi nghiệp vụ chính của Vacation Rental Management System | record_id PK, guest_id FK, service_code, status, created_at | contains VACATION_RENTAL_DETAIL |
| 2 | VACATION_RENTAL_DETAIL | Chi tiết Vacation Rental | Chi tiết từng hạng mục dịch vụ | detail_id PK, record_id FK, item_name, quantity, unit_price | belongs to VACATION_RENTAL_RECORD |
| 3 | VACATION_RENTAL_CATALOG | Danh mục dịch vụ | Danh mục bảng giá và cấu hình | catalog_id PK, category_name, base_price, is_active | applies to VACATION_RENTAL_DETAIL |
| 4 | VACATION_RENTAL_TRANSACTION | Giao dịch tài chính | Lịch sử thanh toán dịch vụ | trans_id PK, record_id FK, payment_method, amount, trans_date | settles VACATION_RENTAL_RECORD |
| 5 | VACATION_RENTAL_STAFF_ASSIGNMENT | Phân công nhân sự | Lịch phân công thực hiện công việc | assignment_id PK, record_id FK, staff_id, assigned_time, completion_time | tracks VACATION_RENTAL_RECORD |
| 6 | VACATION_RENTAL_AUDIT_LOG | Nhật ký kiểm toán | Lưu vết thao tác người dùng | log_id PK, record_id FK, user_id, action_type, timestamp | audits VACATION_RENTAL_RECORD |
| 7 | VACATION_RENTAL_FEEDBACK | Đánh giá dịch vụ | Phản hồi của khách hàng | feedback_id PK, record_id FK, rating_score, comment, created_at | evaluates VACATION_RENTAL_RECORD |
| 8 | VACATION_RENTAL_CONFIG | Cấu hình hệ thống | Tham số quy tắc vận hành | config_id PK, param_key, param_value, description | configures System |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | VACATION_RENTAL_RECORD | one-to-many | VACATION_RENTAL_DETAIL | contains | Một hồ sơ nghiệp vụ chứa nhiều hạng mục chi tiết |
| 2 | VACATION_RENTAL_RECORD | one-to-many | VACATION_RENTAL_TRANSACTION | settles | Một hồ sơ nghiệp vụ có thể thanh toán qua nhiều lần giao dịch |
| 3 | VACATION_RENTAL_CATALOG | one-to-many | VACATION_RENTAL_DETAIL | applies to | Danh mục áp dụng đơn giá cho chi tiết dịch vụ |
| 4 | VACATION_RENTAL_RECORD | one-to-many | VACATION_RENTAL_STAFF_ASSIGNMENT | tracks | Hồ sơ ghi nhận các đợt phân công nhân viên xử lý |
| 5 | VACATION_RENTAL_RECORD | one-to-many | VACATION_RENTAL_AUDIT_LOG | audits | Nhật ký lưu trữ tất cả thao tác biến động của hồ sơ |
