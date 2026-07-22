# Conceptual ERD — Hotel Sustainability Tracking System

## Mermaid Code

```mermaid
erDiagram
    HOTEL_SUSTAINABILITY_TRACKING_RECORD {
        record_id PK
        guest_id FK
        service_code
        status
        created_at
    }
    HOTEL_SUSTAINABILITY_TRACKING_DETAIL {
        detail_id PK
        record_id FK
        item_name
        quantity
        unit_price
    }
    HOTEL_SUSTAINABILITY_TRACKING_CATALOG {
        catalog_id PK
        category_name
        base_price
        is_active
    }
    HOTEL_SUSTAINABILITY_TRACKING_TRANSACTION {
        trans_id PK
        record_id FK
        payment_method
        amount
        trans_date
    }
    HOTEL_SUSTAINABILITY_TRACKING_STAFF_ASSIGNMENT {
        assignment_id PK
        record_id FK
        staff_id
        assigned_time
        completion_time
    }
    HOTEL_SUSTAINABILITY_TRACKING_AUDIT_LOG {
        log_id PK
        record_id FK
        user_id
        action_type
        timestamp
    }
    HOTEL_SUSTAINABILITY_TRACKING_FEEDBACK {
        feedback_id PK
        record_id FK
        rating_score
        comment
        created_at
    }
    HOTEL_SUSTAINABILITY_TRACKING_CONFIG {
        config_id PK
        param_key
        param_value
        description
    }

    HOTEL_SUSTAINABILITY_TRACKING_RECORD ||--o{ HOTEL_SUSTAINABILITY_TRACKING_DETAIL : "contains"
    HOTEL_SUSTAINABILITY_TRACKING_RECORD ||--o{ HOTEL_SUSTAINABILITY_TRACKING_TRANSACTION : "settles"
    HOTEL_SUSTAINABILITY_TRACKING_CATALOG ||--o{ HOTEL_SUSTAINABILITY_TRACKING_DETAIL : "applies to"
    HOTEL_SUSTAINABILITY_TRACKING_RECORD ||--o{ HOTEL_SUSTAINABILITY_TRACKING_STAFF_ASSIGNMENT : "tracks"
    HOTEL_SUSTAINABILITY_TRACKING_RECORD ||--o{ HOTEL_SUSTAINABILITY_TRACKING_AUDIT_LOG : "audits"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|--------------------|
| 1 | HOTEL_SUSTAINABILITY_TRACKING_RECORD | Hồ sơ ESG | Bản ghi nghiệp vụ chính của Hotel Sustainability Tracking System | record_id PK, guest_id FK, service_code, status, created_at | contains HOTEL_SUSTAINABILITY_TRACKING_DETAIL |
| 2 | HOTEL_SUSTAINABILITY_TRACKING_DETAIL | Chi tiết ESG | Chi tiết từng hạng mục dịch vụ | detail_id PK, record_id FK, item_name, quantity, unit_price | belongs to HOTEL_SUSTAINABILITY_TRACKING_RECORD |
| 3 | HOTEL_SUSTAINABILITY_TRACKING_CATALOG | Danh mục dịch vụ | Danh mục bảng giá và cấu hình | catalog_id PK, category_name, base_price, is_active | applies to HOTEL_SUSTAINABILITY_TRACKING_DETAIL |
| 4 | HOTEL_SUSTAINABILITY_TRACKING_TRANSACTION | Giao dịch tài chính | Lịch sử thanh toán dịch vụ | trans_id PK, record_id FK, payment_method, amount, trans_date | settles HOTEL_SUSTAINABILITY_TRACKING_RECORD |
| 5 | HOTEL_SUSTAINABILITY_TRACKING_STAFF_ASSIGNMENT | Phân công nhân sự | Lịch phân công thực hiện công việc | assignment_id PK, record_id FK, staff_id, assigned_time, completion_time | tracks HOTEL_SUSTAINABILITY_TRACKING_RECORD |
| 6 | HOTEL_SUSTAINABILITY_TRACKING_AUDIT_LOG | Nhật ký kiểm toán | Lưu vết thao tác người dùng | log_id PK, record_id FK, user_id, action_type, timestamp | audits HOTEL_SUSTAINABILITY_TRACKING_RECORD |
| 7 | HOTEL_SUSTAINABILITY_TRACKING_FEEDBACK | Đánh giá dịch vụ | Phản hồi của khách hàng | feedback_id PK, record_id FK, rating_score, comment, created_at | evaluates HOTEL_SUSTAINABILITY_TRACKING_RECORD |
| 8 | HOTEL_SUSTAINABILITY_TRACKING_CONFIG | Cấu hình hệ thống | Tham số quy tắc vận hành | config_id PK, param_key, param_value, description | configures System |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | HOTEL_SUSTAINABILITY_TRACKING_RECORD | one-to-many | HOTEL_SUSTAINABILITY_TRACKING_DETAIL | contains | Một hồ sơ nghiệp vụ chứa nhiều hạng mục chi tiết |
| 2 | HOTEL_SUSTAINABILITY_TRACKING_RECORD | one-to-many | HOTEL_SUSTAINABILITY_TRACKING_TRANSACTION | settles | Một hồ sơ nghiệp vụ có thể thanh toán qua nhiều lần giao dịch |
| 3 | HOTEL_SUSTAINABILITY_TRACKING_CATALOG | one-to-many | HOTEL_SUSTAINABILITY_TRACKING_DETAIL | applies to | Danh mục áp dụng đơn giá cho chi tiết dịch vụ |
| 4 | HOTEL_SUSTAINABILITY_TRACKING_RECORD | one-to-many | HOTEL_SUSTAINABILITY_TRACKING_STAFF_ASSIGNMENT | tracks | Hồ sơ ghi nhận các đợt phân công nhân viên xử lý |
| 5 | HOTEL_SUSTAINABILITY_TRACKING_RECORD | one-to-many | HOTEL_SUSTAINABILITY_TRACKING_AUDIT_LOG | audits | Nhật ký lưu trữ tất cả thao tác biến động của hồ sơ |
