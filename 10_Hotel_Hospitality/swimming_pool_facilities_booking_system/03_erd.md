# Conceptual ERD — Swimming Pool & Facilities Booking System

## Mermaid Code

```mermaid
erDiagram
    SWIMMING_POOL_FACILITIES_BOOKING_RECORD {
        record_id PK
        guest_id FK
        service_code
        status
        created_at
    }
    SWIMMING_POOL_FACILITIES_BOOKING_DETAIL {
        detail_id PK
        record_id FK
        item_name
        quantity
        unit_price
    }
    SWIMMING_POOL_FACILITIES_BOOKING_CATALOG {
        catalog_id PK
        category_name
        base_price
        is_active
    }
    SWIMMING_POOL_FACILITIES_BOOKING_TRANSACTION {
        trans_id PK
        record_id FK
        payment_method
        amount
        trans_date
    }
    SWIMMING_POOL_FACILITIES_BOOKING_STAFF_ASSIGNMENT {
        assignment_id PK
        record_id FK
        staff_id
        assigned_time
        completion_time
    }
    SWIMMING_POOL_FACILITIES_BOOKING_AUDIT_LOG {
        log_id PK
        record_id FK
        user_id
        action_type
        timestamp
    }
    SWIMMING_POOL_FACILITIES_BOOKING_FEEDBACK {
        feedback_id PK
        record_id FK
        rating_score
        comment
        created_at
    }
    SWIMMING_POOL_FACILITIES_BOOKING_CONFIG {
        config_id PK
        param_key
        param_value
        description
    }

    SWIMMING_POOL_FACILITIES_BOOKING_RECORD ||--o{ SWIMMING_POOL_FACILITIES_BOOKING_DETAIL : "contains"
    SWIMMING_POOL_FACILITIES_BOOKING_RECORD ||--o{ SWIMMING_POOL_FACILITIES_BOOKING_TRANSACTION : "settles"
    SWIMMING_POOL_FACILITIES_BOOKING_CATALOG ||--o{ SWIMMING_POOL_FACILITIES_BOOKING_DETAIL : "applies to"
    SWIMMING_POOL_FACILITIES_BOOKING_RECORD ||--o{ SWIMMING_POOL_FACILITIES_BOOKING_STAFF_ASSIGNMENT : "tracks"
    SWIMMING_POOL_FACILITIES_BOOKING_RECORD ||--o{ SWIMMING_POOL_FACILITIES_BOOKING_AUDIT_LOG : "audits"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|--------------------|
| 1 | SWIMMING_POOL_FACILITIES_BOOKING_RECORD | Hồ sơ Facilities | Bản ghi nghiệp vụ chính của Swimming Pool & Facilities Booking System | record_id PK, guest_id FK, service_code, status, created_at | contains SWIMMING_POOL_FACILITIES_BOOKING_DETAIL |
| 2 | SWIMMING_POOL_FACILITIES_BOOKING_DETAIL | Chi tiết Facilities | Chi tiết từng hạng mục dịch vụ | detail_id PK, record_id FK, item_name, quantity, unit_price | belongs to SWIMMING_POOL_FACILITIES_BOOKING_RECORD |
| 3 | SWIMMING_POOL_FACILITIES_BOOKING_CATALOG | Danh mục dịch vụ | Danh mục bảng giá và cấu hình | catalog_id PK, category_name, base_price, is_active | applies to SWIMMING_POOL_FACILITIES_BOOKING_DETAIL |
| 4 | SWIMMING_POOL_FACILITIES_BOOKING_TRANSACTION | Giao dịch tài chính | Lịch sử thanh toán dịch vụ | trans_id PK, record_id FK, payment_method, amount, trans_date | settles SWIMMING_POOL_FACILITIES_BOOKING_RECORD |
| 5 | SWIMMING_POOL_FACILITIES_BOOKING_STAFF_ASSIGNMENT | Phân công nhân sự | Lịch phân công thực hiện công việc | assignment_id PK, record_id FK, staff_id, assigned_time, completion_time | tracks SWIMMING_POOL_FACILITIES_BOOKING_RECORD |
| 6 | SWIMMING_POOL_FACILITIES_BOOKING_AUDIT_LOG | Nhật ký kiểm toán | Lưu vết thao tác người dùng | log_id PK, record_id FK, user_id, action_type, timestamp | audits SWIMMING_POOL_FACILITIES_BOOKING_RECORD |
| 7 | SWIMMING_POOL_FACILITIES_BOOKING_FEEDBACK | Đánh giá dịch vụ | Phản hồi của khách hàng | feedback_id PK, record_id FK, rating_score, comment, created_at | evaluates SWIMMING_POOL_FACILITIES_BOOKING_RECORD |
| 8 | SWIMMING_POOL_FACILITIES_BOOKING_CONFIG | Cấu hình hệ thống | Tham số quy tắc vận hành | config_id PK, param_key, param_value, description | configures System |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | SWIMMING_POOL_FACILITIES_BOOKING_RECORD | one-to-many | SWIMMING_POOL_FACILITIES_BOOKING_DETAIL | contains | Một hồ sơ nghiệp vụ chứa nhiều hạng mục chi tiết |
| 2 | SWIMMING_POOL_FACILITIES_BOOKING_RECORD | one-to-many | SWIMMING_POOL_FACILITIES_BOOKING_TRANSACTION | settles | Một hồ sơ nghiệp vụ có thể thanh toán qua nhiều lần giao dịch |
| 3 | SWIMMING_POOL_FACILITIES_BOOKING_CATALOG | one-to-many | SWIMMING_POOL_FACILITIES_BOOKING_DETAIL | applies to | Danh mục áp dụng đơn giá cho chi tiết dịch vụ |
| 4 | SWIMMING_POOL_FACILITIES_BOOKING_RECORD | one-to-many | SWIMMING_POOL_FACILITIES_BOOKING_STAFF_ASSIGNMENT | tracks | Hồ sơ ghi nhận các đợt phân công nhân viên xử lý |
| 5 | SWIMMING_POOL_FACILITIES_BOOKING_RECORD | one-to-many | SWIMMING_POOL_FACILITIES_BOOKING_AUDIT_LOG | audits | Nhật ký lưu trữ tất cả thao tác biến động của hồ sơ |
