# Conceptual ERD — Corporate Travel & Rate Agreement System

## Mermaid Code

```mermaid
erDiagram
    CORPORATE_TRAVEL_RATE_AGREEMENT_RECORD {
        record_id PK
        guest_id FK
        service_code
        status
        created_at
    }
    CORPORATE_TRAVEL_RATE_AGREEMENT_DETAIL {
        detail_id PK
        record_id FK
        item_name
        quantity
        unit_price
    }
    CORPORATE_TRAVEL_RATE_AGREEMENT_CATALOG {
        catalog_id PK
        category_name
        base_price
        is_active
    }
    CORPORATE_TRAVEL_RATE_AGREEMENT_TRANSACTION {
        trans_id PK
        record_id FK
        payment_method
        amount
        trans_date
    }
    CORPORATE_TRAVEL_RATE_AGREEMENT_STAFF_ASSIGNMENT {
        assignment_id PK
        record_id FK
        staff_id
        assigned_time
        completion_time
    }
    CORPORATE_TRAVEL_RATE_AGREEMENT_AUDIT_LOG {
        log_id PK
        record_id FK
        user_id
        action_type
        timestamp
    }
    CORPORATE_TRAVEL_RATE_AGREEMENT_FEEDBACK {
        feedback_id PK
        record_id FK
        rating_score
        comment
        created_at
    }
    CORPORATE_TRAVEL_RATE_AGREEMENT_CONFIG {
        config_id PK
        param_key
        param_value
        description
    }

    CORPORATE_TRAVEL_RATE_AGREEMENT_RECORD ||--o{ CORPORATE_TRAVEL_RATE_AGREEMENT_DETAIL : "contains"
    CORPORATE_TRAVEL_RATE_AGREEMENT_RECORD ||--o{ CORPORATE_TRAVEL_RATE_AGREEMENT_TRANSACTION : "settles"
    CORPORATE_TRAVEL_RATE_AGREEMENT_CATALOG ||--o{ CORPORATE_TRAVEL_RATE_AGREEMENT_DETAIL : "applies to"
    CORPORATE_TRAVEL_RATE_AGREEMENT_RECORD ||--o{ CORPORATE_TRAVEL_RATE_AGREEMENT_STAFF_ASSIGNMENT : "tracks"
    CORPORATE_TRAVEL_RATE_AGREEMENT_RECORD ||--o{ CORPORATE_TRAVEL_RATE_AGREEMENT_AUDIT_LOG : "audits"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|--------------------|
| 1 | CORPORATE_TRAVEL_RATE_AGREEMENT_RECORD | Hồ sơ Corporate | Bản ghi nghiệp vụ chính của Corporate Travel & Rate Agreement System | record_id PK, guest_id FK, service_code, status, created_at | contains CORPORATE_TRAVEL_RATE_AGREEMENT_DETAIL |
| 2 | CORPORATE_TRAVEL_RATE_AGREEMENT_DETAIL | Chi tiết Corporate | Chi tiết từng hạng mục dịch vụ | detail_id PK, record_id FK, item_name, quantity, unit_price | belongs to CORPORATE_TRAVEL_RATE_AGREEMENT_RECORD |
| 3 | CORPORATE_TRAVEL_RATE_AGREEMENT_CATALOG | Danh mục dịch vụ | Danh mục bảng giá và cấu hình | catalog_id PK, category_name, base_price, is_active | applies to CORPORATE_TRAVEL_RATE_AGREEMENT_DETAIL |
| 4 | CORPORATE_TRAVEL_RATE_AGREEMENT_TRANSACTION | Giao dịch tài chính | Lịch sử thanh toán dịch vụ | trans_id PK, record_id FK, payment_method, amount, trans_date | settles CORPORATE_TRAVEL_RATE_AGREEMENT_RECORD |
| 5 | CORPORATE_TRAVEL_RATE_AGREEMENT_STAFF_ASSIGNMENT | Phân công nhân sự | Lịch phân công thực hiện công việc | assignment_id PK, record_id FK, staff_id, assigned_time, completion_time | tracks CORPORATE_TRAVEL_RATE_AGREEMENT_RECORD |
| 6 | CORPORATE_TRAVEL_RATE_AGREEMENT_AUDIT_LOG | Nhật ký kiểm toán | Lưu vết thao tác người dùng | log_id PK, record_id FK, user_id, action_type, timestamp | audits CORPORATE_TRAVEL_RATE_AGREEMENT_RECORD |
| 7 | CORPORATE_TRAVEL_RATE_AGREEMENT_FEEDBACK | Đánh giá dịch vụ | Phản hồi của khách hàng | feedback_id PK, record_id FK, rating_score, comment, created_at | evaluates CORPORATE_TRAVEL_RATE_AGREEMENT_RECORD |
| 8 | CORPORATE_TRAVEL_RATE_AGREEMENT_CONFIG | Cấu hình hệ thống | Tham số quy tắc vận hành | config_id PK, param_key, param_value, description | configures System |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | CORPORATE_TRAVEL_RATE_AGREEMENT_RECORD | one-to-many | CORPORATE_TRAVEL_RATE_AGREEMENT_DETAIL | contains | Một hồ sơ nghiệp vụ chứa nhiều hạng mục chi tiết |
| 2 | CORPORATE_TRAVEL_RATE_AGREEMENT_RECORD | one-to-many | CORPORATE_TRAVEL_RATE_AGREEMENT_TRANSACTION | settles | Một hồ sơ nghiệp vụ có thể thanh toán qua nhiều lần giao dịch |
| 3 | CORPORATE_TRAVEL_RATE_AGREEMENT_CATALOG | one-to-many | CORPORATE_TRAVEL_RATE_AGREEMENT_DETAIL | applies to | Danh mục áp dụng đơn giá cho chi tiết dịch vụ |
| 4 | CORPORATE_TRAVEL_RATE_AGREEMENT_RECORD | one-to-many | CORPORATE_TRAVEL_RATE_AGREEMENT_STAFF_ASSIGNMENT | tracks | Hồ sơ ghi nhận các đợt phân công nhân viên xử lý |
| 5 | CORPORATE_TRAVEL_RATE_AGREEMENT_RECORD | one-to-many | CORPORATE_TRAVEL_RATE_AGREEMENT_AUDIT_LOG | audits | Nhật ký lưu trữ tất cả thao tác biến động của hồ sơ |
