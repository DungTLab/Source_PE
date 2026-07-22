# Swimlane Diagram — IoT Platform & Device Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["IoT Solutions Architect"]
        A1["Initiate Operation Request"]
        A2["Review Processing Parameters"]
        A3["Confirm Final Sign-off"]
    end

    subgraph Lane2["IoT Platform & Device Management System"]
        S1["Validate Input Data & Policy Rules"]
        S2{"Is Data Valid & Compliant?"}
        S3["Execute Automated Core Processing"]
        S4["Update Database Record & Audit Trail"]
    end

    subgraph Lane3["IoT Gateway Edge Node"]
        E1["Process Integration Payload"]
        E2["Return Processing Status Confirmation"]
    end

    subgraph Lane4["Security Specialist"]
        M1["Audit Event Log Summary"]
        M2["Approve Security & Compliance Verification"]
    end

    Finish(["End"])

    Start --> A1 --> S1 --> S2
    S2 -->|"No"| A2 --> A1
    S2 -->|"Yes"| S3 --> E1 --> E2 --> S4 --> M1 --> M2 --> A3 --> Finish
```

## Flow Description | Mô tả luồng xử lý

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | IoT Solutions Architect | Khởi tạo yêu cầu tác vụ, xem xét các tham số nghiệp vụ và xác nhận hoàn tất quy trình. |
| 2 | IoT Platform & Device Management System | Kiểm tra tính hợp lệ của dữ liệu đầu vào, thực thi xử lý tự động, cập nhật cơ sở dữ liệu và lưu vết kiểm toán. |
| 3 | IoT Gateway Edge Node | Tiếp nhận payload tích hợp dịch vụ, xử lý phản hồi và trả về trạng thái cho hệ thống trung tâm. |
| 4 | Security Specialist | Giám sát nhật ký sự kiện, kiểm tra tính tuân thủ an ninh và phê duyệt báo cáo kiểm toán. |
