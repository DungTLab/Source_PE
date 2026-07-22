# Swimlane Diagram — Software Development Lifecycle Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Product Owner / Manager"]
        PO1["Define Requirement Epic & Stories"]
        PO2["Plan & Commit Sprint Backlog"]
        PO3["Review Final Release Readiness"]
    end

    subgraph Lane2["Software Engineer"]
        DEV1["Claim Work Item from Sprint Board"]
        DEV2["Write Code & Commit with Ticket ID"]
        DEV3["Create Pull Request & Request Review"]
    end

    subgraph Lane3["SDLC Management Platform"]
        SYS1["Auto-Link Git Commit & PR to Ticket"]
        SYS2["Trigger Automated CI Build & Sonar Scan"]
        SYS3{"Did CI Build & Tests Pass?"}
        SYS4["Update Ticket Status to Code Reviewed"]
        SYS5["Package Artifact & Lock Release Audit"]
    end

    subgraph Lane4["QA & Release Lead"]
        QA1["Execute Test Suite & Log Bugs"]
        QA2{"Any Open Critical Bugs?"}
        QA3["Approve Production Release Gate"]
    end

    Finish(["End"])

    Start --> PO1 --> PO2 --> DEV1 --> DEV2 --> DEV3 --> SYS1 --> SYS2 --> SYS3
    
    SYS3 -->|"No - Build Failed"| DEV2
    SYS3 -->|"Yes"| SYS4 --> QA1 --> QA2

    QA2 -->|"Yes - Critical Bug"| DEV2
    QA2 -->|"No"| PO3 --> QA3 --> SYS5 --> Finish
```

## Flow Description | Mô tả luồng xử lý

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Product Owner / Manager | Định nghĩa các Epic và User Story, lập kế hoạch cho chu kỳ Sprint, kiểm tra ma trận truy vết yêu cầu và xác nhận hoàn thành mục tiêu phát hành. |
| 2 | Software Engineer | Tiếp nhận công việc từ bảng Kanban/Scrum, thực hiện lập trình, commit mã nguồn đính kèm ID ticket, tạo Pull Request và tham gia review code đồng nghiệp. |
| 3 | SDLC Management Platform | Tự động bắt sự kiện Git để liên kết Commit/PR vào ticket, kích hoạt đường ống CI Build và kiểm tra bảo mật, cập nhật trạng thái công việc và đóng gói release. |
| 4 | QA & Release Lead | Thiết lập kịch bản kiểm thử, thực thi test suite, ghi nhận bug nếu có lỗi, và thực hiện duyệt cổng phát hành (Release Gate) lên môi trường Production. |
