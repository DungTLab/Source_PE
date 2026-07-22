# Conceptual ERD — Grant Application & Management System

## Mermaid Code

```mermaid
erDiagram
    GRANT_PROGRAM {
        int program_id PK
        string program_name
        string category
        decimal total_budget_pool
        decimal max_award_limit
        datetime application_deadline
        string status
    }

    APPLICANT_ORG {
        int org_id PK
        string org_name
        string tax_id_ein
        string org_type
        string contact_email
        string verification_status
    }

    TAX_RECORD {
        int tax_record_id PK
        int org_id FK
        string tax_status_code
        datetime verification_date
        string tax_exempt_certificate_url
    }

    GRANT_APPLICATION {
        int application_id PK
        int program_id FK
        int org_id FK
        string project_title
        decimal requested_amount
        string status
        datetime submission_date
    }

    REVIEWER {
        int reviewer_id PK
        string full_name
        string email
        string expertise_domain
        string status
    }

    EVALUATION_SCORE {
        int evaluation_id PK
        int application_id FK
        int reviewer_id FK
        decimal total_score
        string recommendation
        datetime evaluation_date
    }

    GRANT_AWARD {
        int award_id PK
        int application_id FK
        decimal approved_amount
        datetime award_date
        datetime start_date
        datetime end_date
        string award_status
    }

    DISBURSEMENT_TRANCHE {
        int tranche_id PK
        int award_id FK
        int tranche_sequence
        decimal amount
        datetime scheduled_date
        string payout_status
    }

    MILESTONE_REPORT {
        int report_id PK
        int award_id FK
        string milestone_title
        datetime due_date
        datetime submission_date
        string review_status
    }

    EXPENSE_CLAIM {
        int claim_id PK
        int report_id FK
        int award_id FK
        decimal total_claimed_amount
        datetime claim_date
        string verification_status
    }

    COMPLIANCE_AUDIT {
        int audit_id PK
        int award_id FK
        string compliance_type
        string audit_result
        datetime audit_date
    }

    APPLICATION_REVIEWER {
        int application_id PK, FK
        int reviewer_id PK, FK
        datetime assigned_date
    }

    GRANT_PROGRAM ||--o{ GRANT_APPLICATION : "publishes"
    APPLICANT_ORG ||--o{ GRANT_APPLICATION : "submits"
    APPLICANT_ORG ||--|| TAX_RECORD : "verified_by"
    GRANT_APPLICATION ||--o{ EVALUATION_SCORE : "scored_in"
    REVIEWER ||--o{ EVALUATION_SCORE : "evaluates"
    GRANT_APPLICATION ||--|| GRANT_AWARD : "results_in"
    GRANT_AWARD ||--o{ DISBURSEMENT_TRANCHE : "schedules"
    GRANT_AWARD ||--o{ MILESTONE_REPORT : "tracks"
    MILESTONE_REPORT ||--o{ EXPENSE_CLAIM : "contains"
    GRANT_AWARD ||--o{ EXPENSE_CLAIM : "billed_against"
    GRANT_AWARD ||--o{ COMPLIANCE_AUDIT : "audited_in"
    GRANT_APPLICATION ||--o{ APPLICATION_REVIEWER : "assigned_to"
    REVIEWER ||--o{ APPLICATION_REVIEWER : "evaluates_apps"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|-------------------|
| 1 | GRANT_PROGRAM | Chương trình Tài trợ | Represents a specific grant opportunity call with total budget pool, eligibility criteria, and submission deadline. | program_id (PK), program_name, category, total_budget_pool, application_deadline | Publishes Applications |
| 2 | APPLICANT_ORG | Tổ chức Nộp đơn | Non-profit organization, research institute, or small business applying for grant funding. | org_id (PK), org_name, tax_id_ein, org_type, verification_status | Submits Applications, verified by Tax Record |
| 3 | TAX_RECORD | Hồ sơ Mã số Thuế | Official tax verification record confirming 501(c)(3) / tax-exempt status and legal registration. | tax_record_id (PK), org_id (FK), tax_status_code, tax_exempt_certificate_url | Verifies Applicant Org |
| 4 | GRANT_APPLICATION | Đơn Xin Tài trợ | Formal grant proposal submitted by an applicant organization for a specific grant program. | application_id (PK), program_id (FK), org_id (FK), project_title, requested_amount, status | Belongs to Grant Program & Applicant Org, scored in Evaluation Score, results in Grant Award |
| 5 | REVIEWER | Chuyên gia Đánh giá | External or internal domain expert assigned to review and score grant application dossiers. | reviewer_id (PK), full_name, email, expertise_domain | Evaluates Applications via Evaluation Score |
| 6 | EVALUATION_SCORE | Điểm Đánh giá | Numerical criteria scores, qualitative notes, and recommendation submitted by a peer reviewer. | evaluation_id (PK), application_id (FK), reviewer_id (FK), total_score, recommendation | Belongs to Application & Reviewer |
| 7 | GRANT_AWARD | Quyết định Cấp Vốn | Binding grant contract awarded to an application, defining approved amount and performance period. | award_id (PK), application_id (FK), approved_amount, award_date, award_status | Belongs to Application, schedules Tranches, tracks Milestone Reports & Audits |
| 8 | DISBURSEMENT_TRANCHE | Trực Đợt Giải ngân | Individual payment installment disbursed to awardee based on milestone achievements. | tranche_id (PK), award_id (FK), tranche_sequence, amount, payout_status | Belongs to Grant Award |
| 9 | MILESTONE_REPORT | Báo cáo Tiến độ | Periodic milestone progress deliverable submitted by grant recipient to verify performance. | report_id (PK), award_id (FK), milestone_title, due_date, review_status | Belongs to Grant Award, contains Expense Claims |
| 10 | EXPENSE_CLAIM | Yêu cầu Thanh toán | Itemized financial expense report submitted with receipts to account for grant expenditures. | claim_id (PK), report_id (FK), award_id (FK), total_claimed_amount, verification_status | Belongs to Milestone Report & Grant Award |
| 11 | COMPLIANCE_AUDIT | Kiểm toán Tuân thủ | Risk and financial audit record tracking grant recipient compliance with statutory rules. | audit_id (PK), award_id (FK), compliance_type, audit_result, audit_date | Audits Grant Award |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | GRANT_PROGRAM | one-to-many | GRANT_APPLICATION | publishes | A Grant Program receives multiple Grant Applications. |
| 2 | APPLICANT_ORG | one-to-many | GRANT_APPLICATION | submits | An Applicant Org can submit multiple Grant Applications over time. |
| 3 | APPLICANT_ORG | one-to-one | TAX_RECORD | verified_by | An Applicant Org is verified by a unique Tax Record. |
| 4 | GRANT_APPLICATION | one-to-many | EVALUATION_SCORE | scored_in | A Grant Application receives multiple peer review Evaluation Scores. |
| 5 | REVIEWER | one-to-many | EVALUATION_SCORE | evaluates | A Reviewer submits Evaluation Scores across assigned applications. |
| 6 | GRANT_APPLICATION | one-to-one | GRANT_AWARD | results_in | An approved Grant Application results in a formal Grant Award contract. |
| 7 | GRANT_AWARD | one-to-many | DISBURSEMENT_TRANCHE | schedules | A Grant Award schedules multiple payment Disbursement Tranches. |
| 8 | GRANT_AWARD | one-to-many | MILESTONE_REPORT | tracks | A Grant Award tracks periodic Milestone Reports. |
| 9 | MILESTONE_REPORT | one-to-many | EXPENSE_CLAIM | contains | A Milestone Report contains itemized Expense Claims. |
| 10 | GRANT_AWARD | one-to-many | EXPENSE_CLAIM | billed_against | Expense Claims are billed against approved Grant Award budget lines. |
| 11 | GRANT_AWARD | one-to-many | COMPLIANCE_AUDIT | audited_in | A Grant Award undergoes periodic Compliance Audits. |
| 12 | GRANT_APPLICATION | many-to-many | REVIEWER | assigned_to | Applications are assigned to multiple Reviewers (via APPLICATION_REVIEWER). |
