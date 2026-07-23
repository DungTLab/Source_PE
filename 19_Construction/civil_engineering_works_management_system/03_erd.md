# Conceptual ERD — Civil Engineering Works Management System

## Mermaid Code

```mermaid
erDiagram
    CIVIL_ENGI_MAIN {
        int id PK
        string code
        string title
        datetime created_at
        string status
    }

    CIVIL_ENGI_DETAIL {
        int detail_id PK
        int main_id FK
        string item_name
        decimal capacity_vol
        string remarks
    }

    CIVIL_ENGI_INSPECTION {
        int inspect_id PK
        int main_id FK
        string inspector_name
        datetime inspect_date
        string result
    }

    CIVIL_ENGI_RECORD {
        int record_id PK
        int main_id FK
        string record_code
        decimal value_amount
        datetime record_date
    }

    CIVIL_ENGI_COMPLIANCE {
        int comp_id PK
        int main_id FK
        string rule_name
        string compliance_status
    }

    CIVIL_ENGI_REPORT {
        int report_id PK
        int main_id FK
        string report_no
        datetime issue_date
        string summary
    }

    CIVIL_ENGI_MAIN ||--o{ CIVIL_ENGI_DETAIL : "contains"
    CIVIL_ENGI_MAIN ||--o{ CIVIL_ENGI_INSPECTION : "requires"
    CIVIL_ENGI_MAIN ||--o{ CIVIL_ENGI_RECORD : "generates"
    CIVIL_ENGI_MAIN ||--o{ CIVIL_ENGI_COMPLIANCE : "verifies"
    CIVIL_ENGI_MAIN ||--o{ CIVIL_ENGI_REPORT : "produces"
```

## Entity Description Table | Bang mo ta Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|-------------------|
| 1 | CIVIL_ENGI_MAIN | Entity civil_engi_main | Stores civil_engi_main data for Civil Engineering Works Management System | id | Main core entity |
| 2 | CIVIL_ENGI_DETAIL | Entity civil_engi_detail | Stores civil_engi_detail data for Civil Engineering Works Management System | detail_id | Main core entity |
| 3 | CIVIL_ENGI_INSPECTION | Entity civil_engi_inspection | Stores civil_engi_inspection data for Civil Engineering Works Management System | inspect_id | Main core entity |
| 4 | CIVIL_ENGI_RECORD | Entity civil_engi_record | Stores civil_engi_record data for Civil Engineering Works Management System | record_id | Main core entity |
| 5 | CIVIL_ENGI_COMPLIANCE | Entity civil_engi_compliance | Stores civil_engi_compliance data for Civil Engineering Works Management System | comp_id | Main core entity |
| 6 | CIVIL_ENGI_REPORT | Entity civil_engi_report | Stores civil_engi_report data for Civil Engineering Works Management System | report_id | Main core entity |

## Relationship Description | Mo ta Quan he

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | CIVIL_ENGI_MAIN | one-to-many | CIVIL_ENGI_DETAIL | contains | Thanh phan chinh bao gom nhieu chi tiet nghiep vu |
| 2 | CIVIL_ENGI_MAIN | one-to-many | CIVIL_ENGI_INSPECTION | requires | Thanh phan chinh yeu cau cac dot kiem tra kiem dinh |
| 3 | CIVIL_ENGI_MAIN | one-to-many | CIVIL_ENGI_RECORD | generates | Thanh phan chinh xuat cac ban ghi thong ke |
| 4 | CIVIL_ENGI_MAIN | one-to-many | CIVIL_ENGI_COMPLIANCE | verifies | Thanh phan chinh kiem tra tinh tuan thu quy chuan |
| 5 | CIVIL_ENGI_MAIN | one-to-many | CIVIL_ENGI_REPORT | produces | Thanh phan chinh xuat cac bao cao tong hop |
