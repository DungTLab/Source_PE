# Conceptual ERD — Hospitality Training & Certification System

## Mermaid Code

```mermaid
erDiagram
    HOSPITALITY_TRAINING_CERTIFICATION_RECORD {
        record_id PK
        guest_id FK
        service_code
        status
        created_at
    }
    HOSPITALITY_TRAINING_CERTIFICATION_DETAIL {
        detail_id PK
        record_id FK
        item_name
        quantity
        unit_price
    }
    HOSPITALITY_TRAINING_CERTIFICATION_CATALOG {
        catalog_id PK
        category_name
        base_price
        is_active
    }
    HOSPITALITY_TRAINING_CERTIFICATION_TRANSACTION {
        trans_id PK
        record_id FK
        payment_method
        amount
        trans_date
    }
    HOSPITALITY_TRAINING_CERTIFICATION_STAFF_ASSIGNMENT {
        assignment_id PK
        record_id FK
        staff_id
        assigned_time
        completion_time
    }
    HOSPITALITY_TRAINING_CERTIFICATION_AUDIT_LOG {
        log_id PK
        record_id FK
        user_id
        action_type
        timestamp
    }
    HOSPITALITY_TRAINING_CERTIFICATION_FEEDBACK {
        feedback_id PK
        record_id FK
        rating_score
        comment
        created_at
    }
    HOSPITALITY_TRAINING_CERTIFICATION_CONFIG {
        config_id PK
        param_key
        param_value
        description
    }

    HOSPITALITY_TRAINING_CERTIFICATION_RECORD ||--o{ HOSPITALITY_TRAINING_CERTIFICATION_DETAIL : "contains"
    HOSPITALITY_TRAINING_CERTIFICATION_RECORD ||--o{ HOSPITALITY_TRAINING_CERTIFICATION_TRANSACTION : "settles"
    HOSPITALITY_TRAINING_CERTIFICATION_CATALOG ||--o{ HOSPITALITY_TRAINING_CERTIFICATION_DETAIL : "applies to"
    HOSPITALITY_TRAINING_CERTIFICATION_RECORD ||--o{ HOSPITALITY_TRAINING_CERTIFICATION_STAFF_ASSIGNMENT : "tracks"
    HOSPITALITY_TRAINING_CERTIFICATION_RECORD ||--o{ HOSPITALITY_TRAINING_CERTIFICATION_AUDIT_LOG : "audits"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|--------------------|
| 1 | HOSPITALITY_TRAINING_CERTIFICATION_RECORD | Hồ sơ Certification | Bản ghi nghiệp vụ chính của Hospitality Training & Certification System | record_id PK, guest_id FK, service_code, status, created_at | contains HOSPITALITY_TRAINING_CERTIFICATION_DETAIL |
| 2 | HOSPITALITY_TRAINING_CERTIFICATION_DETAIL | Chi tiết Certification | Chi tiết từng hạng mục dịch vụ | detail_id PK, record_id FK, item_name, quantity, unit_price | belongs to HOSPITALITY_TRAINING_CERTIFICATION_RECORD |
| 3 | HOSPITALITY_TRAINING_CERTIFICATION_CATALOG | Danh mục dịch vụ | Danh mục bảng giá và cấu hình | catalog_id PK, category_name, base_price, is_active | applies to HOSPITALITY_TRAINING_CERTIFICATION_DETAIL |
| 4 | HOSPITALITY_TRAINING_CERTIFICATION_TRANSACTION | Giao dịch tài chính | Lịch sử thanh toán dịch vụ | trans_id PK, record_id FK, payment_method, amount, trans_date | settles HOSPITALITY_TRAINING_CERTIFICATION_RECORD |
| 5 | HOSPITALITY_TRAINING_CERTIFICATION_STAFF_ASSIGNMENT | Phân công nhân sự | Lịch phân công thực hiện công việc | assignment_id PK, record_id FK, staff_id, assigned_time, completion_time | tracks HOSPITALITY_TRAINING_CERTIFICATION_RECORD |
| 6 | HOSPITALITY_TRAINING_CERTIFICATION_AUDIT_LOG | Nhật ký kiểm toán | Lưu vết thao tác người dùng | log_id PK, record_id FK, user_id, action_type, timestamp | audits HOSPITALITY_TRAINING_CERTIFICATION_RECORD |
| 7 | HOSPITALITY_TRAINING_CERTIFICATION_FEEDBACK | Đánh giá dịch vụ | Phản hồi của khách hàng | feedback_id PK, record_id FK, rating_score, comment, created_at | evaluates HOSPITALITY_TRAINING_CERTIFICATION_RECORD |
| 8 | HOSPITALITY_TRAINING_CERTIFICATION_CONFIG | Cấu hình hệ thống | Tham số quy tắc vận hành | config_id PK, param_key, param_value, description | configures System |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | HOSPITALITY_TRAINING_CERTIFICATION_RECORD | one-to-many | HOSPITALITY_TRAINING_CERTIFICATION_DETAIL | contains | Một hồ sơ nghiệp vụ chứa nhiều hạng mục chi tiết |
| 2 | HOSPITALITY_TRAINING_CERTIFICATION_RECORD | one-to-many | HOSPITALITY_TRAINING_CERTIFICATION_TRANSACTION | settles | Một hồ sơ nghiệp vụ có thể thanh toán qua nhiều lần giao dịch |
| 3 | HOSPITALITY_TRAINING_CERTIFICATION_CATALOG | one-to-many | HOSPITALITY_TRAINING_CERTIFICATION_DETAIL | applies to | Danh mục áp dụng đơn giá cho chi tiết dịch vụ |
| 4 | HOSPITALITY_TRAINING_CERTIFICATION_RECORD | one-to-many | HOSPITALITY_TRAINING_CERTIFICATION_STAFF_ASSIGNMENT | tracks | Hồ sơ ghi nhận các đợt phân công nhân viên xử lý |
| 5 | HOSPITALITY_TRAINING_CERTIFICATION_RECORD | one-to-many | HOSPITALITY_TRAINING_CERTIFICATION_AUDIT_LOG | audits | Nhật ký lưu trữ tất cả thao tác biến động của hồ sơ |
