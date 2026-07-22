# Swimlane Diagram — IT Service Management (ITSM) System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["End User / Employee"]
        U1["Access ITSM Portal"]
        U2["Fill Ticket Form & Submit"]
        U3["Review KB Workaround"]
        U4["Verify Solution & Provide Rating"]
    end

    subgraph Lane2["ITSM System Portal"]
        S1["Suggest KB Articles"]
        S2["Validate Inputs & Calculate SLA Priority"]
        S3["Notify Agent & Route to Queue"]
        S4{"Is Issue Resolved?"}
        S5["Update Status to Resolved & Send Survey"]
        S6["Close Ticket Automatically"]
    end

    subgraph Lane3["IT Support Agent"]
        A1["Claim Ticket from Queue"]
        A2["Diagnose Incident & Test Fix"]
        A3{"Needs Escalation?"}
        A4["Submit Resolution & Fix Summary"]
    end

    subgraph Lane4["IT Service Manager"]
        M1["Review High Impact Escalation"]
        M2["Assign Senior Specialist or Change Request"]
    end

    Finish(["End"])

    Start --> U1 --> U2 --> S1
    S1 --> U3
    U3 --> S2 --> S3 --> A1 --> A2 --> A3
    
    A3 -->|"No"| A4 --> S4
    A3 -->|"Yes"| M1 --> M2 --> A2

    S4 -->|"Yes"| S5 --> U4 --> S6 --> Finish
    S4 -->|"No - User Reopens"| A2
```

## Flow Description | Mô tả luồng xử lý

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | End User / Employee | Truy cập cổng dịch vụ, nhập thông tin mô tả sự cố, thử áp dụng bài viết hướng dẫn (KB), và xác nhận đánh giá chất lượng sau khi hỗ trợ hoàn tất. |
| 2 | ITSM System Portal | Tự động gợi ý giải pháp từ KB, kiểm tra tính hợp lệ của dữ liệu, tính toán độ ưu tiên SLA, điều phối ticket vào hàng chờ, và gửi thông báo tự động. |
| 3 | IT Support Agent | Nhận ticket từ hàng chờ, tiến hành chẩn đoán kỹ thuật, thực hiện sửa lỗi, đánh giá nhu cầu leo thang sự cố, và cập nhật kết quả xử lý. |
| 4 | IT Service Manager | Tiếp nhận và phê duyệt các sự cố phức tạp bị leo thang (Escalation), điều phối chuyên gia cấp cao hoặc tạo Yêu cầu Thay đổi (RFC). |
