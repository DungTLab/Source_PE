# Swimlane Diagram — Software Testing Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["QA / Test Engineer"]
        Q1["Author Test Cases & Define Expected Results"]
        Q2["Trigger Execution Run or Run Manual Test"]
        Q3["Attach Screenshot Evidence & Mark Failed Step"]
        Q4["Verify Fixed Bug & Close Test Case"]
    end

    subgraph Lane2["Software Testing Management System"]
        SYS1["Link Test Cases to Jira Requirements"]
        SYS2["Ingest Test Execution Results"]
        SYS3{"Did All Test Steps Pass?"}
        SYS4["Auto-Create Bug Ticket & Link to Story"]
        SYS5["Update Pass Rate & Generate Traceability Matrix"]
    end

    subgraph Lane3["Automation Test Runner"]
        AUT1["Execute Selenium / Cypress Scripts"]
        AUT2["Export JUnit XML / JSON Report File"]
    end

    subgraph Lane4["Software Developer"]
        DEV1["Receive Bug Ticket & Repro Logs"]
        DEV2["Fix Code Defect & Submit Re-test Request"]
    end

    Finish(["End"])

    Start --> Q1 --> SYS1 --> Q2
    
    Q2 -->|"Manual Run"| Q3 --> SYS3
    Q2 -->|"Automation Run"| AUT1 --> AUT2 --> SYS2 --> SYS3

    SYS3 -->|"No - Failed Step"| SYS4 --> DEV1 --> DEV2 --> Q4 --> SYS5 --> Finish
    SYS3 -->|"Yes"| SYS5 --> Finish
```

## Flow Description | Mô tả luồng xử lý

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | QA / Test Engineer | Thiết kế kịch bản test và kết quả mong đợi, kích hoạt lượt chạy test thủ công/tự động, đính kèm bằng chứng ảnh lỗi và xác nhận đóng bug sau khi dev đã sửa. |
| 2 | Software Testing Management System | Liên kết kịch bản test với yêu cầu Jira, tiếp nhận file kết quả tự động, tự động mở ticket bug khi test thất bại và cập nhật tỷ lệ pass rate/ma trận RTM. |
| 3 | Automation Test Runner | Thực thi kịch bản mã lệnh tự động (Selenium/Cypress), kiểm tra các bước giao diện/API và trích xuất file báo cáo định dạng chuẩn XML/JSON. |
| 4 | Software Developer | Tiếp nhận thông báo bug kèm các bước tái hiện và bằng chứng ảnh, tiến hành sửa lỗi trong mã nguồn và yêu cầu QA kiểm thử lại. |
