# Swimlane Diagram — Concierge & Guest Service System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph UserLane[" Hotel Guest "]
        U1["Submit Concierge request"]
    end

    subgraph StaffLane[" Concierge Staff "]
        S1["Verify request & check parameters"]
        S2["Execute service & record progress"]
        S3["Close task & update PMS status"]
        S4["Reject request & send reason to guest"]
    end

    subgraph SystemLane[" System Core "]
        Y1["Validate availability & pricing rules"]
        D1{"Is request approved & valid?"}
        Y2["Calculate final charges & build invoice"]
    end

    subgraph PayLane[" Payment Gateway "]
        P1["Process card / folio settlement"]
    end

    Finish(["End"])

    Start --> U1
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Hotel Guest | Khởi tạo yêu cầu và thanh toán dịch vụ |
| 2 | Concierge Staff | Tiếp nhận, thực hiện công việc và cập nhật kết quả |
| 3 | System Core | Xử lý dữ liệu, kiểm tra quy tắc và tính tiền |
| 4 | Payment Gateway | Xác thực và thanh toán giao dịch |
