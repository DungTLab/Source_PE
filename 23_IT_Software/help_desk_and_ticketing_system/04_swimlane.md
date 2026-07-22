# Swimlane Diagram — Help Desk & Ticketing System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["End User / Customer"]
        U1["Access Help Desk Portal"]
        U2["Fill Ticket Form & Attach Files"]
        U3["Check Auto-Suggested KB Articles"]
        U4["Review Solution & Submit CSAT Rating"]
    end

    subgraph Lane2["Help Desk Portal & Auto-Routing"]
        S1["Validate Input & Detect Category"]
        S2["Auto-Assign Ticket based on Rules & SLA"]
        S3["Send Email/SMS Notification to Customer"]
        S4{"Is Solution Accepted?"}
        S5["Update Status to Closed & Record CSAT"]
    end

    subgraph Lane3["Help Desk Support Agent"]
        A1["Receive Assigned Ticket"]
        A2["Diagnose Issue & Apply Macro Reply"]
        A3{"Exceeds Tier 1 Scope?"}
        A4["Submit Resolution & Mark Ticket Resolved"]
    end

    subgraph Lane4["Technical Team Lead"]
        M1["Review Escalated Complex Ticket"]
        M2["Assign Tier 2 Expert or Apply Bug Fix"]
    end

    Finish(["End"])

    Start --> U1 --> U2 --> U3
    U3 --> S1 --> S2 --> A1 --> A2 --> A3
    
    A3 -->|"No"| A4 --> S3 --> S4
    A3 -->|"Yes"| M1 --> M2 --> A2

    S4 -->|"Yes"| U4 --> S5 --> Finish
    S4 -->|"No - Reopen"| A2
```

## Flow Description | Mô tả luồng xử lý

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | End User / Customer | Khởi tạo yêu cầu hỗ trợ qua cổng Web Portal, đính kèm tệp tin mô tả lỗi, tra cứu bài viết gợi ý tự động, xem phản hồi và gửi đánh giá chất lượng (CSAT) sau khi kết thúc. |
| 2 | Help Desk Portal & Auto-Routing | Kiểm tra tính hợp lệ của dữ liệu nhập, xác định danh mục, tự động điều phối ticket đến đúng kỹ thuật viên theo quy tắc SLA, và quản lý các thông báo tự động. |
| 3 | Help Desk Support Agent | Tiếp nhận ticket được điều phối, chẩn đoán nguyên nhân sự cố, áp dụng mẫu câu trả lời nhanh (Macro) hoặc nhập các bước khắc phục, đánh giá nhu cầu leo thang công việc. |
| 4 | Technical Team Lead | Đóng vai trò điểm leo thang cấp cao (Tier 2/3), tiếp nhận các ticket phức tạp ngoài phạm vi xử lý của Tier 1, phân công chuyên gia hoặc phối hợp sửa lỗi hạ tầng. |
