# Conceptual ERD — Event Ticketing & Registration System

## Mermaid Code

```mermaid
erDiagram
    TICKET_EVENT {
        string event_id PK
        string title
        string venue_name
        string start_time
        string end_time
        string total_capacity
        string status
        string created_at
    }
    TICKET_TIER {
        string tier_id PK
        string event_id FK
        string tier_name
        string price
        string total_quota
        string available_quota
        string sales_start
        string sales_end
    }
    TICKET_ORDER {
        string order_id PK
        string event_id FK
        string customer_name
        string email
        string phone
        string total_amount
        string payment_status
        string order_date
    }
    TICKET_ITEM {
        string ticket_id PK
        string order_id FK
        string tier_id FK
        string ticket_code
        string attendee_name
        string qr_code_hash
        string status
        string checked_in_at
    }
    PROMO_CODE {
        string promo_id PK
        string event_id FK
        string code
        string discount_type
        string discount_value
        string max_uses
        string current_uses
        string valid_until
    }
    PAYMENT_TRANSACTION {
        string transaction_id PK
        string order_id FK
        string payment_method
        string gateway_ref
        string amount
        string status
        string transaction_time
    }
    REFUND_LOG {
        string refund_id PK
        string order_id FK
        string amount
        string reason
        string processed_by
        string refund_date
        string gateway_refund_ref
    }
    CHECK_IN_LOG {
        string scan_id PK
        string ticket_id FK
        string gate_name
        string scanner_device_id
        string scan_time
        string validation_status
    }
    SEAT_MAP {
        string seat_id PK
        string tier_id FK
        string section
        string row_number
        string seat_number
        string status
        string reserved_until
    }

    TICKET_EVENT ||--o{ TICKET_TIER : "offers"
    TICKET_EVENT ||--o{ TICKET_ORDER : "receives"
    TICKET_ORDER ||--o{ TICKET_ITEM : "contains"
    TICKET_TIER ||--o{ TICKET_ITEM : "categorizes"
    TICKET_ORDER ||--|| PAYMENT_TRANSACTION : "generates"
    TICKET_ORDER ||--o{ REFUND_LOG : "tracks"
    TICKET_ITEM ||--o{ CHECK_IN_LOG : "records"
    TICKET_TIER ||--o{ SEAT_MAP : "allocates"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|-------------------|
| 1 | TICKET_EVENT | Sự kiện Bán vé | Master event record configured for ticketing. | event_id PK, title, venue_name, start_time, end_time, total_capacity, status, created_at | offers tiers, receives orders |
| 2 | TICKET_TIER | Hạng vé | Pricing tier defining price, quota, and benefits. | tier_id PK, event_id FK, tier_name, price, total_quota, available_quota, sales_start, sales_end | belongs to TICKET_EVENT |
| 3 | TICKET_ORDER | Đơn hàng Vé | Transaction record for purchased tickets. | order_id PK, event_id FK, customer_name, email, phone, total_amount, payment_status, order_date | belongs to TICKET_EVENT |
| 4 | TICKET_ITEM | Vé Cá thể | Individual scannable ticket issued to attendee. | ticket_id PK, order_id FK, tier_id FK, ticket_code, attendee_name, qr_code_hash, status, checked_in_at | belongs to TICKET_ORDER |
| 5 | PROMO_CODE | Mã Giảm giá | Discount coupon code with validity conditions. | promo_id PK, event_id FK, code, discount_type, discount_value, max_uses, current_uses, valid_until | belongs to TICKET_EVENT |
| 6 | PAYMENT_TRANSACTION | Giao dịch Thanh toán | Financial transaction log from payment gateway. | transaction_id PK, order_id FK, payment_method, gateway_ref, amount, status, transaction_time | belongs to TICKET_ORDER |
| 7 | REFUND_LOG | Nhật ký Hoàn tiền | Audit log of refunded ticket orders. | refund_id PK, order_id FK, amount, reason, processed_by, refund_date, gateway_refund_ref | belongs to TICKET_ORDER |
| 8 | CHECK_IN_LOG | Nhật ký Check-in | Entry scan log recorded at venue turnstile. | scan_id PK, ticket_id FK, gate_name, scanner_device_id, scan_time, validation_status | belongs to TICKET_ITEM |
| 9 | SEAT_MAP | Sơ đồ Chỗ ngồi | Seating map for reserved seating events. | seat_id PK, tier_id FK, section, row_number, seat_number, status, reserved_until | belongs to TICKET_TIER |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | TICKET_EVENT | one-to-many | TICKET_TIER | offers | Một sự kiện cung cấp nhiều hạng vé. |
| 2 | TICKET_EVENT | one-to-many | TICKET_ORDER | receives | Một sự kiện nhận nhiều đơn hàng vé. |
| 3 | TICKET_ORDER | one-to-many | TICKET_ITEM | contains | Một đơn hàng chứa nhiều vé cá thể. |
| 4 | TICKET_TIER | one-to-many | TICKET_ITEM | categorizes | Một hạng vé phân loại nhiều vé cá thể. |
| 5 | TICKET_ORDER | one-to-one | PAYMENT_TRANSACTION | generates | Một đơn hàng tạo ra một giao dịch thanh toán. |
| 6 | TICKET_ORDER | one-to-many | REFUND_LOG | tracks | Một đơn hàng theo dõi các lần hoàn tiền. |
| 7 | TICKET_ITEM | one-to-many | CHECK_IN_LOG | records | Một vé ghi nhận nhiều lần quét check-in. |
| 8 | TICKET_TIER | one-to-many | SEAT_MAP | allocates | Một hạng vé phân bổ các chỗ ngồi. |

