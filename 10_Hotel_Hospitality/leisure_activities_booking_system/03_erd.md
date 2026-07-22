# Conceptual ERD — Leisure & Activities Booking System

## Mermaid Code

```mermaid
erDiagram
    LEISURE_ACTIVITIES_BOOKING_RECORD {
        record_id PK
        guest_id FK
        service_code
        status
        created_at
    }
    LEISURE_ACTIVITIES_BOOKING_DETAIL {
        detail_id PK
        record_id FK
        item_name
        quantity
        unit_price
    }
    LEISURE_ACTIVITIES_BOOKING_CATALOG {
        catalog_id PK
        category_name
        base_price
        is_active
    }
    LEISURE_ACTIVITIES_BOOKING_TRANSACTION {
        trans_id PK
        record_id FK
        payment_method
        amount
        trans_date
    }
    LEISURE_ACTIVITIES_BOOKING_STAFF_ASSIGNMENT {
        assignment_id PK
        record_id FK
        staff_id
        assigned_time
        completion_time
    }
    LEISURE_ACTIVITIES_BOOKING_AUDIT_LOG {
        log_id PK
        record_id FK
        user_id
        action_type
        timestamp
    }
    LEISURE_ACTIVITIES_BOOKING_FEEDBACK {
        feedback_id PK
        record_id FK
        rating_score
        comment
        created_at
    }
    LEISURE_ACTIVITIES_BOOKING_CONFIG {
        config_id PK
        param_key
        param_value
        description
    }

    LEISURE_ACTIVITIES_BOOKING_RECORD ||--o{ LEISURE_ACTIVITIES_BOOKING_DETAIL : "contains"
    LEISURE_ACTIVITIES_BOOKING_RECORD ||--o{ LEISURE_ACTIVITIES_BOOKING_TRANSACTION : "settles"
    LEISURE_ACTIVITIES_BOOKING_CATALOG ||--o{ LEISURE_ACTIVITIES_BOOKING_DETAIL : "applies to"
    LEISURE_ACTIVITIES_BOOKING_RECORD ||--o{ LEISURE_ACTIVITIES_BOOKING_STAFF_ASSIGNMENT : "tracks"
    LEISURE_ACTIVITIES_BOOKING_RECORD ||--o{ LEISURE_ACTIVITIES_BOOKING_AUDIT_LOG : "audits"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|--------------------|
| 1 | LEISURE_ACTIVITIES_BOOKING_RECORD | Hồ sơ Recreation | Bản ghi nghiệp vụ chính của Leisure & Activities Booking System | record_id PK, guest_id FK, service_code, status, created_at | contains LEISURE_ACTIVITIES_BOOKING_DETAIL |
| 2 | LEISURE_ACTIVITIES_BOOKING_DETAIL | Chi tiết Recreation | Chi tiết từng hạng mục dịch vụ | detail_id PK, record_id FK, item_name, quantity, unit_price | belongs to LEISURE_ACTIVITIES_BOOKING_RECORD |
| 3 | LEISURE_ACTIVITIES_BOOKING_CATALOG | Danh mục dịch vụ | Danh mục bảng giá và cấu hình | catalog_id PK, category_name, base_price, is_active | applies to LEISURE_ACTIVITIES_BOOKING_DETAIL |
| 4 | LEISURE_ACTIVITIES_BOOKING_TRANSACTION | Giao dịch tài chính | Lịch sử thanh toán dịch vụ | trans_id PK, record_id FK, payment_method, amount, trans_date | settles LEISURE_ACTIVITIES_BOOKING_RECORD |
| 5 | LEISURE_ACTIVITIES_BOOKING_STAFF_ASSIGNMENT | Phân công nhân sự | Lịch phân công thực hiện công việc | assignment_id PK, record_id FK, staff_id, assigned_time, completion_time | tracks LEISURE_ACTIVITIES_BOOKING_RECORD |
| 6 | LEISURE_ACTIVITIES_BOOKING_AUDIT_LOG | Nhật ký kiểm toán | Lưu vết thao tác người dùng | log_id PK, record_id FK, user_id, action_type, timestamp | audits LEISURE_ACTIVITIES_BOOKING_RECORD |
| 7 | LEISURE_ACTIVITIES_BOOKING_FEEDBACK | Đánh giá dịch vụ | Phản hồi của khách hàng | feedback_id PK, record_id FK, rating_score, comment, created_at | evaluates LEISURE_ACTIVITIES_BOOKING_RECORD |
| 8 | LEISURE_ACTIVITIES_BOOKING_CONFIG | Cấu hình hệ thống | Tham số quy tắc vận hành | config_id PK, param_key, param_value, description | configures System |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | LEISURE_ACTIVITIES_BOOKING_RECORD | one-to-many | LEISURE_ACTIVITIES_BOOKING_DETAIL | contains | Một hồ sơ nghiệp vụ chứa nhiều hạng mục chi tiết |
| 2 | LEISURE_ACTIVITIES_BOOKING_RECORD | one-to-many | LEISURE_ACTIVITIES_BOOKING_TRANSACTION | settles | Một hồ sơ nghiệp vụ có thể thanh toán qua nhiều lần giao dịch |
| 3 | LEISURE_ACTIVITIES_BOOKING_CATALOG | one-to-many | LEISURE_ACTIVITIES_BOOKING_DETAIL | applies to | Danh mục áp dụng đơn giá cho chi tiết dịch vụ |
| 4 | LEISURE_ACTIVITIES_BOOKING_RECORD | one-to-many | LEISURE_ACTIVITIES_BOOKING_STAFF_ASSIGNMENT | tracks | Hồ sơ ghi nhận các đợt phân công nhân viên xử lý |
| 5 | LEISURE_ACTIVITIES_BOOKING_RECORD | one-to-many | LEISURE_ACTIVITIES_BOOKING_AUDIT_LOG | audits | Nhật ký lưu trữ tất cả thao tác biến động của hồ sơ |
