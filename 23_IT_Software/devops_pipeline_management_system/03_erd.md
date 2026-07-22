# Conceptual ERD — DevOps Pipeline Management System

## Mermaid Code

```mermaid
erDiagram
    GIT_REPOSITORY {
        int repo_id PK
        string repo_name
        string repo_url
        string default_branch
        string webhook_secret
        boolean is_active
    }

    PIPELINE {
        int pipeline_id PK
        int repo_id FK
        string pipeline_name
        string yaml_config_path
        string trigger_event
        boolean is_enabled
        datetime created_at
    }

    PIPELINE_STAGE {
        int stage_id PK
        int pipeline_id FK
        string stage_name
        int execution_order
        boolean is_manual_approval
    }

    PIPELINE_RUN {
        int run_id PK
        int pipeline_id FK
        int run_number
        string commit_sha
        string branch_name
        string triggered_by
        string run_status
        datetime started_at
        datetime finished_at
    }

    JOB_STEP {
        int step_id PK
        int run_id FK
        int stage_id FK
        string step_name
        string runner_node
        string step_status
        int exit_code
        datetime execution_time
    }

    BUILD_ARTIFACT {
        int artifact_id PK
        int run_id FK
        string artifact_name
        string artifact_type
        string storage_path
        int size_bytes
        string image_digest
    }

    SECRET_VARIABLE {
        int secret_id PK
        int pipeline_id FK
        string key_name
        string encrypted_value
        string environment_scope
        boolean is_masked
    }

    ENVIRONMENT {
        int env_id PK
        string env_name
        string cluster_endpoint
        string namespace
        string status
    }

    DEPLOYMENT_RECORD {
        int deploy_id PK
        int run_id FK
        int env_id FK
        string deployed_by
        string image_tag
        string deployment_status
        datetime deployed_at
    }

    SECURITY_SCAN_REPORT {
        int report_id PK
        int run_id FK
        int critical_count
        int high_count
        int medium_count
        string scan_status
        datetime scanned_at
    }

    GIT_REPOSITORY ||--o{ PIPELINE : "triggers"
    PIPELINE ||--o{ PIPELINE_STAGE : "contains"
    PIPELINE ||--o{ PIPELINE_RUN : "executes"
    PIPELINE ||--o{ SECRET_VARIABLE : "uses"
    PIPELINE_RUN ||--o{ JOB_STEP : "runs"
    PIPELINE_STAGE ||--o{ JOB_STEP : "groups"
    PIPELINE_RUN ||--o{ BUILD_ARTIFACT : "produces"
    PIPELINE_RUN ||--o{ SECURITY_SCAN_REPORT : "generates"
    PIPELINE_RUN ||--o{ DEPLOYMENT_RECORD : "initiates"
    ENVIRONMENT ||--o{ DEPLOYMENT_RECORD : "targets"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|-------------------|
| 1 | GIT_REPOSITORY | Kho mã nguồn Git | Thông tin lưu trữ và cấu hình kết nối Webhook với kho mã nguồn | repo_id (PK), repo_name, repo_url, default_branch, webhook_secret | Triggers PIPELINE |
| 2 | PIPELINE | Quy trình CI/CD | Định nghĩa cấu hình quy trình gồm file YAML, quy tắc kích hoạt và môi trường | pipeline_id (PK), repo_id (FK), pipeline_name, yaml_config_path | Belongs to GIT_REPOSITORY, contains STAGE, executes RUN, uses SECRET |
| 3 | PIPELINE_STAGE | Công đoạn Pipeline | Định nghĩa các công đoạn trong quy trình (Build, Test, Security, Deploy) | stage_id (PK), pipeline_id (FK), stage_name, execution_order | Belongs to PIPELINE, groups JOB_STEP |
| 4 | PIPELINE_RUN | Lượt Chạy Pipeline | Ghi nhận thông tin chi tiết từng đợt thực thi pipeline (Commit SHA, trạng thái, thời gian) | run_id (PK), pipeline_id (FK), run_number, commit_sha, run_status | Belongs to PIPELINE, runs JOB_STEP, produces ARTIFACT, initiates DEPLOYMENT |
| 5 | JOB_STEP | Bước Thực thi Công việc | Chi tiết từng bước lệnh shell được chạy trên runner node | step_id (PK), run_id (FK), stage_id (FK), step_name, runner_node, step_status | Belongs to PIPELINE_RUN and PIPELINE_STAGE |
| 6 | BUILD_ARTIFACT | Sản phẩm Đóng gói | File binary, container image digest hoặc gói Helm được tạo ra từ đợt build | artifact_id (PK), run_id (FK), artifact_name, artifact_type, image_digest | Produced by PIPELINE_RUN |
| 7 | SECRET_VARIABLE | Biến Mã hóa Bí mật | Biến môi trường, token API hoặc mật khẩu được mã hóa an toàn | secret_id (PK), pipeline_id (FK), key_name, encrypted_value, is_masked | Used by PIPELINE |
| 8 | ENVIRONMENT | Môi trường Triển khai | Thông tin các cụm môi trường mục tiêu (Dev, Staging, Production) | env_id (PK), env_name, cluster_endpoint, namespace | Targets by DEPLOYMENT_RECORD |
| 9 | DEPLOYMENT_RECORD | Nhật ký Triển khai | Ghi nhận lịch sử triển khai container image lên các cụm môi trường | deploy_id (PK), run_id (FK), env_id (FK), image_tag, deployment_status | Initiated by PIPELINE_RUN, targets ENVIRONMENT |
| 10 | SECURITY_SCAN_REPORT | Báo cáo Quét Bảo mật | Kết quả phân tích lỗ hổng mã nguồn và container (CVE status) | report_id (PK), run_id (FK), critical_count, high_count, scan_status | Generated by PIPELINE_RUN |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | GIT_REPOSITORY | 1 to Many | PIPELINE | triggers | Một kho mã nguồn Git có thể sở hữu nhiều quy trình pipeline khác nhau. |
| 2 | PIPELINE | 1 to Many | PIPELINE_STAGE | contains | Một pipeline bao gồm nhiều công đoạn thực thi nối tiếp (Stage). |
| 3 | PIPELINE | 1 to Many | PIPELINE_RUN | executes | Một pipeline thực thi nhiều lượt chạy (Run) tương ứng từng đợt push code. |
| 4 | PIPELINE | 1 to Many | SECRET_VARIABLE | uses | Một pipeline sử dụng nhiều biến bí mật mã hóa cho công việc. |
| 5 | PIPELINE_RUN | 1 to Many | JOB_STEP | runs | Một lượt chạy pipeline thực thi nhiều bước lệnh shell chi tiết. |
| 6 | PIPELINE_STAGE | 1 to Many | JOB_STEP | groups | Một công đoạn gom nhóm các bước lệnh thuộc công đoạn đó. |
| 7 | PIPELINE_RUN | 1 to Many | BUILD_ARTIFACT | produces | Một lượt chạy có thể đóng gói tạo ra nhiều sản phẩm Artifact/Docker Image. |
| 8 | PIPELINE_RUN | 1 to 1 | SECURITY_SCAN_REPORT | generates | Mỗi lượt chạy tạo ra 1 bản báo cáo quét lỗ hổng bảo mật. |
| 9 | PIPELINE_RUN | 1 to Many | DEPLOYMENT_RECORD | initiates | Lượt chạy pipeline kích hoạt đợt triển khai sản phẩm lên các môi trường. |
| 10 | ENVIRONMENT | 1 to Many | DEPLOYMENT_RECORD | targets | Một môi trường (Staging/Production) tiếp nhận nhiều lượt triển khai phiên bản. |
