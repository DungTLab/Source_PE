# Context Diagram — Software Testing Management System

## Mermaid Code

```mermaid
flowchart LR
    QA उसमेंManager["Test Lead / QA Manager"]
    TestEngineer["QA / Test Engineer"]
    SoftwareDeveloper["Software Developer"]
    ProductManager["Product Owner / Manager"]

    AutomationEngine["Automation Test Runner (Selenium/Playwright)"]
    RequirementsTracker["Requirement Tracker (Jira/Azure DevOps)"]
    CICDPipeline["CI/CD Pipeline Engine"]
    DefectTracker["Defect & Bug Tracker Engine"]
    LoadTestRunner["Performance Load Test Engine (JMeter/k6)"]

    TestingSystem(("Software Testing Management System"))

    QA उसमेंManager -->|"submits test strategies & quality gate rules"| TestingSystem
    TestingSystem -->|"returns test pass rate & quality dashboards"| QA उसमेंManager

    TestEngineer -->|"authors test cases & executes test runs"| TestingSystem
    TestingSystem -->|"assigns test suites & provides execution logs"| TestEngineer

    SoftwareDeveloper -->|"receives bug verification tasks"| TestingSystem
    TestingSystem -->|"notifies defect repro steps & failed test cases"| SoftwareDeveloper

    ProductManager -->|"queries requirement coverage & release readiness"| TestingSystem
    TestingSystem -->|"returns requirement traceability matrix"| ProductManager

    RequirementsTracker -->|"provides user stories & acceptance criteria"| TestingSystem
    TestingSystem -->|"syncs requirement coverage mapping"| RequirementsTracker

    AutomationEngine -->|"pushes automated test execution results"| TestingSystem
    TestingSystem -->|"triggers automated test suite execution"| AutomationEngine

    CICDPipeline -->|"sends build release hooks"| TestingSystem
    TestingSystem -->|"returns build quality gate pass/fail status"| CICDPipeline

    TestingSystem -->|"creates & syncs defect tickets"| DefectTracker
    DefectTracker -->|"returns defect status & resolution updates"| TestingSystem

    LoadTestRunner -->|"pushes performance latency & RPS metrics"| TestingSystem
```

## Actor & Interaction Table | Bảng Actor & Tương tác

| # | Actor | Actor Type | Data Sent TO System | Data Received FROM System | Notes |
|---|-------|------------|---------------------|---------------------------|-------|
| 1 | Test Lead / QA Manager | Primary | Test strategies, test plan targets, quality gate thresholds | Quality dashboards, test execution velocity, team productivity | Manages overall QA process and release readiness |
| 2 | QA / Test Engineer | Primary | Test case steps, preconditions, expected results, execution statuses | Assigned test suites, execution runs, bug template forms | Authors and executes manual/automated tests |
| 3 | Software Developer | Primary | Bug fix status, verification requests, code fix notes | Defect reproduction steps, failed test case logs | Fixes reported software defects |
| 4 | Product Owner / Manager | Primary | Requirement acceptance criteria queries, release target queries | Requirements traceability matrix (RTM), coverage reports | Ensures product requirements are verified |
| 5 | Requirement Tracker | Supporting | User story IDs, feature acceptance criteria, release epics | Test case mapping links, requirement test status | Systems like Jira, Azure DevOps |
| 6 | Automation Test Runner | Supporting | JUnit/TestNG XML reports, pass/fail status, execution logs | Automated test suite triggers, test environment config | Tools like Selenium, Playwright, Cypress, Appium |
| 7 | CI/CD Pipeline Engine | Supporting | Build release Webhooks, deployment candidate tags | Build quality gate pass/fail status, test summary | Automation engines like Jenkins, GitHub Actions |
| 8 | Defect & Bug Tracker | Supporting | Defect status updates, developer assignment changes | Auto-generated defect tickets, reproduction logs | Bug tracking platforms (Jira Bugs, Bugzilla) |
| 9 | Performance Load Test Engine | Supporting | Response latency metrics, throughput RPS, concurrency graphs | Performance test triggers, load profile parameters | Tools like Apache JMeter, k6, Locust |

## System Boundary Description | Mô tả Scope Hệ thống

Hệ thống **Software Testing Management System (Test Management Platform)** quản lý tập trung toàn bộ các hoạt động kiểm thử phần mềm từ thiết kế kịch bản test, thực thi kiểm thử thủ công/tự động, đến theo dõi vết bug và báo cáo chất lượng phát hành.

- **Phạm vi bên trong hệ thống (In-Scope)**:
  - Quản lý danh mục Kế hoạch kiểm thử (Test Plan), Bộ kịch bản (Test Suite), Kịch bản chi tiết (Test Case) và các bước kiểm thử (Test Steps).
  - Điều phối các đợt thực thi kiểm thử (Test Execution Runs) cho kiểm thử thủ công và tự động.
  - Tích hợp nhận báo cáo kết quả kiểm thử tự động (JUnit XML, Allure) từ các Framework Selenium/Playwright/Cypress.
  - Xây dựng ma trận truy vết yêu cầu (Requirements Traceability Matrix - RTM) kết nối User Story -> Test Case -> Defect -> Build Version.

- **Bên ngoài phạm vi hệ thống (Out-of-Scope)**:
  - Trực tiếp chạy mã lệnh điều khiển trình duyệt Web/Mobile (do Selenium/Playwright runner đảm nhận).
  - Trực tiếp tạo tải trọng giả lập hàng triệu user (do JMeter/k6 thực hiện).
  - Trực tiếp quản lý yêu cầu gốc (thuộc Jira / Azure DevOps).
