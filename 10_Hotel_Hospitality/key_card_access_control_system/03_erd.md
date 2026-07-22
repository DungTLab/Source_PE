# Conceptual ERD — Key Card & Access Control System

## Mermaid Code

```mermaid
erDiagram
    KEY_CARD_ACCESS_CONTROL_RECORD {
        record_id PK
        guest_id FK
        service_code
        status
        created_at
    }
    KEY_CARD_ACCESS_CONTROL_DETAIL {
        detail_id PK
        record_id FK
        item_name
        quantity
        unit_price
    }
    KEY_CARD_ACCESS_CONTROL_CATALOG {
        catalog_id PK
        category_name
        base_price
        is_active
    }
    KEY_CARD_ACCESS_CONTROL_TRANSACTION {
        trans_id PK
        record_id FK
        payment_method
        amount
        trans_date
    }
    KEY_CARD_ACCESS_CONTROL_STAFF_ASSIGNMENT {
        assignment_id PK
        record_id FK
        staff_id
        assigned_time
        completion_time
    }
    KEY_CARD_ACCESS_CONTROL_AUDIT_LOG {
        log_id PK
        record_id FK
        user_id
        action_type
        timestamp
    }
    KEY_CARD_ACCESS_CONTROL_FEEDBACK {
        feedback_id PK
        record_id FK
        rating_score
        comment
        created_at
    }
    KEY_CARD_ACCESS_CONTROL_CONFIG {
        config_id PK
        param_key
        param_value
        description
    }

    KEY_CARD_ACCESS_CONTROL_RECORD ||--o{ KEY_CARD_ACCESS_CONTROL_DETAIL : "contains"
    KEY_CARD_ACCESS_CONTROL_RECORD ||--o{ KEY_CARD_ACCESS_CONTROL_TRANSACTION : "settles"
    KEY_CARD_ACCESS_CONTROL_CATALOG ||--o{ KEY_CARD_ACCESS_CONTROL_DETAIL : "applies to"
    KEY_CARD_ACCESS_CONTROL_RECORD ||--o{ KEY_CARD_ACCESS_CONTROL_STAFF_ASSIGNMENT : "tracks"
    KEY_CARD_ACCESS_CONTROL_RECORD ||--o{ KEY_CARD_ACCESS_CONTROL_AUDIT_LOG : "audits"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|--------------------|
| 1 | KEY_CARD_ACCESS_CONTROL_RECORD | Hồ sơ Access Control | Bản ghi nghiệp vụ chính của Key Card & Access Control System | record_id PK, guest_id FK, service_code, status, created_at | contains KEY_CARD_ACCESS_CONTROL_DETAIL |
| 2 | KEY_CARD_ACCESS_CONTROL_DETAIL | Chi tiết Access Control | Chi tiết từng hạng mục dịch vụ | detail_id PK, record_id FK, item_name, quantity, unit_price | belongs to KEY_CARD_ACCESS_CONTROL_RECORD |
| 3 | KEY_CARD_ACCESS_CONTROL_CATALOG | Danh mục dịch vụ | Danh mục bảng giá và cấu hình | catalog_id PK, category_name, base_price, is_active | applies to KEY_CARD_ACCESS_CONTROL_DETAIL |
| 4 | KEY_CARD_ACCESS_CONTROL_TRANSACTION | Giao dịch tài chính | Lịch sử thanh toán dịch vụ | trans_id PK, record_id FK, payment_method, amount, trans_date | settles KEY_CARD_ACCESS_CONTROL_RECORD |
| 5 | KEY_CARD_ACCESS_CONTROL_STAFF_ASSIGNMENT | Phân công nhân sự | Lịch phân công thực hiện công việc | assignment_id PK, record_id FK, staff_id, assigned_time, completion_time | tracks KEY_CARD_ACCESS_CONTROL_RECORD |
| 6 | KEY_CARD_ACCESS_CONTROL_AUDIT_LOG | Nhật ký kiểm toán | Lưu vết thao tác người dùng | log_id PK, record_id FK, user_id, action_type, timestamp | audits KEY_CARD_ACCESS_CONTROL_RECORD |
| 7 | KEY_CARD_ACCESS_CONTROL_FEEDBACK | Đánh giá dịch vụ | Phản hồi của khách hàng | feedback_id PK, record_id FK, rating_score, comment, created_at | evaluates KEY_CARD_ACCESS_CONTROL_RECORD |
| 8 | KEY_CARD_ACCESS_CONTROL_CONFIG | Cấu hình hệ thống | Tham số quy tắc vận hành | config_id PK, param_key, param_value, description | configures System |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | KEY_CARD_ACCESS_CONTROL_RECORD | one-to-many | KEY_CARD_ACCESS_CONTROL_DETAIL | contains | Một hồ sơ nghiệp vụ chứa nhiều hạng mục chi tiết |
| 2 | KEY_CARD_ACCESS_CONTROL_RECORD | one-to-many | KEY_CARD_ACCESS_CONTROL_TRANSACTION | settles | Một hồ sơ nghiệp vụ có thể thanh toán qua nhiều lần giao dịch |
| 3 | KEY_CARD_ACCESS_CONTROL_CATALOG | one-to-many | KEY_CARD_ACCESS_CONTROL_DETAIL | applies to | Danh mục áp dụng đơn giá cho chi tiết dịch vụ |
| 4 | KEY_CARD_ACCESS_CONTROL_RECORD | one-to-many | KEY_CARD_ACCESS_CONTROL_STAFF_ASSIGNMENT | tracks | Hồ sơ ghi nhận các đợt phân công nhân viên xử lý |
| 5 | KEY_CARD_ACCESS_CONTROL_RECORD | one-to-many | KEY_CARD_ACCESS_CONTROL_AUDIT_LOG | audits | Nhật ký lưu trữ tất cả thao tác biến động của hồ sơ |
