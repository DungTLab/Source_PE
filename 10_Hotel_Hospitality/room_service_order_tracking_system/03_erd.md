# Conceptual ERD — Room Service Order Tracking System

## Mermaid Code

```mermaid
erDiagram
    ROOM_SERVICE_ORDER_TRACKING_RECORD {
        record_id PK
        guest_id FK
        service_code
        status
        created_at
    }
    ROOM_SERVICE_ORDER_TRACKING_DETAIL {
        detail_id PK
        record_id FK
        item_name
        quantity
        unit_price
    }
    ROOM_SERVICE_ORDER_TRACKING_CATALOG {
        catalog_id PK
        category_name
        base_price
        is_active
    }
    ROOM_SERVICE_ORDER_TRACKING_TRANSACTION {
        trans_id PK
        record_id FK
        payment_method
        amount
        trans_date
    }
    ROOM_SERVICE_ORDER_TRACKING_STAFF_ASSIGNMENT {
        assignment_id PK
        record_id FK
        staff_id
        assigned_time
        completion_time
    }
    ROOM_SERVICE_ORDER_TRACKING_AUDIT_LOG {
        log_id PK
        record_id FK
        user_id
        action_type
        timestamp
    }
    ROOM_SERVICE_ORDER_TRACKING_FEEDBACK {
        feedback_id PK
        record_id FK
        rating_score
        comment
        created_at
    }
    ROOM_SERVICE_ORDER_TRACKING_CONFIG {
        config_id PK
        param_key
        param_value
        description
    }

    ROOM_SERVICE_ORDER_TRACKING_RECORD ||--o{ ROOM_SERVICE_ORDER_TRACKING_DETAIL : "contains"
    ROOM_SERVICE_ORDER_TRACKING_RECORD ||--o{ ROOM_SERVICE_ORDER_TRACKING_TRANSACTION : "settles"
    ROOM_SERVICE_ORDER_TRACKING_CATALOG ||--o{ ROOM_SERVICE_ORDER_TRACKING_DETAIL : "applies to"
    ROOM_SERVICE_ORDER_TRACKING_RECORD ||--o{ ROOM_SERVICE_ORDER_TRACKING_STAFF_ASSIGNMENT : "tracks"
    ROOM_SERVICE_ORDER_TRACKING_RECORD ||--o{ ROOM_SERVICE_ORDER_TRACKING_AUDIT_LOG : "audits"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|--------------------|
| 1 | ROOM_SERVICE_ORDER_TRACKING_RECORD | Hồ sơ Room Service | Bản ghi nghiệp vụ chính của Room Service Order Tracking System | record_id PK, guest_id FK, service_code, status, created_at | contains ROOM_SERVICE_ORDER_TRACKING_DETAIL |
| 2 | ROOM_SERVICE_ORDER_TRACKING_DETAIL | Chi tiết Room Service | Chi tiết từng hạng mục dịch vụ | detail_id PK, record_id FK, item_name, quantity, unit_price | belongs to ROOM_SERVICE_ORDER_TRACKING_RECORD |
| 3 | ROOM_SERVICE_ORDER_TRACKING_CATALOG | Danh mục dịch vụ | Danh mục bảng giá và cấu hình | catalog_id PK, category_name, base_price, is_active | applies to ROOM_SERVICE_ORDER_TRACKING_DETAIL |
| 4 | ROOM_SERVICE_ORDER_TRACKING_TRANSACTION | Giao dịch tài chính | Lịch sử thanh toán dịch vụ | trans_id PK, record_id FK, payment_method, amount, trans_date | settles ROOM_SERVICE_ORDER_TRACKING_RECORD |
| 5 | ROOM_SERVICE_ORDER_TRACKING_STAFF_ASSIGNMENT | Phân công nhân sự | Lịch phân công thực hiện công việc | assignment_id PK, record_id FK, staff_id, assigned_time, completion_time | tracks ROOM_SERVICE_ORDER_TRACKING_RECORD |
| 6 | ROOM_SERVICE_ORDER_TRACKING_AUDIT_LOG | Nhật ký kiểm toán | Lưu vết thao tác người dùng | log_id PK, record_id FK, user_id, action_type, timestamp | audits ROOM_SERVICE_ORDER_TRACKING_RECORD |
| 7 | ROOM_SERVICE_ORDER_TRACKING_FEEDBACK | Đánh giá dịch vụ | Phản hồi của khách hàng | feedback_id PK, record_id FK, rating_score, comment, created_at | evaluates ROOM_SERVICE_ORDER_TRACKING_RECORD |
| 8 | ROOM_SERVICE_ORDER_TRACKING_CONFIG | Cấu hình hệ thống | Tham số quy tắc vận hành | config_id PK, param_key, param_value, description | configures System |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | ROOM_SERVICE_ORDER_TRACKING_RECORD | one-to-many | ROOM_SERVICE_ORDER_TRACKING_DETAIL | contains | Một hồ sơ nghiệp vụ chứa nhiều hạng mục chi tiết |
| 2 | ROOM_SERVICE_ORDER_TRACKING_RECORD | one-to-many | ROOM_SERVICE_ORDER_TRACKING_TRANSACTION | settles | Một hồ sơ nghiệp vụ có thể thanh toán qua nhiều lần giao dịch |
| 3 | ROOM_SERVICE_ORDER_TRACKING_CATALOG | one-to-many | ROOM_SERVICE_ORDER_TRACKING_DETAIL | applies to | Danh mục áp dụng đơn giá cho chi tiết dịch vụ |
| 4 | ROOM_SERVICE_ORDER_TRACKING_RECORD | one-to-many | ROOM_SERVICE_ORDER_TRACKING_STAFF_ASSIGNMENT | tracks | Hồ sơ ghi nhận các đợt phân công nhân viên xử lý |
| 5 | ROOM_SERVICE_ORDER_TRACKING_RECORD | one-to-many | ROOM_SERVICE_ORDER_TRACKING_AUDIT_LOG | audits | Nhật ký lưu trữ tất cả thao tác biến động của hồ sơ |
