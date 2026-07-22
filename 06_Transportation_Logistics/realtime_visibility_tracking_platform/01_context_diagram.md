# Context Diagram — Real-time Visibility & Tracking Platform

## Mermaid Code

```mermaid
flowchart LR
    Actor_P1["Fleet Manager"]
    Actor_P2["Vehicle Driver"]
    Actor_P3["Logistics Dispatcher"]
    Actor_P4["System Administrator"]

    Actor_S1["GPS Telematics Gateway"]
    Actor_S2["Map & Routing API"]
    Actor_S3["Notification Gateway"]
    Actor_R1["Department of Transportation Portal"]

    System((" Real-time Visibility & Tracking Platform "))

    Actor_P1 -->|"submits operational request"| System
    System -->|"returns status & confirmation"| Actor_P1

    Actor_P2 -->|"sends execution updates"| System
    System -->|"dispatches assigned tasks"| Actor_P2

    Actor_P3 -->|"configures rules & schedules"| System
    System -->|"provides operational metrics"| Actor_P3

    Actor_P4 -->|"manages user access & system configuration"| System
    System -->|"returns system health & audit logs"| Actor_P4

    Actor_S1 -->|"streams real-time telemetry data"| System
    System -->|"sends command & sync requests"| Actor_S1

    System -->|"sends payment or event payloads"| Actor_S2
    Actor_S2 -->|"returns transaction verification"| System

    System -->|"dispatches push notifications & alerts"| Actor_S3
    Actor_S3 -->|"returns message delivery status"| System

    System -->|"exports compliance & regulatory reports"| Actor_R1
```

## Actor & Interaction Table | Bảng Actor & Tương tác

| # | Actor | Actor Type | Data Sent TO System | Data Received FROM System | Notes |
|---|-------|------------|---------------------|---------------------------|-------|
| 1 | Fleet Manager | Primary | Submits operational booking/request, updates preferences, inputs criteria | Real-time status updates, execution confirmation, digital receipt | Main service requester / operator |
| 2 | Vehicle Driver | Primary | Task progress updates, GPS location data, exception notes | Assigned dispatch tasks, route details, schedule updates | Field execution personnel / vehicle unit |
| 3 | Logistics Dispatcher | Primary | Workflow configurations, dispatch rules, threshold parameters | Operational dashboards, SLA breach alerts, KPI analytics | Operational management & planning role |
| 4 | System Administrator | Primary | System permissions, master data, system parameters | Audit logs, security alerts, diagnostic status | System administrator |
| 5 | GPS Telematics Gateway | Supporting | Sensor telemetry, location coordinates, status pings | Synchronization requests, configuration commands | External IoT / sensor / tracking gateway |
| 6 | Map & Routing API | Supporting | Transaction approval tokens, status webhooks | Payment requests, billing payloads, API queries | Financial / external integration partner |
| 7 | Notification Gateway | Supporting | Delivery verification receipts, bounce logs | Email / SMS / Push alert payloads | Communication gateway service |
| 8 | Department of Transportation Portal | Regulatory | Compliance guidelines, regulatory standards | Audit logs, safety compliance reports, inspection records | Government / Industry oversight agency |

## System Boundary Description | Mô tả Scope Hệ thống

Hệ thống **Real-time Visibility & Tracking Platform (Nền tảng Theo dõi Thời gian thực)** đóng vai trò là nền tảng điều hành trung tâm cho các hoạt động nghiệp vụ trong lĩnh vực vận tải & logistics.

- **Phạm vi bên trong hệ thống (In-Scope)**:
  - Tiếp nhận, phân luồng và quản lý toàn bộ vòng đời của giao dịch/lệnh vận hành từ khởi tạo đến hoàn thành.
  - Tự động hóa tính toán lộ trình, điều phối tài nguyên, theo dõi trạng thái thời gian thực và quản lý tài xế/phương tiện/tài sản.
  - Cung cấp cổng giao tiếp người dùng, cấu hình quy tắc nghiệp vụ, giám sát SLA và lập báo cáo phân tích hiệu năng.
  - Lưu trữ nhật ký kiểm toán, quản lý phân quyền theo vai trò và đồng bộ dữ liệu với các đối tác liên quan.

- **Bên ngoài phạm vi hệ thống (Out-of-Scope)**:
  - Trực tiếp sản xuất thiết bị phần cứng GPS/IoT hoặc duy trì hạ tầng viễn thông di động.
  - Xử lý các giao dịch ngân hàng gốc mà phải thông qua Cổng thanh toán (Payment Gateway) đối tác.
  - Đảm nhận chức năng kế toán tổng hợp cấp doanh nghiệp (thuộc phạm vi của hệ thống ERP tổng).
