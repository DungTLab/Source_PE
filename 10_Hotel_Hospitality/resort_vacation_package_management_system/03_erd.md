# Conceptual ERD — Resort & Vacation Package Management System

## Mermaid Code

```mermaid
erDiagram
    RESORT_VACATION_PACKAGE_RECORD {
        record_id PK
        guest_id FK
        service_code
        status
        created_at
    }
    RESORT_VACATION_PACKAGE_DETAIL {
        detail_id PK
        record_id FK
        item_name
        quantity
        unit_price
    }
    RESORT_VACATION_PACKAGE_CATALOG {
        catalog_id PK
        category_name
        base_price
        is_active
    }
    RESORT_VACATION_PACKAGE_TRANSACTION {
        trans_id PK
        record_id FK
        payment_method
        amount
        trans_date
    }
    RESORT_VACATION_PACKAGE_STAFF_ASSIGNMENT {
        assignment_id PK
        record_id FK
        staff_id
        assigned_time
        completion_time
    }
    RESORT_VACATION_PACKAGE_AUDIT_LOG {
        log_id PK
        record_id FK
        user_id
        action_type
        timestamp
    }
    RESORT_VACATION_PACKAGE_FEEDBACK {
        feedback_id PK
        record_id FK
        rating_score
        comment
        created_at
    }
    RESORT_VACATION_PACKAGE_CONFIG {
        config_id PK
        param_key
        param_value
        description
    }

    RESORT_VACATION_PACKAGE_RECORD ||--o{ RESORT_VACATION_PACKAGE_DETAIL : "contains"
    RESORT_VACATION_PACKAGE_RECORD ||--o{ RESORT_VACATION_PACKAGE_TRANSACTION : "settles"
    RESORT_VACATION_PACKAGE_CATALOG ||--o{ RESORT_VACATION_PACKAGE_DETAIL : "applies to"
    RESORT_VACATION_PACKAGE_RECORD ||--o{ RESORT_VACATION_PACKAGE_STAFF_ASSIGNMENT : "tracks"
    RESORT_VACATION_PACKAGE_RECORD ||--o{ RESORT_VACATION_PACKAGE_AUDIT_LOG : "audits"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|--------------------|
| 1 | RESORT_VACATION_PACKAGE_RECORD | Hồ sơ Resort | Bản ghi nghiệp vụ chính của Resort & Vacation Package Management System | record_id PK, guest_id FK, service_code, status, created_at | contains RESORT_VACATION_PACKAGE_DETAIL |
| 2 | RESORT_VACATION_PACKAGE_DETAIL | Chi tiết Resort | Chi tiết từng hạng mục dịch vụ | detail_id PK, record_id FK, item_name, quantity, unit_price | belongs to RESORT_VACATION_PACKAGE_RECORD |
| 3 | RESORT_VACATION_PACKAGE_CATALOG | Danh mục dịch vụ | Danh mục bảng giá và cấu hình | catalog_id PK, category_name, base_price, is_active | applies to RESORT_VACATION_PACKAGE_DETAIL |
| 4 | RESORT_VACATION_PACKAGE_TRANSACTION | Giao dịch tài chính | Lịch sử thanh toán dịch vụ | trans_id PK, record_id FK, payment_method, amount, trans_date | settles RESORT_VACATION_PACKAGE_RECORD |
| 5 | RESORT_VACATION_PACKAGE_STAFF_ASSIGNMENT | Phân công nhân sự | Lịch phân công thực hiện công việc | assignment_id PK, record_id FK, staff_id, assigned_time, completion_time | tracks RESORT_VACATION_PACKAGE_RECORD |
| 6 | RESORT_VACATION_PACKAGE_AUDIT_LOG | Nhật ký kiểm toán | Lưu vết thao tác người dùng | log_id PK, record_id FK, user_id, action_type, timestamp | audits RESORT_VACATION_PACKAGE_RECORD |
| 7 | RESORT_VACATION_PACKAGE_FEEDBACK | Đánh giá dịch vụ | Phản hồi của khách hàng | feedback_id PK, record_id FK, rating_score, comment, created_at | evaluates RESORT_VACATION_PACKAGE_RECORD |
| 8 | RESORT_VACATION_PACKAGE_CONFIG | Cấu hình hệ thống | Tham số quy tắc vận hành | config_id PK, param_key, param_value, description | configures System |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | RESORT_VACATION_PACKAGE_RECORD | one-to-many | RESORT_VACATION_PACKAGE_DETAIL | contains | Một hồ sơ nghiệp vụ chứa nhiều hạng mục chi tiết |
| 2 | RESORT_VACATION_PACKAGE_RECORD | one-to-many | RESORT_VACATION_PACKAGE_TRANSACTION | settles | Một hồ sơ nghiệp vụ có thể thanh toán qua nhiều lần giao dịch |
| 3 | RESORT_VACATION_PACKAGE_CATALOG | one-to-many | RESORT_VACATION_PACKAGE_DETAIL | applies to | Danh mục áp dụng đơn giá cho chi tiết dịch vụ |
| 4 | RESORT_VACATION_PACKAGE_RECORD | one-to-many | RESORT_VACATION_PACKAGE_STAFF_ASSIGNMENT | tracks | Hồ sơ ghi nhận các đợt phân công nhân viên xử lý |
| 5 | RESORT_VACATION_PACKAGE_RECORD | one-to-many | RESORT_VACATION_PACKAGE_AUDIT_LOG | audits | Nhật ký lưu trữ tất cả thao tác biến động của hồ sơ |
