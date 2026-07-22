# Conceptual ERD — Hotel Staff Training Management System

## Mermaid Code

```mermaid
erDiagram
    HOTEL_STAFF_TRAINING_RECORD {
        record_id PK
        guest_id FK
        service_code
        status
        created_at
    }
    HOTEL_STAFF_TRAINING_DETAIL {
        detail_id PK
        record_id FK
        item_name
        quantity
        unit_price
    }
    HOTEL_STAFF_TRAINING_CATALOG {
        catalog_id PK
        category_name
        base_price
        is_active
    }
    HOTEL_STAFF_TRAINING_TRANSACTION {
        trans_id PK
        record_id FK
        payment_method
        amount
        trans_date
    }
    HOTEL_STAFF_TRAINING_STAFF_ASSIGNMENT {
        assignment_id PK
        record_id FK
        staff_id
        assigned_time
        completion_time
    }
    HOTEL_STAFF_TRAINING_AUDIT_LOG {
        log_id PK
        record_id FK
        user_id
        action_type
        timestamp
    }
    HOTEL_STAFF_TRAINING_FEEDBACK {
        feedback_id PK
        record_id FK
        rating_score
        comment
        created_at
    }
    HOTEL_STAFF_TRAINING_CONFIG {
        config_id PK
        param_key
        param_value
        description
    }

    HOTEL_STAFF_TRAINING_RECORD ||--o{ HOTEL_STAFF_TRAINING_DETAIL : "contains"
    HOTEL_STAFF_TRAINING_RECORD ||--o{ HOTEL_STAFF_TRAINING_TRANSACTION : "settles"
    HOTEL_STAFF_TRAINING_CATALOG ||--o{ HOTEL_STAFF_TRAINING_DETAIL : "applies to"
    HOTEL_STAFF_TRAINING_RECORD ||--o{ HOTEL_STAFF_TRAINING_STAFF_ASSIGNMENT : "tracks"
    HOTEL_STAFF_TRAINING_RECORD ||--o{ HOTEL_STAFF_TRAINING_AUDIT_LOG : "audits"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|--------------------|
| 1 | HOTEL_STAFF_TRAINING_RECORD | Hồ sơ HR & Training | Bản ghi nghiệp vụ chính của Hotel Staff Training Management System | record_id PK, guest_id FK, service_code, status, created_at | contains HOTEL_STAFF_TRAINING_DETAIL |
| 2 | HOTEL_STAFF_TRAINING_DETAIL | Chi tiết HR & Training | Chi tiết từng hạng mục dịch vụ | detail_id PK, record_id FK, item_name, quantity, unit_price | belongs to HOTEL_STAFF_TRAINING_RECORD |
| 3 | HOTEL_STAFF_TRAINING_CATALOG | Danh mục dịch vụ | Danh mục bảng giá và cấu hình | catalog_id PK, category_name, base_price, is_active | applies to HOTEL_STAFF_TRAINING_DETAIL |
| 4 | HOTEL_STAFF_TRAINING_TRANSACTION | Giao dịch tài chính | Lịch sử thanh toán dịch vụ | trans_id PK, record_id FK, payment_method, amount, trans_date | settles HOTEL_STAFF_TRAINING_RECORD |
| 5 | HOTEL_STAFF_TRAINING_STAFF_ASSIGNMENT | Phân công nhân sự | Lịch phân công thực hiện công việc | assignment_id PK, record_id FK, staff_id, assigned_time, completion_time | tracks HOTEL_STAFF_TRAINING_RECORD |
| 6 | HOTEL_STAFF_TRAINING_AUDIT_LOG | Nhật ký kiểm toán | Lưu vết thao tác người dùng | log_id PK, record_id FK, user_id, action_type, timestamp | audits HOTEL_STAFF_TRAINING_RECORD |
| 7 | HOTEL_STAFF_TRAINING_FEEDBACK | Đánh giá dịch vụ | Phản hồi của khách hàng | feedback_id PK, record_id FK, rating_score, comment, created_at | evaluates HOTEL_STAFF_TRAINING_RECORD |
| 8 | HOTEL_STAFF_TRAINING_CONFIG | Cấu hình hệ thống | Tham số quy tắc vận hành | config_id PK, param_key, param_value, description | configures System |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | HOTEL_STAFF_TRAINING_RECORD | one-to-many | HOTEL_STAFF_TRAINING_DETAIL | contains | Một hồ sơ nghiệp vụ chứa nhiều hạng mục chi tiết |
| 2 | HOTEL_STAFF_TRAINING_RECORD | one-to-many | HOTEL_STAFF_TRAINING_TRANSACTION | settles | Một hồ sơ nghiệp vụ có thể thanh toán qua nhiều lần giao dịch |
| 3 | HOTEL_STAFF_TRAINING_CATALOG | one-to-many | HOTEL_STAFF_TRAINING_DETAIL | applies to | Danh mục áp dụng đơn giá cho chi tiết dịch vụ |
| 4 | HOTEL_STAFF_TRAINING_RECORD | one-to-many | HOTEL_STAFF_TRAINING_STAFF_ASSIGNMENT | tracks | Hồ sơ ghi nhận các đợt phân công nhân viên xử lý |
| 5 | HOTEL_STAFF_TRAINING_RECORD | one-to-many | HOTEL_STAFF_TRAINING_AUDIT_LOG | audits | Nhật ký lưu trữ tất cả thao tác biến động của hồ sơ |
