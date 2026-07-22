# Swimlane Diagram — Configuration Management System (CMDB)

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["DevOps / Change Manager"]
        DEV1["Submit Change Request RFC & Target CI"]
        DEV2["Review CI Blast Radius & Impact Map"]
        DEV3["Execute Approved Change & Lock Baseline"]
    end

    subgraph Lane2["CMDB System Engine"]
        SYS1["Traverse CI Relationship Tree"]
        SYS2["Calculate Upstream Business Service Impact"]
        SYS3{"Contains High Criticality Services?"}
        SYS4["Compare Live Config vs Locked Baseline"]
        SYS5{"Unauthorized Drift Detected?"}
        SYS6["Record Verified Change & Update CI Attributes"]
    end

    subgraph Lane3["IT Service Manager"]
        M1["Review CAB Approval Request & Blast Radius"]
        M2["Sign-off Change Advisory Board Approval"]
    end

    subgraph Lane4["IT Security Auditor"]
        SEC1["Receive Unauthorized Drift Alert"]
        SEC2["Initiate Incident Investigation & Audit Log"]
    end

    Finish(["End"])

    Start --> DEV1 --> SYS1 --> SYS2 --> SYS3
    
    SYS3 -->|"Yes"| M1 --> M2 --> DEV2
    SYS3 -->|"No"| DEV2

    DEV2 --> DEV3 --> SYS4 --> SYS5

    SYS5 -->|"Yes - Unauthorized"| SEC1 --> SEC2 --> Finish
    SYS5 -->|"No - Valid Change"| SYS6 --> Finish
```

## Flow Description | Mô tả luồng xử lý

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | DevOps / Change Manager | Khởi tạo yêu cầu thay đổi (RFC), xem xét báo cáo ma trận ảnh hưởng (Blast Radius), thực hiện thay đổi và yêu cầu đóng vết bản mẫu (Baseline). |
| 2 | CMDB System Engine | Tự động duyệt cây quan hệ CI, tính toán các dịch vụ bị ảnh hưởng, so sánh trạng thái thực tế với baseline và phát hiện các biến đổi trái phép (Drift). |
| 3 | IT Service Manager | Xem xét báo cáo mức độ ảnh hưởng của thay đổi, chủ trì Hội đồng Phê duyệt Thay đổi (CAB) và xác nhận đồng ý triển khai. |
| 4 | IT Security Auditor | Tiếp nhận cảnh báo khi hệ thống phát hiện thay đổi cấu hình CI trái phép (không có RFC phê duyệt) và tiến hành kiểm toán bảo mật. |
