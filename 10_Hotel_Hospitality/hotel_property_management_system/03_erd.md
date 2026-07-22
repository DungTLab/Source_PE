# Conceptual ERD — Hotel Property Management System (PMS)

## Mermaid Code

```mermaid
erDiagram
    GUEST {
        guest_id PK
        full_name
        passport_no
        email
        phone
        created_at
    }
    ROOM_TYPE {
        room_type_id PK
        type_name
        base_rate
        capacity
        amenities
    }
    ROOM {
        room_id PK
        room_number
        room_type_id FK
        floor
        status
    }
    RESERVATION {
        reservation_id PK
        guest_id FK
        room_id FK
        check_in_date
        check_out_date
        status
    }
    FOLIO {
        folio_id PK
        reservation_id FK
        total_amount
        paid_amount
        balance
    }
    FOLIO_TRANSACTION {
        trans_id PK
        folio_id FK
        service_type
        amount
        trans_date
    }
    RATE_PLAN {
        rate_plan_id PK
        plan_code
        description
        discount_percent
        is_active
    }
    HOUSEKEEPING_LOG {
        log_id PK
        room_id FK
        staff_id
        clean_status
        updated_at
    }

    GUEST ||--o{ RESERVATION : "places"
    ROOM_TYPE ||--o{ ROOM : "categorizes"
    ROOM ||--o{ RESERVATION : "assigned to"
    RESERVATION ||--|| FOLIO : "generates"
    FOLIO ||--o{ FOLIO_TRANSACTION : "contains"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|--------------------|
| 1 | GUEST | Khách hàng | Hồ sơ cá nhân khách lưu trú | guest_id PK, full_name, passport_no, email, phone, created_at | places RESERVATION |
| 2 | ROOM_TYPE | Loại phòng | Hạng phòng và cấu hình | room_type_id PK, type_name, base_rate, capacity, amenities | categorizes ROOM |
| 3 | ROOM | Phòng | Phòng vật lý trong khách sạn | room_id PK, room_number, room_type_id FK, floor, status | assigned to RESERVATION |
| 4 | RESERVATION | Đặt phòng | Hồ sơ đăng ký lưu trú | reservation_id PK, guest_id FK, room_id FK, check_in_date, check_out_date, status | generates FOLIO |
| 5 | FOLIO | Folio tài khoản | Hóa đơn tài khoản phòng | folio_id PK, reservation_id FK, total_amount, paid_amount, balance | contains FOLIO_TRANSACTION |
| 6 | FOLIO_TRANSACTION | Giao dịch Folio | Chi tiết từng khoản nợ/có | trans_id PK, folio_id FK, service_type, amount, trans_date | belongs to FOLIO |
| 7 | RATE_PLAN | Gói giá | Chính sách giá bán phòng | rate_plan_id PK, plan_code, description, discount_percent, is_active | applies to RESERVATION |
| 8 | HOUSEKEEPING_LOG | Nhật ký buồng phòng | Lịch sử dọn phòng | log_id PK, room_id FK, staff_id, clean_status, updated_at | tracks ROOM |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | GUEST | one-to-many | RESERVATION | places | Một khách hàng có thể có nhiều lượt đặt phòng |
| 2 | ROOM_TYPE | one-to-many | ROOM | categorizes | Một loại phòng chứa nhiều phòng vật lý |
| 3 | ROOM | one-to-many | RESERVATION | assigned to | Một phòng gán cho nhiều đợt lưu trú |
| 4 | RESERVATION | one-to-one | FOLIO | generates | Mỗi lượt đặt phòng có một tài khoản folio |
| 5 | FOLIO | one-to-many | FOLIO_TRANSACTION | contains | Một folio ghi nhận nhiều giao dịch |
