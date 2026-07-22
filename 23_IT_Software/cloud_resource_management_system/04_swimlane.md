# Swimlane Diagram — Cloud Resource Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Enterprise End User"]
        U1["Request VM Instance from Portal"]
        U2["Fill Provisioning Form & Select Spec"]
        U3["Receive Instance IP & Access Key"]
        U4["Use VM Instance for Workloads"]
    end

    subgraph Lane2["Cloud RMS Platform"]
        S1["Validate Department Budget Quota"]
        S2{"Quota Available & Policy Compliant?"}
        S3["Format IaC Provisioning Payload"]
        S4["Record Active Instance Metadata & Tags"]
        S5["Monitor Daily Spending & Security"]
    end

    subgraph Lane3["Multi-Cloud API Gateway"]
        C1["Dispatch API Call to AWS / Azure / GCP"]
        C2["Provision VM, Storage & IP Endpoint"]
        C3["Return Instance Telemetry & Bill Logs"]
    end

    subgraph Lane4["FinOps & Security Manager"]
        M1["Audit Budget Breach & S3 Security"]
        M2{"Spotted Idle VM or Open Port?"}
        M3["Enforce Auto-Shutdown or Access Revoke"]
    end

    Finish(["End"])

    Start --> U1 --> U2 --> S1 --> S2
    
    S2 -->|"No - Quota Exceeded"| Finish
    S2 -->|"Yes"| S3 --> C1 --> C2 --> C3 --> S4 --> U3 --> U4

    S4 --> S5 --> M1 --> M2
    M2 -->|"Yes"| M3 --> Finish
    M2 -->|"No"| Finish
```

## Flow Description | Mô tả luồng xử lý

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Enterprise End User | Khởi tạo yêu cầu máy chủ ảo qua cổng tự phục vụ, lựa chọn cấu hình phù hợp, tiếp nhận thông tin kết nối (IP/SSH key) và sử dụng cho công việc. |
| 2 | Cloud RMS Platform | Kiểm tra hạn mức ngân sách phòng ban, kiểm tra tính tuân thủ quy tắc an ninh, đóng gói yêu cầu dạng IaC, lưu vết tài nguyên và giám sát hoạt động. |
| 3 | Multi-Cloud API Gateway | Kết nối trực tiếp với API của AWS, Azure, GCP để khởi tạo hạ tầng thực tế (VM, Storage, Network) và trích xuất dữ liệu vận hành và hóa đơn. |
| 4 | FinOps & Security Manager | Kiểm soát báo cáo chi phí, phát hiện các máy chủ chạy ngầm không sử dụng (Idle VM) hoặc lỗ hổng bảo mật, thực hiện thu hồi hoặc tắt máy chủ tự động. |
