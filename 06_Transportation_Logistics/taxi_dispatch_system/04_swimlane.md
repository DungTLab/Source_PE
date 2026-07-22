# Swimlane Diagram — Taxi Dispatch System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start Process"])

    subgraph Lane1["Passenger / Rider (Requester)"]
        A1["Input Order Details & Requirements"]
        A2["Review Estimated Cost & Route"]
        A3["Confirm Order Submission"]
        A4["Receive Real-time Status & ePOD"]
    end

    subgraph Lane2["Taxi Dispatch System (Core Engine)"]
        S1["Validate Order & Coordinates"]
        S2["Run Route & Load Optimization"]
        S3{"Resource Available?"}
        S4["Assign Vehicle & Driver"]
        S5["Monitor Telematics & Geofence"]
        S6["Verify Proof of Delivery (ePOD)"]
    end

    subgraph Lane3["Driver Partner (Field Executor)"]
        B1["Receive Dispatch Notification"]
        B2["Accept Assignment & Start Route"]
        B3["Perform Pickup & Update Progress"]
        B4["Deliver Payload & Capture ePOD"]
    end

    subgraph Lane4["Dispatch Operator (Operations Manager)"]
        M1["Monitor Operational Dashboard"]
        M2["Handle Resource Exception / Override"]
    end

    Finish(["End Process"])

    Start --> A1 --> S1 --> S2 --> S3
    S3 -->|"Yes"| S4 --> A2 --> A3 --> B1
    S3 -->|"No"| M2 --> S4
    B1 --> B2 --> B3 --> S5 --> B4 --> S6 --> A4 --> Finish
    S5 -.-> M1
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Passenger / Rider (Requester) | Khởi tạo đơn vận tải, xem chi phí dự kiến, xác nhận đặt chỗ và nhận thông báo theo dõi cùng bằng chứng giao hàng ePOD. |
| 2 | Taxi Dispatch System (Core Engine) | Đóng vai trò hệ thống trung tâm: kiểm tra tính hợp lệ, chạy thuật toán tối ưu hóa lộ trình, phân công tài nguyên, giám sát GPS và xác thực ePOD. |
| 3 | Driver Partner (Field Executor) | Nhận lệnh điều động, xác nhận ca làm việc, di chuyển theo lộ trình, cập nhật tiến độ và thu thập chữ ký/mã OTP khi hoàn thành. |
| 4 | Dispatch Operator (Operations Manager) | Giám sát toàn bộ luồng vận hành trên màn hình Real-time Dashboard và can thiệp xử lý khi có ngoại lệ thiếu tài nguyên hoặc sự cố. |
