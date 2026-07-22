# Conceptual ERD — Boutique Hotel Management System

## Mermaid Code

```mermaid
erDiagram
    BOUTIQUE_HOTEL_RECORD {
        record_id PK
        guest_id FK
        service_code
        status
        created_at
    }
    BOUTIQUE_HOTEL_DETAIL {
        detail_id PK
        record_id FK
        item_name
        quantity
        unit_price
    }
    BOUTIQUE_HOTEL_CATALOG {
        catalog_id PK
        category_name
        base_price
        is_active
    }
    BOUTIQUE_HOTEL_TRANSACTION {
        trans_id PK
        record_id FK
        payment_method
        amount
        trans_date
    }
    BOUTIQUE_HOTEL_STAFF_ASSIGNMENT {
        assignment_id PK
        record_id FK
        staff_id
        assigned_time
        completion_time
    }
    BOUTIQUE_HOTEL_AUDIT_LOG {
        log_id PK
        record_id FK
        user_id
        action_type
        timestamp
    }
    BOUTIQUE_HOTEL_FEEDBACK {
        feedback_id PK
        record_id FK
        rating_score
        comment
        created_at
    }
    BOUTIQUE_HOTEL_CONFIG {
        config_id PK
        param_key
        param_value
        description
    }

    BOUTIQUE_HOTEL_RECORD ||--o{ BOUTIQUE_HOTEL_DETAIL : "contains"
    BOUTIQUE_HOTEL_RECORD ||--o{ BOUTIQUE_HOTEL_TRANSACTION : "settles"
    BOUTIQUE_HOTEL_CATALOG ||--o{ BOUTIQUE_HOTEL_DETAIL : "applies to"
    BOUTIQUE_HOTEL_RECORD ||--o{ BOUTIQUE_HOTEL_STAFF_ASSIGNMENT : "tracks"
    BOUTIQUE_HOTEL_RECORD ||--o{ BOUTIQUE_HOTEL_AUDIT_LOG : "audits"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|--------------------|
| 1 | BOUTIQUE_HOTEL_RECORD | Hồ sơ Boutique | Bản ghi nghiệp vụ chính của Boutique Hotel Management System | record_id PK, guest_id FK, service_code, status, created_at | contains BOUTIQUE_HOTEL_DETAIL |
| 2 | BOUTIQUE_HOTEL_DETAIL | Chi tiết Boutique | Chi tiết từng hạng mục dịch vụ | detail_id PK, record_id FK, item_name, quantity, unit_price | belongs to BOUTIQUE_HOTEL_RECORD |
| 3 | BOUTIQUE_HOTEL_CATALOG | Danh mục dịch vụ | Danh mục bảng giá và cấu hình | catalog_id PK, category_name, base_price, is_active | applies to BOUTIQUE_HOTEL_DETAIL |
| 4 | BOUTIQUE_HOTEL_TRANSACTION | Giao dịch tài chính | Lịch sử thanh toán dịch vụ | trans_id PK, record_id FK, payment_method, amount, trans_date | settles BOUTIQUE_HOTEL_RECORD |
| 5 | BOUTIQUE_HOTEL_STAFF_ASSIGNMENT | Phân công nhân sự | Lịch phân công thực hiện công việc | assignment_id PK, record_id FK, staff_id, assigned_time, completion_time | tracks BOUTIQUE_HOTEL_RECORD |
| 6 | BOUTIQUE_HOTEL_AUDIT_LOG | Nhật ký kiểm toán | Lưu vết thao tác người dùng | log_id PK, record_id FK, user_id, action_type, timestamp | audits BOUTIQUE_HOTEL_RECORD |
| 7 | BOUTIQUE_HOTEL_FEEDBACK | Đánh giá dịch vụ | Phản hồi của khách hàng | feedback_id PK, record_id FK, rating_score, comment, created_at | evaluates BOUTIQUE_HOTEL_RECORD |
| 8 | BOUTIQUE_HOTEL_CONFIG | Cấu hình hệ thống | Tham số quy tắc vận hành | config_id PK, param_key, param_value, description | configures System |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | BOUTIQUE_HOTEL_RECORD | one-to-many | BOUTIQUE_HOTEL_DETAIL | contains | Một hồ sơ nghiệp vụ chứa nhiều hạng mục chi tiết |
| 2 | BOUTIQUE_HOTEL_RECORD | one-to-many | BOUTIQUE_HOTEL_TRANSACTION | settles | Một hồ sơ nghiệp vụ có thể thanh toán qua nhiều lần giao dịch |
| 3 | BOUTIQUE_HOTEL_CATALOG | one-to-many | BOUTIQUE_HOTEL_DETAIL | applies to | Danh mục áp dụng đơn giá cho chi tiết dịch vụ |
| 4 | BOUTIQUE_HOTEL_RECORD | one-to-many | BOUTIQUE_HOTEL_STAFF_ASSIGNMENT | tracks | Hồ sơ ghi nhận các đợt phân công nhân viên xử lý |
| 5 | BOUTIQUE_HOTEL_RECORD | one-to-many | BOUTIQUE_HOTEL_AUDIT_LOG | audits | Nhật ký lưu trữ tất cả thao tác biến động của hồ sơ |
