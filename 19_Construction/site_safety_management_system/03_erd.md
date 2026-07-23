# Conceptual ERD — Site Safety Management System

## Mermaid Code

```mermaid
erDiagram
    SITE_SAFET_MAIN {
        int id PK
        string code
        string title
        datetime created_at
        string status
    }

    SITE_SAFET_DETAIL {
        int detail_id PK
        int main_id FK
        string item_name
        decimal capacity_vol
        string remarks
    }

    SITE_SAFET_INSPECTION {
        int inspect_id PK
        int main_id FK
        string inspector_name
        datetime inspect_date
        string result
    }

    SITE_SAFET_RECORD {
        int record_id PK
        int main_id FK
        string record_code
        decimal value_amount
        datetime record_date
    }

    SITE_SAFET_COMPLIANCE {
        int comp_id PK
        int main_id FK
        string rule_name
        string compliance_status
    }

    SITE_SAFET_REPORT {
        int report_id PK
        int main_id FK
        string report_no
        datetime issue_date
        string summary
    }

    SITE_SAFET_MAIN ||--o{ SITE_SAFET_DETAIL : "contains"
    SITE_SAFET_MAIN ||--o{ SITE_SAFET_INSPECTION : "requires"
    SITE_SAFET_MAIN ||--o{ SITE_SAFET_RECORD : "generates"
    SITE_SAFET_MAIN ||--o{ SITE_SAFET_COMPLIANCE : "verifies"
    SITE_SAFET_MAIN ||--o{ SITE_SAFET_REPORT : "produces"
```

## Entity Description Table | Bang mo ta Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|-------------------|
| 1 | SITE_SAFET_MAIN | Entity site_safet_main | Stores site_safet_main data for Site Safety Management System | id | Main core entity |
| 2 | SITE_SAFET_DETAIL | Entity site_safet_detail | Stores site_safet_detail data for Site Safety Management System | detail_id | Main core entity |
| 3 | SITE_SAFET_INSPECTION | Entity site_safet_inspection | Stores site_safet_inspection data for Site Safety Management System | inspect_id | Main core entity |
| 4 | SITE_SAFET_RECORD | Entity site_safet_record | Stores site_safet_record data for Site Safety Management System | record_id | Main core entity |
| 5 | SITE_SAFET_COMPLIANCE | Entity site_safet_compliance | Stores site_safet_compliance data for Site Safety Management System | comp_id | Main core entity |
| 6 | SITE_SAFET_REPORT | Entity site_safet_report | Stores site_safet_report data for Site Safety Management System | report_id | Main core entity |

## Relationship Description | Mo ta Quan he

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | SITE_SAFET_MAIN | one-to-many | SITE_SAFET_DETAIL | contains | Thanh phan chinh bao gom nhieu chi tiet nghiep vu |
| 2 | SITE_SAFET_MAIN | one-to-many | SITE_SAFET_INSPECTION | requires | Thanh phan chinh yeu cau cac dot kiem tra kiem dinh |
| 3 | SITE_SAFET_MAIN | one-to-many | SITE_SAFET_RECORD | generates | Thanh phan chinh xuat cac ban ghi thong ke |
| 4 | SITE_SAFET_MAIN | one-to-many | SITE_SAFET_COMPLIANCE | verifies | Thanh phan chinh kiem tra tinh tuan thu quy chuan |
| 5 | SITE_SAFET_MAIN | one-to-many | SITE_SAFET_REPORT | produces | Thanh phan chinh xuat cac bao cao tong hop |
