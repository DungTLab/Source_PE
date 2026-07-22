# Conceptual ERD — Spa & Wellness Center Management System

## Mermaid Code

```mermaid
erDiagram
    SPA_WELLNESS_CENTER_RECORD {
        record_id PK
        guest_id FK
        service_code
        status
        created_at
    }
    SPA_WELLNESS_CENTER_DETAIL {
        detail_id PK
        record_id FK
        item_name
        quantity
        unit_price
    }
    SPA_WELLNESS_CENTER_CATALOG {
        catalog_id PK
        category_name
        base_price
        is_active
    }
    SPA_WELLNESS_CENTER_TRANSACTION {
        trans_id PK
        record_id FK
        payment_method
        amount
        trans_date
    }
    SPA_WELLNESS_CENTER_STAFF_ASSIGNMENT {
        assignment_id PK
        record_id FK
        staff_id
        assigned_time
        completion_time
    }
    SPA_WELLNESS_CENTER_AUDIT_LOG {
        log_id PK
        record_id FK
        user_id
        action_type
        timestamp
    }
    SPA_WELLNESS_CENTER_FEEDBACK {
        feedback_id PK
        record_id FK
        rating_score
        comment
        created_at
    }
    SPA_WELLNESS_CENTER_CONFIG {
        config_id PK
        param_key
        param_value
        description
    }

    SPA_WELLNESS_CENTER_RECORD ||--o{ SPA_WELLNESS_CENTER_DETAIL : "contains"
    SPA_WELLNESS_CENTER_RECORD ||--o{ SPA_WELLNESS_CENTER_TRANSACTION : "settles"
    SPA_WELLNESS_CENTER_CATALOG ||--o{ SPA_WELLNESS_CENTER_DETAIL : "applies to"
    SPA_WELLNESS_CENTER_RECORD ||--o{ SPA_WELLNESS_CENTER_STAFF_ASSIGNMENT : "tracks"
    SPA_WELLNESS_CENTER_RECORD ||--o{ SPA_WELLNESS_CENTER_AUDIT_LOG : "audits"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|--------------------|
| 1 | SPA_WELLNESS_CENTER_RECORD | Hồ sơ Wellness | Bản ghi nghiệp vụ chính của Spa & Wellness Center Management System | record_id PK, guest_id FK, service_code, status, created_at | contains SPA_WELLNESS_CENTER_DETAIL |
| 2 | SPA_WELLNESS_CENTER_DETAIL | Chi tiết Wellness | Chi tiết từng hạng mục dịch vụ | detail_id PK, record_id FK, item_name, quantity, unit_price | belongs to SPA_WELLNESS_CENTER_RECORD |
| 3 | SPA_WELLNESS_CENTER_CATALOG | Danh mục dịch vụ | Danh mục bảng giá và cấu hình | catalog_id PK, category_name, base_price, is_active | applies to SPA_WELLNESS_CENTER_DETAIL |
| 4 | SPA_WELLNESS_CENTER_TRANSACTION | Giao dịch tài chính | Lịch sử thanh toán dịch vụ | trans_id PK, record_id FK, payment_method, amount, trans_date | settles SPA_WELLNESS_CENTER_RECORD |
| 5 | SPA_WELLNESS_CENTER_STAFF_ASSIGNMENT | Phân công nhân sự | Lịch phân công thực hiện công việc | assignment_id PK, record_id FK, staff_id, assigned_time, completion_time | tracks SPA_WELLNESS_CENTER_RECORD |
| 6 | SPA_WELLNESS_CENTER_AUDIT_LOG | Nhật ký kiểm toán | Lưu vết thao tác người dùng | log_id PK, record_id FK, user_id, action_type, timestamp | audits SPA_WELLNESS_CENTER_RECORD |
| 7 | SPA_WELLNESS_CENTER_FEEDBACK | Đánh giá dịch vụ | Phản hồi của khách hàng | feedback_id PK, record_id FK, rating_score, comment, created_at | evaluates SPA_WELLNESS_CENTER_RECORD |
| 8 | SPA_WELLNESS_CENTER_CONFIG | Cấu hình hệ thống | Tham số quy tắc vận hành | config_id PK, param_key, param_value, description | configures System |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | SPA_WELLNESS_CENTER_RECORD | one-to-many | SPA_WELLNESS_CENTER_DETAIL | contains | Một hồ sơ nghiệp vụ chứa nhiều hạng mục chi tiết |
| 2 | SPA_WELLNESS_CENTER_RECORD | one-to-many | SPA_WELLNESS_CENTER_TRANSACTION | settles | Một hồ sơ nghiệp vụ có thể thanh toán qua nhiều lần giao dịch |
| 3 | SPA_WELLNESS_CENTER_CATALOG | one-to-many | SPA_WELLNESS_CENTER_DETAIL | applies to | Danh mục áp dụng đơn giá cho chi tiết dịch vụ |
| 4 | SPA_WELLNESS_CENTER_RECORD | one-to-many | SPA_WELLNESS_CENTER_STAFF_ASSIGNMENT | tracks | Hồ sơ ghi nhận các đợt phân công nhân viên xử lý |
| 5 | SPA_WELLNESS_CENTER_RECORD | one-to-many | SPA_WELLNESS_CENTER_AUDIT_LOG | audits | Nhật ký lưu trữ tất cả thao tác biến động của hồ sơ |
