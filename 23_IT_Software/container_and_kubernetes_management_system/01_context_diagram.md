# Context Diagram — Container & Kubernetes Management System

## Mermaid Code

```mermaid
flowchart LR
    KubernetesAdministrator["Kubernetes Administrator"]
    DevOpsEngineer["DevOps Engineer"]
    CloudArchitect["Cloud Architect"]
    SecurityAuditor["Security Auditor"]

    KubernetesAPIServer["Kubernetes API Server"]
    HelmChartRegistry["Helm Chart Registry"]
    PrometheusMetrics["Prometheus Metrics"]
    IstioMesh["Istio Mesh"]
    SIEMPortal["SIEM Portal"]

    SystemNode(("Container & Kubernetes Management System"))

    KubernetesAdministrator -->|"submits management requests & policies"| SystemNode
    SystemNode -->|"returns system status & analytics reports"| KubernetesAdministrator

    DevOpsEngineer -->|"interacts with self-service operations"| SystemNode
    SystemNode -->|"provides real-time processing results"| DevOpsEngineer

    CloudArchitect -->|"configures operational rules & data"| SystemNode
    SystemNode -->|"returns execution logs & alerts"| CloudArchitect

    SecurityAuditor -->|"audits compliance & security logs"| SystemNode
    SystemNode -->|"exports compliance audit records"| SecurityAuditor

    KubernetesAPIServer -->|"provides integration payloads & telemetry"| SystemNode
    SystemNode -->|"dispatches API requests & sync events"| KubernetesAPIServer

    HelmChartRegistry -->|"authenticates user credentials"| SystemNode
    SystemNode -->|"queries identity & role memberships"| HelmChartRegistry

    SystemNode -->|"exports financial & inventory data"| PrometheusMetrics
    SystemNode -->|"triggers emergency alert notifications"| IstioMesh
    SystemNode -->|"streams audit events & compliance data"| SIEMPortal
```

## Actor & Interaction Table | Bảng Actor & Tương tác

| # | Actor | Actor Type | Data Sent TO System | Data Received FROM System | Notes |
|---|-------|------------|---------------------|---------------------------|-------|
| 1 | Kubernetes Administrator | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Kubernetes Administrator role |
| 2 | DevOps Engineer | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | DevOps Engineer role |
| 3 | Cloud Architect | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Cloud Architect role |
| 4 | Security Auditor | Primary | Operational requests, policy configurations, audit queries | Status updates, performance reports, audit results | Security Auditor role |
| 5 | Kubernetes API Server | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Kubernetes API Server role |
| 6 | Helm Chart Registry | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Helm Chart Registry role |
| 7 | Prometheus Metrics | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Prometheus Metrics role |
| 8 | Istio Mesh | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | Istio Mesh role |
| 9 | SIEM Portal | Supporting | Integration payloads, auth claims, event logs | API sync responses, verification tokens | SIEM Portal role |

## System Boundary Description | Mô tả Scope Hệ thống

Hệ thống **Container & Kubernetes Management System** (Hệ thống Quản lý Container và Kubernetes) được thiết kế nhằm quản lý tập trung và tự động hóa các quy trình vận hành CNTT cốt lõi trong doanh nghiệp.

- **Phạm vi bên trong hệ thống (In-Scope)**:
  - Quản lý dữ liệu nghiệp vụ trung tâm, tự động hóa quy trình theo chính sách doanh nghiệp.
  - Phân quyền người dùng chi tiết, theo dõi lịch sử thao tác và xuất báo cáo tuân thủ (ISO/SOC2).
  - Tích hợp phát hiện sự cố, gửi cảnh báo tức thì và kết nối dữ liệu hai chiều.

- **Bên ngoài phạm vi hệ thống (Out-of-Scope)**:
  - Trực tiếp quản lý hạ tầng phần cứng máy chủ vật lý.
  - Trực tiếp xử lý xác thực mật khẩu người dùng gốc (do Identity Provider đảm nhận).
