# Conceptual ERD — Software Development Lifecycle Management System

## Mermaid Code

```mermaid
erDiagram
    PROJECT {
        int project_id PK
        string project_key
        string project_name
        string lead_owner
        boolean is_active
        datetime created_at
    }

    REQUIREMENT_EPIC {
        int epic_id PK
        int project_id FK
        string epic_title
        string business_goal
        string status
        datetime target_completion
    }

    SPRINT {
        int sprint_id PK
        int project_id FK
        string sprint_name
        datetime start_date
        datetime end_date
        int capacity_points
        string status
    }

    WORK_ITEM {
        int item_id PK
        string item_key
        int project_id FK
        int epic_id FK
        int sprint_id FK
        int assignee_id FK
        string item_type
        string title
        int story_points
        string priority
        string status
    }

    CODE_COMMIT {
        int commit_id PK
        int item_id FK
        string commit_hash
        string repository_name
        string branch_name
        string author_email
        datetime committed_at
    }

    PULL_REQUEST {
        int pr_id PK
        int item_id FK
        int pr_number
        string source_branch
        string target_branch
        string pr_status
        int review_approval_count
        datetime merged_at
    }

    BUILD_PIPELINE {
        int build_id PK
        int pr_id FK
        string build_number
        string commit_hash
        string build_status
        int duration_seconds
        string artifact_tag
        datetime executed_at
    }

    TEST_SUITE {
        int suite_id PK
        int project_id FK
        string suite_name
        string test_type
        int total_test_cases
        int last_pass_count
    }

    DEFECT_BUG {
        int bug_id PK
        int item_id FK
        int suite_id FK
        string bug_key
        string severity
        string reproduction_steps
        string status
    }

    RELEASE_DEPLOYMENT {
        int release_id PK
        int project_id FK
        string version_tag
        string release_name
        string environment
        string gate_approval_status
        datetime deployed_at
    }

    PROJECT ||--o{ REQUIREMENT_EPIC : "defines"
    PROJECT ||--o{ SPRINT : "schedules"
    PROJECT ||--o{ WORK_ITEM : "contains"
    REQUIREMENT_EPIC ||--o{ WORK_ITEM : "groups"
    SPRINT ||--o{ WORK_ITEM : "executes"
    WORK_ITEM ||--o{ CODE_COMMIT : "linked_to"
    WORK_ITEM ||--o{ PULL_REQUEST : "triggers"
    PULL_REQUEST ||--o{ BUILD_PIPELINE : "validates_by"
    PROJECT ||--o{ TEST_SUITE : "tests"
    WORK_ITEM ||--o{ DEFECT_BUG : "spawns"
    TEST_SUITE ||--o{ DEFECT_BUG : "detects"
    PROJECT ||--o{ RELEASE_DEPLOYMENT : "releases"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|-------------------|
| 1 | PROJECT | Dự án Phần mềm | Đại diện cho dự án phần mềm tổng thể, chứa toàn bộ epic, sprint và work items | project_id (PK), project_key, project_name, lead_owner | Defines REQUIREMENT_EPIC, schedules SPRINT, releases DEPLOYMENT |
| 2 | REQUIREMENT_EPIC | Epic Yêu cầu Nghiệp vụ | Tính năng lớn cấp Epic gom nhóm các User Story liên quan | epic_id (PK), project_id (FK), epic_title, business_goal | Belongs to PROJECT, groups WORK_ITEM |
| 3 | SPRINT | Chu kỳ Phát triển (Sprint) | Vòng lặp thời gian (thường 2-4 tuần) để hoàn thành các mục tiêu phát triển | sprint_id (PK), project_id (FK), sprint_name, capacity_points | Belongs to PROJECT, executes WORK_ITEM |
| 4 | WORK_ITEM | Mục Công việc (Story/Task) | Đơn vị công việc chi tiết (User Story, Task, Sub-task) | item_id (PK), item_key, project_id (FK), epic_id (FK), sprint_id (FK) | Belongs to PROJECT/EPIC/SPRINT, linked to COMMIT/PR, spawns DEFECT_BUG |
| 5 | CODE_COMMIT | Git Commit Mã nguồn | Ghi nhận lượt commit mã nguồn từ Git được liên kết với ticket ID | commit_id (PK), item_id (FK), commit_hash, repository_name, branch_name | Linked to WORK_ITEM |
| 6 | PULL_REQUEST | Yêu cầu Merge Code (PR) | Yêu cầu review và merge mã nguồn từ branch phát triển vào branch chính | pr_id (PK), item_id (FK), pr_number, source_branch, target_branch | Triggered by WORK_ITEM, validated by BUILD_PIPELINE |
| 7 | BUILD_PIPELINE | Đường ống Build CI/CD | Ghi nhận thông tin thực thi build tự động, biên dịch code và đóng gói artifact | build_id (PK), pr_id (FK), build_number, build_status, artifact_tag | Validates PULL_REQUEST |
| 8 | TEST_SUITE | Bộ Kịch bản Kiểm thử | Tập hợp các test case kiểm thử tự động hoặc thủ công cho dự án | suite_id (PK), project_id (FK), suite_name, test_type, total_test_cases | Belongs to PROJECT, detects DEFECT_BUG |
| 9 | DEFECT_BUG | Lỗi Phần mềm (Defect/Bug) | Ghi nhận báo cáo lỗi phát sinh trong quá trình kiểm thử hoặc sản xuất | bug_id (PK), item_id (FK), suite_id (FK), bug_key, severity | Spawned by WORK_ITEM, detected by TEST_SUITE |
| 10 | RELEASE_DEPLOYMENT | Đợt Phát hành & Triển khai | Ghi nhận thông tin phiên bản phần mềm phát hành và trạng thái duyệt cổng release | release_id (PK), project_id (FK), version_tag, release_name, environment | Belongs to PROJECT |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | PROJECT | 1 to Many | REQUIREMENT_EPIC | defines | Một dự án định nghĩa nhiều Epic yêu cầu lớn. |
| 2 | PROJECT | 1 to Many | SPRINT | schedules | Một dự án lập kế hoạch cho nhiều chu kỳ Sprint phát triển. |
| 3 | PROJECT | 1 to Many | WORK_ITEM | contains | Một dự án chứa danh mục các Work Item (User Story/Task). |
| 4 | REQUIREMENT_EPIC | 1 to Many | WORK_ITEM | groups | Một Epic gom nhóm nhiều User Story chi tiết. |
| 5 | SPRINT | 1 to Many | WORK_ITEM | executes | Một Sprint thực thi một danh sách các Work Item đã cam kết. |
| 6 | WORK_ITEM | 1 to Many | CODE_COMMIT | linked_to | Một công việc có thể liên quan tới nhiều lượt Commit mã nguồn. |
| 7 | WORK_ITEM | 1 to Many | PULL_REQUEST | triggers | Một công việc mở ra một hoặc nhiều Pull Request để review code. |
| 8 | PULL_REQUEST | 1 to Many | BUILD_PIPELINE | validates_by | Mỗi Pull Request kích hoạt các đợt Build kiểm tra tự động. |
| 9 | PROJECT | 1 to Many | TEST_SUITE | tests | Một dự án có nhiều bộ kịch bản kiểm thử (Test Suites). |
| 10 | WORK_ITEM | 1 to Many | DEFECT_BUG | spawns | Một tính năng/User Story có thể phát sinh các Bug lỗi cần sửa. |
| 11 | TEST_SUITE | 1 to Many | DEFECT_BUG | detects | Một bộ kịch bản kiểm thử phát hiện các Bug lỗi phần mềm. |
| 12 | PROJECT | 1 to Many | RELEASE_DEPLOYMENT | releases | Một dự án thực hiện nhiều đợt đóng gói và phát hành (Release). |
