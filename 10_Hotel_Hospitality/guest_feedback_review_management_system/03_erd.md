# Conceptual ERD — Guest Feedback & Review Management System

## Mermaid Code

```mermaid
erDiagram
    GUEST_FEEDBACK_REVIEW_RECORD {
        record_id PK
        guest_id FK
        service_code
        status
        created_at
    }
    GUEST_FEEDBACK_REVIEW_DETAIL {
        detail_id PK
        record_id FK
        item_name
        quantity
        unit_price
    }
    GUEST_FEEDBACK_REVIEW_CATALOG {
        catalog_id PK
        category_name
        base_price
        is_active
    }
    GUEST_FEEDBACK_REVIEW_TRANSACTION {
        trans_id PK
        record_id FK
        payment_method
        amount
        trans_date
    }
    GUEST_FEEDBACK_REVIEW_STAFF_ASSIGNMENT {
        assignment_id PK
        record_id FK
        staff_id
        assigned_time
        completion_time
    }
    GUEST_FEEDBACK_REVIEW_AUDIT_LOG {
        log_id PK
        record_id FK
        user_id
        action_type
        timestamp
    }
    GUEST_FEEDBACK_REVIEW_FEEDBACK {
        feedback_id PK
        record_id FK
        rating_score
        comment
        created_at
    }
    GUEST_FEEDBACK_REVIEW_CONFIG {
        config_id PK
        param_key
        param_value
        description
    }

    GUEST_FEEDBACK_REVIEW_RECORD ||--o{ GUEST_FEEDBACK_REVIEW_DETAIL : "contains"
    GUEST_FEEDBACK_REVIEW_RECORD ||--o{ GUEST_FEEDBACK_REVIEW_TRANSACTION : "settles"
    GUEST_FEEDBACK_REVIEW_CATALOG ||--o{ GUEST_FEEDBACK_REVIEW_DETAIL : "applies to"
    GUEST_FEEDBACK_REVIEW_RECORD ||--o{ GUEST_FEEDBACK_REVIEW_STAFF_ASSIGNMENT : "tracks"
    GUEST_FEEDBACK_REVIEW_RECORD ||--o{ GUEST_FEEDBACK_REVIEW_AUDIT_LOG : "audits"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|--------------------|
| 1 | GUEST_FEEDBACK_REVIEW_RECORD | Hồ sơ Feedback | Bản ghi nghiệp vụ chính của Guest Feedback & Review Management System | record_id PK, guest_id FK, service_code, status, created_at | contains GUEST_FEEDBACK_REVIEW_DETAIL |
| 2 | GUEST_FEEDBACK_REVIEW_DETAIL | Chi tiết Feedback | Chi tiết từng hạng mục dịch vụ | detail_id PK, record_id FK, item_name, quantity, unit_price | belongs to GUEST_FEEDBACK_REVIEW_RECORD |
| 3 | GUEST_FEEDBACK_REVIEW_CATALOG | Danh mục dịch vụ | Danh mục bảng giá và cấu hình | catalog_id PK, category_name, base_price, is_active | applies to GUEST_FEEDBACK_REVIEW_DETAIL |
| 4 | GUEST_FEEDBACK_REVIEW_TRANSACTION | Giao dịch tài chính | Lịch sử thanh toán dịch vụ | trans_id PK, record_id FK, payment_method, amount, trans_date | settles GUEST_FEEDBACK_REVIEW_RECORD |
| 5 | GUEST_FEEDBACK_REVIEW_STAFF_ASSIGNMENT | Phân công nhân sự | Lịch phân công thực hiện công việc | assignment_id PK, record_id FK, staff_id, assigned_time, completion_time | tracks GUEST_FEEDBACK_REVIEW_RECORD |
| 6 | GUEST_FEEDBACK_REVIEW_AUDIT_LOG | Nhật ký kiểm toán | Lưu vết thao tác người dùng | log_id PK, record_id FK, user_id, action_type, timestamp | audits GUEST_FEEDBACK_REVIEW_RECORD |
| 7 | GUEST_FEEDBACK_REVIEW_FEEDBACK | Đánh giá dịch vụ | Phản hồi của khách hàng | feedback_id PK, record_id FK, rating_score, comment, created_at | evaluates GUEST_FEEDBACK_REVIEW_RECORD |
| 8 | GUEST_FEEDBACK_REVIEW_CONFIG | Cấu hình hệ thống | Tham số quy tắc vận hành | config_id PK, param_key, param_value, description | configures System |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | GUEST_FEEDBACK_REVIEW_RECORD | one-to-many | GUEST_FEEDBACK_REVIEW_DETAIL | contains | Một hồ sơ nghiệp vụ chứa nhiều hạng mục chi tiết |
| 2 | GUEST_FEEDBACK_REVIEW_RECORD | one-to-many | GUEST_FEEDBACK_REVIEW_TRANSACTION | settles | Một hồ sơ nghiệp vụ có thể thanh toán qua nhiều lần giao dịch |
| 3 | GUEST_FEEDBACK_REVIEW_CATALOG | one-to-many | GUEST_FEEDBACK_REVIEW_DETAIL | applies to | Danh mục áp dụng đơn giá cho chi tiết dịch vụ |
| 4 | GUEST_FEEDBACK_REVIEW_RECORD | one-to-many | GUEST_FEEDBACK_REVIEW_STAFF_ASSIGNMENT | tracks | Hồ sơ ghi nhận các đợt phân công nhân viên xử lý |
| 5 | GUEST_FEEDBACK_REVIEW_RECORD | one-to-many | GUEST_FEEDBACK_REVIEW_AUDIT_LOG | audits | Nhật ký lưu trữ tất cả thao tác biến động của hồ sơ |
