# Conceptual ERD — Volunteer Management System

## Mermaid Code

```mermaid
erDiagram
    VOLUNTEER {
        int volunteer_id PK
        string full_name
        string email
        string phone
        string status
        decimal total_hours_served
        datetime created_at
    }

    ORGANIZATION {
        int org_id PK
        string name
        string org_type
        string contact_email
        string verification_status
        datetime registered_at
    }

    COORDINATOR {
        int coordinator_id PK
        int org_id FK
        string full_name
        string email
        string role_title
        datetime created_at
    }

    OPPORTUNITY {
        int opportunity_id PK
        int org_id FK
        int coordinator_id FK
        string title
        string description
        string location
        string status
        datetime created_at
    }

    SHIFT {
        int shift_id PK
        int opportunity_id FK
        datetime start_time
        datetime end_time
        int max_volunteers
        int filled_slots
        string shift_status
    }

    APPLICATION {
        int application_id PK
        int volunteer_id FK
        int opportunity_id FK
        int shift_id FK
        datetime application_date
        string status
    }

    TIMESHEET {
        int timesheet_id PK
        int volunteer_id FK
        int shift_id FK
        datetime check_in_time
        datetime check_out_time
        decimal hours_logged
        string approval_status
    }

    BACKGROUND_CHECK {
        int check_id PK
        int volunteer_id FK
        string provider_name
        string status
        datetime verification_date
        datetime expiry_date
    }

    CERTIFICATE {
        int certificate_id PK
        int volunteer_id FK
        string certificate_code
        decimal total_hours_certified
        datetime issue_date
        string file_url
    }

    REWARD_BADGE {
        int badge_id PK
        string badge_name
        string description
        int hours_threshold
        string icon_url
    }

    SKILL {
        int skill_id PK
        string skill_name
        string category
        string description
    }

    VOLUNTEER_SKILL {
        int volunteer_id PK, FK
        int skill_id PK, FK
        string proficiency_level
    }

    VOLUNTEER_BADGE {
        int volunteer_id PK, FK
        int badge_id PK, FK
        datetime awarded_at
    }

    ORGANIZATION ||--o{ COORDINATOR : "employs"
    ORGANIZATION ||--o{ OPPORTUNITY : "hosts"
    COORDINATOR ||--o{ OPPORTUNITY : "manages"
    OPPORTUNITY ||--o{ SHIFT : "contains"
    VOLUNTEER ||--o{ APPLICATION : "submits"
    OPPORTUNITY ||--o{ APPLICATION : "receives"
    SHIFT ||--o{ APPLICATION : "schedules"
    VOLUNTEER ||--o{ TIMESHEET : "logs"
    SHIFT ||--o{ TIMESHEET : "records"
    VOLUNTEER ||--o{ BACKGROUND_CHECK : "undergoes"
    VOLUNTEER ||--o{ CERTIFICATE : "earns"
    VOLUNTEER ||--o{ VOLUNTEER_SKILL : "possesses"
    SKILL ||--o{ VOLUNTEER_SKILL : "classified_in"
    VOLUNTEER ||--o{ VOLUNTEER_BADGE : "achieves"
    REWARD_BADGE ||--o{ VOLUNTEER_BADGE : "granted_to"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|-------------------|
| 1 | VOLUNTEER | Tình nguyện viên | Stores profile details, contact information, cumulative served hours, and status of registered volunteers. | volunteer_id (PK), full_name, email, status, total_hours_served | Has many Applications, Timesheets, Certificates, Background Checks, Skills, Badges |
| 2 | ORGANIZATION | Tổ chức | Stores details of non-profits, community groups, or entities hosting volunteer programs. | org_id (PK), name, org_type, verification_status | Has many Coordinators, Opportunities |
| 3 | COORDINATOR | Điều phối viên | Stores information for staff responsible for managing opportunities and approving volunteer hours. | coordinator_id (PK), org_id (FK), full_name, email | Belongs to Organization, manages Opportunities |
| 4 | OPPORTUNITY | Hoạt động Tình nguyện | Represents a volunteer project or event requiring volunteer participation. | opportunity_id (PK), org_id (FK), coordinator_id (FK), title, status | Belongs to Organization, contains Shifts, receives Applications |
| 5 | SHIFT | Ca Tình nguyện | Specific time slot within a volunteer opportunity with capacity limits. | shift_id (PK), opportunity_id (FK), start_time, end_time, max_volunteers | Belongs to Opportunity, has many Applications, Timesheets |
| 6 | APPLICATION | Đơn đăng ký | Tracks volunteer sign-ups for specific opportunities and shifts, including review status. | application_id (PK), volunteer_id (FK), opportunity_id (FK), shift_id (FK), status | Belongs to Volunteer, Opportunity, Shift |
| 7 | TIMESHEET | Bảng chấm công | Records attendance timestamps, logged service hours, and coordinator approval state. | timesheet_id (PK), volunteer_id (FK), shift_id (FK), check_in_time, hours_logged, approval_status | Belongs to Volunteer, Shift |
| 8 | BACKGROUND_CHECK | Xác minh Nhân thân | Tracks third-party identity and safety screening records for volunteers. | check_id (PK), volunteer_id (FK), provider_name, status, expiry_date | Belongs to Volunteer |
| 9 | CERTIFICATE | Chứng nhận Service | Official certificate of service issued to volunteers upon completing hours or projects. | certificate_id (PK), volunteer_id (FK), certificate_code, total_hours_certified, file_url | Belongs to Volunteer |
| 10 | REWARD_BADGE | Huy hiệu Khen thưởng | Gamification badge definition awarded to volunteers when milestone service thresholds are met. | badge_id (PK), badge_name, hours_threshold, icon_url | Granted to Volunteers via Volunteer_Badge |
| 11 | SKILL | Kỹ năng | Skill taxonomy entry (e.g., First Aid, Event Planning, Translation) used for matching. | skill_id (PK), skill_name, category | Associated with Volunteers via Volunteer_Skill |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | ORGANIZATION | one-to-many | COORDINATOR | employs | An Organization can employ multiple Coordinators. |
| 2 | ORGANIZATION | one-to-many | OPPORTUNITY | hosts | An Organization can host multiple volunteer Opportunities. |
| 3 | COORDINATOR | one-to-many | OPPORTUNITY | manages | A Coordinator manages one or more Opportunities. |
| 4 | OPPORTUNITY | one-to-many | SHIFT | contains | An Opportunity consists of one or many time Shifts. |
| 5 | VOLUNTEER | one-to-many | APPLICATION | submits | A Volunteer can submit applications for multiple Opportunities/Shifts. |
| 6 | OPPORTUNITY | one-to-many | APPLICATION | receives | An Opportunity receives applications from multiple Volunteers. |
| 7 | SHIFT | one-to-many | APPLICATION | schedules | A Shift receives sign-ups from multiple Volunteers. |
| 8 | VOLUNTEER | one-to-many | TIMESHEET | logs | A Volunteer logs multiple attendance Timesheets over time. |
| 9 | SHIFT | one-to-many | TIMESHEET | records | A Shift records check-in timesheets for participating Volunteers. |
| 10 | VOLUNTEER | one-to-many | BACKGROUND_CHECK | undergoes | A Volunteer can undergo background checks over time. |
| 11 | VOLUNTEER | one-to-many | CERTIFICATE | earns | A Volunteer earns certificates based on completed hours. |
| 12 | VOLUNTEER | many-to-many | SKILL | possesses | Volunteers possess multiple Skills (via VOLUNTEER_SKILL). |
| 13 | VOLUNTEER | many-to-many | REWARD_BADGE | achieves | Volunteers achieve gamification Badges (via VOLUNTEER_BADGE). |
