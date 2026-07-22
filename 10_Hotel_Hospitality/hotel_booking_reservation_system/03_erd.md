# Conceptual ERD — Hotel Booking & Reservation System

## Mermaid Code

```mermaid
erDiagram
    BOOKING {
        booking_id PK
        booking_ref
        guest_name
        email
        phone
        total_price
        status
    }
    BOOKING_DETAIL {
        detail_id PK
        booking_id FK
        room_type_id FK
        check_in
        check_out
        nightly_rate
    }
    PAYMENT_TRANSACTION {
        trans_id PK
        booking_id FK
        gateway_name
        amount
        trans_status
        created_at
    }
    PROMO_CODE {
        promo_id PK
        code
        discount_rate
        start_date
        end_date
        max_usage
    }
    ROOM_INVENTORY {
        inventory_id PK
        room_type_id FK
        date
        available_qty
        stop_sell
    }

    BOOKING ||--o{ BOOKING_DETAIL : "contains"
    BOOKING ||--o{ PAYMENT_TRANSACTION : "settles"
    PROMO_CODE ||--o{ BOOKING : "applies to"
    ROOM_INVENTORY ||--o{ BOOKING_DETAIL : "allocates"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|--------------------|
| 1 | BOOKING | Đơn đặt phòng | Hồ sơ đơn đặt phòng trực tuyến | booking_id PK, booking_ref, guest_name, email, phone, total_price, status | contains BOOKING_DETAIL |
| 2 | BOOKING_DETAIL | Chi tiết đặt phòng | Chi tiết từng phòng và ngày lưu trú | detail_id PK, booking_id FK, room_type_id FK, check_in, check_out, nightly_rate | belongs to BOOKING |
| 3 | PAYMENT_TRANSACTION | Giao dịch thanh toán | Lịch sử thanh toán cọc/hoàn tiền | trans_id PK, booking_id FK, gateway_name, amount, trans_status, created_at | settles BOOKING |
| 4 | PROMO_CODE | Mã giảm giá | Chương trình khuyến mãi | promo_id PK, code, discount_rate, start_date, end_date, max_usage | applies to BOOKING |
| 5 | ROOM_INVENTORY | Kho phòng khả dụng | Số lượng phòng còn trống theo ngày | inventory_id PK, room_type_id FK, date, available_qty, stop_sell | allocates BOOKING_DETAIL |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | BOOKING | one-to-many | BOOKING_DETAIL | contains | Một đơn đặt phòng có thể bao gồm nhiều phòng lưu trú |
| 2 | BOOKING | one-to-many | PAYMENT_TRANSACTION | settles | Một đơn đặt phòng có thể có nhiều giao dịch cọc hoặc thanh toán bổ sung |
| 3 | PROMO_CODE | one-to-many | BOOKING | applies to | Một mã giảm giá được áp dụng cho nhiều đơn đặt phòng |
| 4 | ROOM_INVENTORY | one-to-many | BOOKING_DETAIL | allocates | Kho phòng phân bổ phòng trống cho các chi tiết đặt phòng |
