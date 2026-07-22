# Swimlane Diagram — DevOps Pipeline Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Software Developer"]
        DEV1["Commit & Push Code to Git"]
        DEV2["Inspect Real-time Console Logs"]
        DEV3["Fix Broken Build or Security Flaw"]
    end

    subgraph Lane2["DevOps Pipeline Engine"]
        SYS1["Receive Webhook Event"]
        SYS2["Allocate Runner & Build Docker Image"]
        SYS3{"Did Unit Tests & Compilation Pass?"}
        SYS4["Push Image to Registry & Trigger Gate"]
        SYS5["Deploy Image to Kubernetes Cluster"]
    end

    subgraph Lane3["Security & Quality Gate"]
        SEC1["Run Static Analysis & Trivy CVE Scan"]
        SEC2{"Satisfies Security Policy Threshold?"}
    end

    subgraph Lane4["Release Manager"]
        REL1["Review Gate Approval Request"]
        REL2{"Approve Production Deploy?"}
    end

    Finish(["End"])

    Start --> DEV1 --> SYS1 --> SYS2 --> SYS3
    
    SYS3 -->|"No"| DEV2 --> DEV3 --> DEV1
    SYS3 -->|"Yes"| SEC1 --> SEC2

    SEC2 -->|"No - Critical CVE"| DEV3
    SEC2 -->|"Yes"| SYS4 --> REL1 --> REL2

    REL2 -->|"No - Rejected"| Finish
    REL2 -->|"Yes - Approved"| SYS5 --> Finish
```

## Flow Description | Mô tả luồng xử lý

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Software Developer | Lập trình và đẩy mã nguồn lên Git repository, xem log console thực thi trực tiếp, và sửa lỗi biên dịch hoặc lỗi bảo mật khi pipeline thất bại. |
| 2 | DevOps Pipeline Engine | Bắt sự kiện Webhook tự động, cấp phát runner thực thi biên dịch ứng dụng, tạo container image, đẩy sản phẩm lên Registry và triển khai lên cụm Kubernetes. |
| 3 | Security & Quality Gate | Thực thi quét lỗ hổng bảo mật ứng dụng và container (SAST/CVE scan), so sánh với ngưỡng quy định và chặn triển khai nếu phát hiện lỗ hổng nghiêm trọng. |
| 4 | Release Manager | Xem xét báo cáo tuân thủ quy trình, thực hiện phê duyệt thủ công cổng phát hành (Approval Gate) trước khi hệ thống cập nhật môi trường Production. |
