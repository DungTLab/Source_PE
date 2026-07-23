# Conceptual ERD — Construction Project Management System

## Mermaid Code

```mermaid
erDiagram
    USER {
        user_id PK
        full_name
        email
        phone
        password_hash
        role_code
        status
        created_at
    }
    CONSTRUCTION_CORE_RECORD {
        record_id PK
        user_id FK
        title
        status_code
        category
        reference_code
        created_at
        updated_at
    }
    CONSTRUCTION_RECORD_DETAIL {
        detail_id PK
        record_id FK
        attribute_key
        attribute_value
        data_type
        is_mandatory
    }
    ATTACHMENT {
        attachment_id PK
        record_id FK
        file_name
        file_url
        mime_type
        file_size
        checksum
    }
    WORKFLOW_STATUS {
        status_id PK
        record_id FK
        previous_status
        new_status
        changed_by_user_id FK
        remarks
        timestamp
    }
    TRANSACTION_PAYMENT {
        payment_id PK
        record_id FK
        user_id FK
        amount
        currency
        payment_status
        gateway_trans_id
        paid_at
    }
    NOTIFICATION_LOG {
        notification_id PK
        user_id FK
        channel
        recipient
        content_preview
        delivery_status
        sent_at
    }
    AUDIT_LOG {
        audit_id PK
        user_id FK
        action_performed
        IP_address
        target_entity
        changes_json
        timestamp
    }

    USER ||--o{ CONSTRUCTION_CORE_RECORD : "submits"
    CONSTRUCTION_CORE_RECORD ||--o{ CONSTRUCTION_RECORD_DETAIL : "contains"
    CONSTRUCTION_CORE_RECORD ||--o{ ATTACHMENT : "attaches"
    CONSTRUCTION_CORE_RECORD ||--o{ WORKFLOW_STATUS : "tracks"
    USER ||--o{ WORKFLOW_STATUS : "executes"
    CONSTRUCTION_CORE_RECORD ||--o{ TRANSACTION_PAYMENT : "settled_by"
    USER ||--o{ TRANSACTION_PAYMENT : "pays"
    USER ||--o{ NOTIFICATION_LOG : "receives"
    USER ||--o{ AUDIT_LOG : "triggers"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|--------------------|
| 1 | USER | Người dùng | Central user repository storing profile info, credentials, and roles. | user_id PK, full_name, email, phone, password_hash, role_code, status, created_at | has many REQUEST, has many AUDIT_LOG |
| 2 | CONSTRUCTION_CORE_RECORD | Bản ghi Cốt lõi | Core data record representing a primary asset or transaction in Construction Project Management System. | record_id PK, user_id FK, title, status_code, category, reference_code, created_at, updated_at | belongs to USER, has many RECORD_DETAIL, has many ATTACHMENT |
| 3 | CONSTRUCTION_RECORD_DETAIL | Chi tiết Bản ghi | Extended parameters, attributes, and specifications of the record. | detail_id PK, record_id FK, attribute_key, attribute_value, data_type, is_mandatory | belongs to CONSTRUCTION_CORE_RECORD |
| 4 | ATTACHMENT | Tài liệu Đính kèm | Digital files, contracts, certificates, and media attachments. | attachment_id PK, record_id FK, file_name, file_url, mime_type, file_size, checksum | belongs to CONSTRUCTION_CORE_RECORD |
| 5 | WORKFLOW_STATUS | Trạng thái Luồng xử lý | Lifecycle state transitions and history tracking. | status_id PK, record_id FK, previous_status, new_status, changed_by_user_id FK, remarks, timestamp | belongs to CONSTRUCTION_CORE_RECORD, belongs to USER |
| 6 | TRANSACTION_PAYMENT | Giao dịch Thanh toán | Financial billing transactions and payment gateway receipts. | payment_id PK, record_id FK, user_id FK, amount, currency, payment_status, gateway_trans_id, paid_at | belongs to CONSTRUCTION_CORE_RECORD, belongs to USER |
| 7 | NOTIFICATION_LOG | Nhật ký Thông báo | System alerts, SMS messages, and email dispatch logs. | notification_id PK, user_id FK, channel, recipient, content_preview, delivery_status, sent_at | belongs to USER |
| 8 | AUDIT_LOG | Nhật ký Kiểm toán | Security and compliance audit trail of critical system operations. | audit_id PK, user_id FK, action_performed, IP_address, target_entity, changes_json, timestamp | belongs to USER |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | USER | ||--o{ | CONSTRUCTION_CORE_RECORD | submits | Một người dùng có thể khởi tạo nhiều bản ghi Construction Project Management System. |
| 2 | CONSTRUCTION_CORE_RECORD | ||--o{ | CONSTRUCTION_RECORD_DETAIL | contains | Một bản ghi cốt lõi bao gồm nhiều thông số chi tiết. |
| 3 | CONSTRUCTION_CORE_RECORD | ||--o{ | ATTACHMENT | attaches | Một bản ghi có đính kèm nhiều tập tin và chứng từ. |
| 4 | CONSTRUCTION_CORE_RECORD | ||--o{ | WORKFLOW_STATUS | tracks | Một bản ghi trải qua nhiều giai đoạn lịch sử trạng thái. |
| 5 | USER | ||--o{ | WORKFLOW_STATUS | executes | Một người dùng cập nhật trạng thái luồng xử lý. |
| 6 | CONSTRUCTION_CORE_RECORD | ||--o{ | TRANSACTION_PAYMENT | settled_by | Một bản ghi phát sinh giao dịch thanh toán. |
| 7 | USER | ||--o{ | TRANSACTION_PAYMENT | pays | Một người dùng thực hiện thanh toán cho các đơn hàng. |
| 8 | USER | ||--o{ | NOTIFICATION_LOG | receives | Một người dùng nhận nhiều thông báo gửi từ hệ thống. |
| 9 | USER | ||--o{ | AUDIT_LOG | triggers | Hành động của người dùng được ghi lại trong nhật ký kiểm toán. |

