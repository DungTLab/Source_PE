# Swimlane Diagram — Hotel Booking & Reservation System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Guest[" Online Guest "]
        A1["Select dates & search rooms"]
        A2["Choose room & fill guest info"]
        A3["Submit payment credentials"]
    end

    subgraph System[" Booking Engine "]
        S1["Check inventory & show rates"]
        S2["Hold room for 15 mins"]
        S3["Confirm booking & issue voucher"]
        S4["Release hold & show payment error"]
    end

    subgraph PayGateway[" Payment Gateway "]
        P1["Authorize transaction"]
        D1{"Is payment successful?"}
    end

    Finish(["End"])

    Start --> A1
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Online Guest | Tìm kiếm phòng, nhập thông tin và thanh toán |
| 2 | Booking Engine | Kiểm tra tồn kho, giữ chỗ tạm thời và tạo voucher |
| 3 | Payment Gateway | Xác thực thẻ và trừ tiền cọc |
