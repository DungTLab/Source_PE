# Conceptual ERD — Research Institution Management System

## Mermaid Code

```mermaid
erDiagram
    INSTITUTION {
        int institution_id PK
        string name
        string code
        string country
        datetime created_at
    }

    RESEARCHER {
        int researcher_id PK
        int institution_id FK
        string full_name
        string email
        string academic_rank
        string department
        datetime hired_date
    }

    LABORATORY {
        int lab_id PK
        int institution_id FK
        int director_id FK
        string lab_name
        string location_building
        string safety_level
    }

    PROJECT {
        int project_id PK
        int pi_researcher_id FK
        int lab_id FK
        string title
        string research_area
        string status
        datetime start_date
        datetime end_date
    }

    GRANT_FUNDING {
        int grant_id PK
        int project_id FK
        string sponsor_name
        string grant_number
        decimal total_awarded_amount
        decimal remaining_balance
        datetime award_date
    }

    EQUIPMENT {
        int equipment_id PK
        int lab_id FK
        string serial_number
        string model_name
        string category
        string operational_status
    }

    EQUIPMENT_BOOKING {
        int booking_id PK
        int equipment_id FK
        int researcher_id FK
        datetime start_time
        datetime end_time
        string booking_status
    }

    ETHICS_APPROVAL {
        int ethics_id PK
        int project_id FK
        string irb_reference_number
        string review_type
        string approval_status
        datetime expiry_date
    }

    PUBLICATION {
        int publication_id PK
        int project_id FK
        string title
        string doi
        string journal_name
        datetime publish_date
        int citation_count
    }

    RESEARCH_DATASET {
        int dataset_id PK
        int publication_id FK
        int project_id FK
        string dataset_doi
        string repository_url
        decimal file_size_gb
        string access_rights
    }

    PATENT_IP {
        int patent_id PK
        int project_id FK
        string patent_number
        string title
        string filing_status
        datetime application_date
    }

    PROJECT_MEMBERS {
        int project_id PK, FK
        int researcher_id PK, FK
        string project_role
    }

    INSTITUTION ||--o{ RESEARCHER : "employs"
    INSTITUTION ||--o{ LABORATORY : "operates"
    LABORATORY ||--o{ EQUIPMENT : "houses"
    RESEARCHER ||--o{ LABORATORY : "directs"
    RESEARCHER ||--o{ PROJECT : "leads_as_pi"
    LABORATORY ||--o{ PROJECT : "hosts"
    PROJECT ||--o{ GRANT_FUNDING : "funded_by"
    EQUIPMENT ||--o{ EQUIPMENT_BOOKING : "scheduled_in"
    RESEARCHER ||--o{ EQUIPMENT_BOOKING : "reserves"
    PROJECT ||--|| ETHICS_APPROVAL : "cleared_by"
    PROJECT ||--o{ PUBLICATION : "produces"
    PUBLICATION ||--o{ RESEARCH_DATASET : "attaches"
    PROJECT ||--o{ PATENT_IP : "generates"
    PROJECT ||--o{ PROJECT_MEMBERS : "staffed_by"
    RESEARCHER ||--o{ PROJECT_MEMBERS : "participates_in"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|-------------------|
| 1 | INSTITUTION | Viện Nghiên cứu | Represents the core academic or scientific institution governing laboratories and researchers. | institution_id (PK), name, code, country | Employs Researchers, operates Laboratories |
| 2 | RESEARCHER | Nhà Nghiên cứu | Individual researcher, professor, postdoc, or technician conducting scientific work. | researcher_id (PK), institution_id (FK), full_name, academic_rank | Belongs to Institution, leads Projects, reserves Equipment |
| 3 | LABORATORY | Phòng Thí nghiệm | Physical research facility equipped with specialized instruments and safety levels. | lab_id (PK), institution_id (FK), director_id (FK), lab_name, safety_level | Belongs to Institution, houses Equipment, hosts Projects |
| 4 | PROJECT | Đề tài Nghiên cứu | Core research initiative with defined scientific goals, timeline, and principal investigator. | project_id (PK), pi_researcher_id (FK), lab_id (FK), title, status | Led by PI Researcher, funded by Grants, produces Publications |
| 5 | GRANT_FUNDING | Nguồn Kinh phí Tài trợ | Financial award provided by external sponsors or internal seed funds to support a project. | grant_id (PK), project_id (FK), sponsor_name, total_awarded_amount | Funds Project |
| 6 | EQUIPMENT | Thiết bị Thí nghiệm | Scientific instrument, microscope, or specialized hardware asset located in a laboratory. | equipment_id (PK), lab_id (FK), model_name, serial_number, operational_status | Housed in Laboratory, scheduled in Bookings |
| 7 | EQUIPMENT_BOOKING | Lịch Đặt Thiết bị | Time reservation slot booked by a researcher to operate specific lab equipment. | booking_id (PK), equipment_id (FK), researcher_id (FK), start_time, end_time | Belongs to Equipment, reserved by Researcher |
| 8 | ETHICS_APPROVAL | Phê duyệt Đạo đức (IRB) | Institutional Review Board compliance certification for human/animal subjects research. | ethics_id (PK), project_id (FK), irb_reference_number, approval_status | Clears Project |
| 9 | PUBLICATION | Bài báo Khoa học | Peer-reviewed journal paper, conference proceeding, or book chapter originating from research. | publication_id (PK), project_id (FK), title, doi, journal_name | Produced by Project, attaches Datasets |
| 10 | RESEARCH_DATASET | Dữ liệu Nghiên cứu | Raw or curated analytical dataset supporting research findings deposited in digital repositories. | dataset_id (PK), publication_id (FK), project_id (FK), dataset_doi, repository_url | Attached to Publication and Project |
| 11 | PATENT_IP | Bằng sáng chế & Sở hữu Trí tuệ | Intellectual property disclosure or granted patent resulting from research discoveries. | patent_id (PK), project_id (FK), patent_number, title, filing_status | Generated by Project |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | INSTITUTION | one-to-many | RESEARCHER | employs | An Institution employs multiple academic Researchers. |
| 2 | INSTITUTION | one-to-many | LABORATORY | operates | An Institution operates multiple research Laboratories. |
| 3 | LABORATORY | one-to-many | EQUIPMENT | houses | A Laboratory houses multiple scientific Equipment assets. |
| 4 | RESEARCHER | one-to-many | LABORATORY | directs | A senior Researcher directs one or more Laboratories. |
| 5 | RESEARCHER | one-to-many | PROJECT | leads_as_pi | A Researcher leads multiple research Projects as Principal Investigator. |
| 6 | LABORATORY | one-to-many | PROJECT | hosts | A Laboratory hosts one or more research Projects. |
| 7 | PROJECT | one-to-many | GRANT_FUNDING | funded_by | A Project can be funded by one or multiple Grant awards. |
| 8 | EQUIPMENT | one-to-many | EQUIPMENT_BOOKING | scheduled_in | Equipment is reserved across multiple time Bookings. |
| 9 | RESEARCHER | one-to-many | EQUIPMENT_BOOKING | reserves | A Researcher makes multiple Equipment Bookings. |
| 10 | PROJECT | one-to-one | ETHICS_APPROVAL | cleared_by | A Project is cleared by an Ethics Approval protocol. |
| 11 | PROJECT | one-to-many | PUBLICATION | produces | A Project produces multiple scientific Publications. |
| 12 | PUBLICATION | one-to-many | RESEARCH_DATASET | attaches | A Publication attaches one or more public Research Datasets. |
| 13 | PROJECT | one-to-many | PATENT_IP | generates | A Project generates one or more Patent & IP filings. |
| 14 | PROJECT | many-to-many | RESEARCHER | staffed_by | Projects are staffed by multiple Researchers (via PROJECT_MEMBERS). |
