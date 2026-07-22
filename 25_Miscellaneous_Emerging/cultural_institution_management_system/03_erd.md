# Conceptual ERD — Cultural Institution Management System

## Mermaid Code

```mermaid
erDiagram
    CULTURAL_STAFF {
        int staff_id PK
        string full_name
        string staff_role
        string department
        string email
    }

    CULTURAL_ARTIFACT {
        int artifact_id PK
        string accession_number
        string object_name
        string culture_period
        string primary_material
        decimal appraisal_value_usd
        string current_status
    }

    PROVENANCE_RECORD {
        int provenance_id PK
        int artifact_id FK
        string previous_owner_name
        string ownership_type
        int acquisition_year
        string title_deed_uri
    }

    EXHIBITION_GALLERY {
        int gallery_id PK
        string gallery_name
        string wing_building
        int max_capacity_visitors
        decimal temp_target_celsius
        decimal humidity_target_pct
    }

    GALLERY_CONSERVATION_SENSOR {
        int sensor_id PK
        int gallery_id FK
        int artifact_id FK
        string sensor_code
        decimal temperature_celsius
        decimal relative_humidity_pct
        decimal lux_light_level
        datetime recorded_at
    }

    VISITOR_TICKET {
        int ticket_id PK
        int gallery_id FK
        string qr_ticket_code
        string visitor_category
        decimal price_paid
        datetime timed_entry_slot
        string entry_status
    }

    PERFORMING_ARTS_EVENT {
        int event_id PK
        string production_title
        string performer_name
        string venue_auditorium
        datetime showtime
        decimal ticket_price_standard
    }

    ARTIFACT_LOAN_AGREEMENT {
        int loan_id PK
        int artifact_id FK
        string borrowing_institution
        string loan_direction
        datetime start_date
        datetime end_date
        decimal insurance_coverage_usd
    }

    INSTITUTION_DONOR {
        int donor_id PK
        string donor_name
        string donor_tier
        decimal total_contributions_usd
        string naming_rights_granted
    }

    MEMBERSHIP_PASS {
        int membership_id PK
        int donor_id FK
        string pass_number
        string membership_level
        datetime valid_until
    }

    RESEARCH_DIGITAL_ARCHIVE {
        int archive_id PK
        int artifact_id FK
        string digital_asset_type
        string iiif_manifest_uri
        string 3d_model_format
        datetime published_at
    }

    CULTURAL_STAFF ||--o{ CULTURAL_ARTIFACT : "accessions"
    CULTURAL_ARTIFACT ||--o{ PROVENANCE_RECORD : "documented_in"
    EXHIBITION_GALLERY ||--o{ CULTURAL_ARTIFACT : "displays"
    EXHIBITION_GALLERY ||--o{ GALLERY_CONSERVATION_SENSOR : "monitored_by"
    CULTURAL_ARTIFACT ||--o{ GALLERY_CONSERVATION_SENSOR : "protected_by"
    EXHIBITION_GALLERY ||--o{ VISITOR_TICKET : "hosts_visitors"
    CULTURAL_ARTIFACT ||--o{ ARTIFACT_LOAN_AGREEMENT : "subject_of_loan"
    INSTITUTION_DONOR ||--o{ MEMBERSHIP_PASS : "holds_pass"
    CULTURAL_ARTIFACT ||--o{ RESEARCH_DIGITAL_ARCHIVE : "digitized_as"
    CULTURAL_STAFF ||--o{ EXHIBITION_GALLERY : "curates"
    CULTURAL_STAFF ||--o{ PERFORMING_ARTS_EVENT : "coordinates"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|-------------------|
| 1 | CULTURAL_STAFF | Nhân viên Văn hóa | Museum curators, conservators, art registrars, and theater directors managing operations. | staff_id (PK), full_name, staff_role, department, email | Accessions Artifacts, curates Galleries, coordinates Events |
| 2 | CULTURAL_ARTIFACT | Cổ vật / Tác phẩm | Cataloged museum artifact or artwork with accession number, materials, and valuation. | artifact_id (PK), accession_number, object_name, culture_period, appraisal_value_usd | Documented in Provenance, displayed in Gallery, subject of Loan |
| 3 | PROVENANCE_RECORD | Nhật ký Lai lịch | Historical ownership chain record documenting previous owners, titles, and acquisition dates. | provenance_id (PK), artifact_id (FK), previous_owner_name, acquisition_year | Belongs to Cultural Artifact |
| 4 | EXHIBITION_GALLERY | Phòng Trưng bày | Physical exhibition hall or gallery room with environmental targets and capacity limits. | gallery_id (PK), gallery_name, wing_building, max_capacity_visitors, temp_target_celsius | Displays Artifacts, monitored by Sensors, hosts Visitor Tickets |
| 5 | GALLERY_CONSERVATION_SENSOR | Cảm biến Bảo quản | IoT sensor recording temperature, relative humidity, lux light, and UV index inside cases. | sensor_id (PK), gallery_id (FK), artifact_id (FK), temperature_celsius, lux_light_level | Monitors Gallery, protects Cultural Artifact |
| 6 | VISITOR_TICKET | Vé Tham quan | Visitor entry pass with QR code, timed-entry slot, category, and gate admission status. | ticket_id (PK), gallery_id (FK), qr_ticket_code, visitor_category, timed_entry_slot | Hosted in Exhibition Gallery |
| 7 | PERFORMING_ARTS_EVENT | Sự kiện Biểu diễn | Theater play, concert, lecture, or film event scheduled in institution auditoriums. | event_id (PK), production_title, performer_name, venue_auditorium, showtime | Coordinated by Cultural Staff |
| 8 | ARTIFACT_LOAN_AGREEMENT | Hợp đồng Mượn Cổ vật | Inter-museum loan contract for incoming/outgoing artifact exchange and insurance. | loan_id (PK), artifact_id (FK), borrowing_institution, loan_direction, insurance_coverage_usd | Subject of Cultural Artifact |
| 9 | INSTITUTION_DONOR | Nhà Tài trợ | Philanthropic donor or patron providing financial gifts, endowments, and sponsorships. | donor_id (PK), donor_name, donor_tier, total_contributions_usd, naming_rights_granted | Holds Membership Passes |
| 10 | MEMBERSHIP_PASS | Thẻ Thành viên Patron | Annual museum membership subscription pass granting free gallery access and benefits. | membership_id (PK), donor_id (FK), pass_number, membership_level, valid_until | Held by Institution Donor |
| 11 | RESEARCH_DIGITAL_ARCHIVE | Kho Lưu trữ Số | High-resolution digital asset (3D photogrammetry mesh, IIIF image manifest) for research. | archive_id (PK), artifact_id (FK), digital_asset_type, iiif_manifest_uri, 3d_model_format | Digitizes Cultural Artifact |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | CULTURAL_STAFF | one-to-many | CULTURAL_ARTIFACT | accessions | Cultural Staff accessions multiple Cultural Artifacts into the collection. |
| 2 | CULTURAL_ARTIFACT | one-to-many | PROVENANCE_RECORD | documented_in | A Cultural Artifact is documented in multiple Provenance Records over time. |
| 3 | EXHIBITION_GALLERY | one-to-many | CULTURAL_ARTIFACT | displays | An Exhibition Gallery displays multiple Cultural Artifacts. |
| 4 | EXHIBITION_GALLERY | one-to-many | GALLERY_CONSERVATION_SENSOR | monitored_by | An Exhibition Gallery is monitored by multiple Gallery Conservation Sensors. |
| 5 | CULTURAL_ARTIFACT | one-to-many | GALLERY_CONSERVATION_SENSOR | protected_by | A Cultural Artifact is protected by Gallery Conservation Sensors inside its case. |
| 6 | EXHIBITION_GALLERY | one-to-many | VISITOR_TICKET | hosts_visitors | An Exhibition Gallery hosts visitors via Visitor Tickets. |
| 7 | CULTURAL_ARTIFACT | one-to-many | ARTIFACT_LOAN_AGREEMENT | subject_of_loan | A Cultural Artifact can be the subject of multiple Artifact Loan Agreements. |
| 8 | INSTITUTION_DONOR | one-to-many | MEMBERSHIP_PASS | holds_pass | An Institution Donor holds one or more Membership Passes. |
| 9 | CULTURAL_ARTIFACT | one-to-many | RESEARCH_DIGITAL_ARCHIVE | digitized_as | A Cultural Artifact is digitized as Research Digital Archives (3D/IIIF). |
| 10 | CULTURAL_STAFF | one-to-many | EXHIBITION_GALLERY | curates | Cultural Staff (Curators) curates multiple Exhibition Galleries. |
| 11 | CULTURAL_STAFF | one-to-many | PERFORMING_ARTS_EVENT | coordinates | Cultural Staff coordinates multiple Performing Arts Events. |
