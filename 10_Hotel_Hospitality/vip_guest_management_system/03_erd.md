# Conceptual ERD — VIP Guest Management System

## Mermaid Code

```mermaid
erDiagram
    VIP_GUEST_RECORD {
        record_id PK
        guest_id FK
        service_code
        status
        created_at
    }
    VIP_GUEST_DETAIL {
        detail_id PK
        record_id FK
        item_name
        quantity
        unit_price
    }
    VIP_GUEST_CATALOG {
        catalog_id PK
        category_name
        base_price
        is_active
    }
    VIP_GUEST_TRANSACTION {
        trans_id PK
        record_id FK
        payment_method
        amount
        trans_date
    }
    VIP_GUEST_STAFF_ASSIGNMENT {
        assignment_id PK
        record_id FK
        staff_id
        assigned_time
        completion_time
    }
    VIP_GUEST_AUDIT_LOG {
        log_id PK
        record_id FK
        user_id
        action_type
        timestamp
    }
    VIP_GUEST_FEEDBACK {
        feedback_id PK
        record_id FK
        rating_score
        comment
        created_at
    }
    VIP_GUEST_CONFIG {
        config_id PK
        param_key
        param_value
        description
    }

    VIP_GUEST_RECORD ||--o{ VIP_GUEST_DETAIL : "contains"
    VIP_GUEST_RECORD ||--o{ VIP_GUEST_TRANSACTION : "settles"
    VIP_GUEST_CATALOG ||--o{ VIP_GUEST_DETAIL : "applies to"
    VIP_GUEST_RECORD ||--o{ VIP_GUEST_STAFF_ASSIGNMENT : "tracks"
    VIP_GUEST_RECORD ||--o{ VIP_GUEST_AUDIT_LOG : "audits"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|--------------------|
| 1 | VIP_GUEST_RECORD | Hồ sơ VIP | Bản ghi nghiệp vụ chính của VIP Guest Management System | record_id PK, guest_id FK, service_code, status, created_at | contains VIP_GUEST_DETAIL |
| 2 | VIP_GUEST_DETAIL | Chi tiết VIP | Chi tiết từng hạng mục dịch vụ | detail_id PK, record_id FK, item_name, quantity, unit_price | belongs to VIP_GUEST_RECORD |
| 3 | VIP_GUEST_CATALOG | Danh mục dịch vụ | Danh mục bảng giá và cấu hình | catalog_id PK, category_name, base_price, is_active | applies to VIP_GUEST_DETAIL |
| 4 | VIP_GUEST_TRANSACTION | Giao dịch tài chính | Lịch sử thanh toán dịch vụ | trans_id PK, record_id FK, payment_method, amount, trans_date | settles VIP_GUEST_RECORD |
| 5 | VIP_GUEST_STAFF_ASSIGNMENT | Phân công nhân sự | Lịch phân công thực hiện công việc | assignment_id PK, record_id FK, staff_id, assigned_time, completion_time | tracks VIP_GUEST_RECORD |
| 6 | VIP_GUEST_AUDIT_LOG | Nhật ký kiểm toán | Lưu vết thao tác người dùng | log_id PK, record_id FK, user_id, action_type, timestamp | audits VIP_GUEST_RECORD |
| 7 | VIP_GUEST_FEEDBACK | Đánh giá dịch vụ | Phản hồi của khách hàng | feedback_id PK, record_id FK, rating_score, comment, created_at | evaluates VIP_GUEST_RECORD |
| 8 | VIP_GUEST_CONFIG | Cấu hình hệ thống | Tham số quy tắc vận hành | config_id PK, param_key, param_value, description | configures System |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | VIP_GUEST_RECORD | one-to-many | VIP_GUEST_DETAIL | contains | Một hồ sơ nghiệp vụ chứa nhiều hạng mục chi tiết |
| 2 | VIP_GUEST_RECORD | one-to-many | VIP_GUEST_TRANSACTION | settles | Một hồ sơ nghiệp vụ có thể thanh toán qua nhiều lần giao dịch |
| 3 | VIP_GUEST_CATALOG | one-to-many | VIP_GUEST_DETAIL | applies to | Danh mục áp dụng đơn giá cho chi tiết dịch vụ |
| 4 | VIP_GUEST_RECORD | one-to-many | VIP_GUEST_STAFF_ASSIGNMENT | tracks | Hồ sơ ghi nhận các đợt phân công nhân viên xử lý |
| 5 | VIP_GUEST_RECORD | one-to-many | VIP_GUEST_AUDIT_LOG | audits | Nhật ký lưu trữ tất cả thao tác biến động của hồ sơ |
