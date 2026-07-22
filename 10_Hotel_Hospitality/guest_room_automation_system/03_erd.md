# Conceptual ERD — Guest Room Automation System

## Mermaid Code

```mermaid
erDiagram
    GUEST_ROOM_AUTOMATION_RECORD {
        record_id PK
        guest_id FK
        service_code
        status
        created_at
    }
    GUEST_ROOM_AUTOMATION_DETAIL {
        detail_id PK
        record_id FK
        item_name
        quantity
        unit_price
    }
    GUEST_ROOM_AUTOMATION_CATALOG {
        catalog_id PK
        category_name
        base_price
        is_active
    }
    GUEST_ROOM_AUTOMATION_TRANSACTION {
        trans_id PK
        record_id FK
        payment_method
        amount
        trans_date
    }
    GUEST_ROOM_AUTOMATION_STAFF_ASSIGNMENT {
        assignment_id PK
        record_id FK
        staff_id
        assigned_time
        completion_time
    }
    GUEST_ROOM_AUTOMATION_AUDIT_LOG {
        log_id PK
        record_id FK
        user_id
        action_type
        timestamp
    }
    GUEST_ROOM_AUTOMATION_FEEDBACK {
        feedback_id PK
        record_id FK
        rating_score
        comment
        created_at
    }
    GUEST_ROOM_AUTOMATION_CONFIG {
        config_id PK
        param_key
        param_value
        description
    }

    GUEST_ROOM_AUTOMATION_RECORD ||--o{ GUEST_ROOM_AUTOMATION_DETAIL : "contains"
    GUEST_ROOM_AUTOMATION_RECORD ||--o{ GUEST_ROOM_AUTOMATION_TRANSACTION : "settles"
    GUEST_ROOM_AUTOMATION_CATALOG ||--o{ GUEST_ROOM_AUTOMATION_DETAIL : "applies to"
    GUEST_ROOM_AUTOMATION_RECORD ||--o{ GUEST_ROOM_AUTOMATION_STAFF_ASSIGNMENT : "tracks"
    GUEST_ROOM_AUTOMATION_RECORD ||--o{ GUEST_ROOM_AUTOMATION_AUDIT_LOG : "audits"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|--------------------|
| 1 | GUEST_ROOM_AUTOMATION_RECORD | Hồ sơ IoT Automation | Bản ghi nghiệp vụ chính của Guest Room Automation System | record_id PK, guest_id FK, service_code, status, created_at | contains GUEST_ROOM_AUTOMATION_DETAIL |
| 2 | GUEST_ROOM_AUTOMATION_DETAIL | Chi tiết IoT Automation | Chi tiết từng hạng mục dịch vụ | detail_id PK, record_id FK, item_name, quantity, unit_price | belongs to GUEST_ROOM_AUTOMATION_RECORD |
| 3 | GUEST_ROOM_AUTOMATION_CATALOG | Danh mục dịch vụ | Danh mục bảng giá và cấu hình | catalog_id PK, category_name, base_price, is_active | applies to GUEST_ROOM_AUTOMATION_DETAIL |
| 4 | GUEST_ROOM_AUTOMATION_TRANSACTION | Giao dịch tài chính | Lịch sử thanh toán dịch vụ | trans_id PK, record_id FK, payment_method, amount, trans_date | settles GUEST_ROOM_AUTOMATION_RECORD |
| 5 | GUEST_ROOM_AUTOMATION_STAFF_ASSIGNMENT | Phân công nhân sự | Lịch phân công thực hiện công việc | assignment_id PK, record_id FK, staff_id, assigned_time, completion_time | tracks GUEST_ROOM_AUTOMATION_RECORD |
| 6 | GUEST_ROOM_AUTOMATION_AUDIT_LOG | Nhật ký kiểm toán | Lưu vết thao tác người dùng | log_id PK, record_id FK, user_id, action_type, timestamp | audits GUEST_ROOM_AUTOMATION_RECORD |
| 7 | GUEST_ROOM_AUTOMATION_FEEDBACK | Đánh giá dịch vụ | Phản hồi của khách hàng | feedback_id PK, record_id FK, rating_score, comment, created_at | evaluates GUEST_ROOM_AUTOMATION_RECORD |
| 8 | GUEST_ROOM_AUTOMATION_CONFIG | Cấu hình hệ thống | Tham số quy tắc vận hành | config_id PK, param_key, param_value, description | configures System |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | GUEST_ROOM_AUTOMATION_RECORD | one-to-many | GUEST_ROOM_AUTOMATION_DETAIL | contains | Một hồ sơ nghiệp vụ chứa nhiều hạng mục chi tiết |
| 2 | GUEST_ROOM_AUTOMATION_RECORD | one-to-many | GUEST_ROOM_AUTOMATION_TRANSACTION | settles | Một hồ sơ nghiệp vụ có thể thanh toán qua nhiều lần giao dịch |
| 3 | GUEST_ROOM_AUTOMATION_CATALOG | one-to-many | GUEST_ROOM_AUTOMATION_DETAIL | applies to | Danh mục áp dụng đơn giá cho chi tiết dịch vụ |
| 4 | GUEST_ROOM_AUTOMATION_RECORD | one-to-many | GUEST_ROOM_AUTOMATION_STAFF_ASSIGNMENT | tracks | Hồ sơ ghi nhận các đợt phân công nhân viên xử lý |
| 5 | GUEST_ROOM_AUTOMATION_RECORD | one-to-many | GUEST_ROOM_AUTOMATION_AUDIT_LOG | audits | Nhật ký lưu trữ tất cả thao tác biến động của hồ sơ |
