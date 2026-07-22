# Context Diagram — Microservices Registry & Management System

## Mermaid Code

```mermaid
flowchart LR
    MicroserviceArchitect["Microservice Architect"]
    DevOpsSpecialist["DevOps Specialist"]
    SoftwareEngineer["Software Engineer"]
    APIConsumerApp["API Consumer App"]

    KubernetesCluster["Kubernetes Cluster"]
    ConsulEurekaRegistry["Consul / Eureka Registry"]
    PrometheusTelemetry["Prometheus Telemetry"]
    IstioServiceMesh["Istio Service Mesh"]
    AuditLogger["Audit Logger"]

    SystemNode(("Microservices Registry & Management System"))

    MicroserviceArchitect -->|"submits management requests & policies"| SystemNode
    SystemNode -->|"returns system status & analytics reports"| MicroserviceArchitect

    DevOpsSpecialist -->|"interacts with self-service operations"| SystemNode
    SystemNode -->|"provides real-time processing results"| DevOpsSpecialist

    SoftwareEngineer -->|"configures operational rules & data"| SystemNode
    SystemNode -->|"returns execution logs & alerts"| SoftwareEngineer

    APIConsumerApp -->|"audits compliance & security logs"| SystemNode
    SystemNode -->|"exports compliance audit records"| APIConsumerApp

    KubernetesCluster -->|"provides integration payloads & telemetry"| SystemNode
    SystemNode -->|"dispatches API requests & sync events"| KubernetesCluster

    ConsulEurekaRegistry -->|"authenticates user credentials"| SystemNode
    SystemNode -->|"queries identity & role memberships"| ConsulEurekaRegistry

    SystemNode -->|"exports financial & inventory data"| PrometheusTelemetry
    SystemNode -->|"triggers emergency alert notifications"| IstioServiceMesh
    SystemNode -->|"streams audit events & compliance data"| AuditLogger
```

## Actor & Interaction Table | Bảng Actor & Tương tác

| # | Actor | Actor Type | Data Sent TO System | Data Received FROM System | Notes |
|---|-------|------------|---------------------|---------------------------|-------|
| 1 | Microservice Architect | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Microservice Architect role |
| 2 | DevOps Specialist | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | DevOps Specialist role |
| 3 | Software Engineer | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Software Engineer role |
| 4 | API Consumer App | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | API Consumer App role |
| 5 | Kubernetes Cluster | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Kubernetes Cluster role |
| 6 | Consul / Eureka Registry | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Consul / Eureka Registry role |
| 7 | Prometheus Telemetry | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Prometheus Telemetry role |
| 8 | Istio Service Mesh | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Istio Service Mesh role |
| 9 | Audit Logger | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Audit Logger role |

## System Boundary Description | Mô tả Scope Hệ thống

Hệ thống **Microservices Registry & Management System** (Hệ thống Đăng ký và Quản lý Microservices) được thiết kế nhằm quản lý tập trung và tự động hóa các quy trình vận hành CNTT cốt lõi trong doanh nghiệp.

- **Phạm vi bên trong hệ thống (In-Scope)**:
  - Quản lý dữ liệu nghiệp vụ trung tâm, tự động hóa quy trình theo chính sách doanh nghiệp.
  - Phân quyền người dùng chi tiết, theo dõi lịch sử thao tác và xuất báo cáo tuân thủ (ISO/SOC2).
  - Tích hợp phát hiện sự cố, gửi cảnh báo tức thì và kết nối dữ liệu hai chiều.

- **Bên ngoài phạm vi hệ thống (Out-of-Scope)**:
  - Trực tiếp quản lý hạ tầng phần cứng máy chủ vật lý.
  - Trực tiếp xử lý xác thực mật khẩu người dùng gốc (do Identity Provider đảm nhận).
