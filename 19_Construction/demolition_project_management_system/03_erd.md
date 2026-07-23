# Conceptual ERD — Demolition Project Management System

## Mermaid Code

```mermaid
erDiagram
    DEMOLITION_MAIN {
        int id PK
        string code
        string title
        datetime created_at
        string status
    }

    DEMOLITION_DETAIL {
        int detail_id PK
        int main_id FK
        string item_name
        decimal capacity_vol
        string remarks
    }

    DEMOLITION_INSPECTION {
        int inspect_id PK
        int main_id FK
        string inspector_name
        datetime inspect_date
        string result
    }

    DEMOLITION_RECORD {
        int record_id PK
        int main_id FK
        string record_code
        decimal value_amount
        datetime record_date
    }

    DEMOLITION_COMPLIANCE {
        int comp_id PK
        int main_id FK
        string rule_name
        string compliance_status
    }

    DEMOLITION_REPORT {
        int report_id PK
        int main_id FK
        string report_no
        datetime issue_date
        string summary
    }

    DEMOLITION_MAIN ||--o{ DEMOLITION_DETAIL : "contains"
    DEMOLITION_MAIN ||--o{ DEMOLITION_INSPECTION : "requires"
    DEMOLITION_MAIN ||--o{ DEMOLITION_RECORD : "generates"
    DEMOLITION_MAIN ||--o{ DEMOLITION_COMPLIANCE : "verifies"
    DEMOLITION_MAIN ||--o{ DEMOLITION_REPORT : "produces"
```

## Entity Description Table | Bang mo ta Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|-------------------|
| 1 | DEMOLITION_MAIN | Entity demolition_main | Stores demolition_main data for Demolition Project Management System | id | Main core entity |
| 2 | DEMOLITION_DETAIL | Entity demolition_detail | Stores demolition_detail data for Demolition Project Management System | detail_id | Main core entity |
| 3 | DEMOLITION_INSPECTION | Entity demolition_inspection | Stores demolition_inspection data for Demolition Project Management System | inspect_id | Main core entity |
| 4 | DEMOLITION_RECORD | Entity demolition_record | Stores demolition_record data for Demolition Project Management System | record_id | Main core entity |
| 5 | DEMOLITION_COMPLIANCE | Entity demolition_compliance | Stores demolition_compliance data for Demolition Project Management System | comp_id | Main core entity |
| 6 | DEMOLITION_REPORT | Entity demolition_report | Stores demolition_report data for Demolition Project Management System | report_id | Main core entity |

## Relationship Description | Mo ta Quan he

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | DEMOLITION_MAIN | one-to-many | DEMOLITION_DETAIL | contains | Thanh phan chinh bao gom nhieu chi tiet nghiep vu |
| 2 | DEMOLITION_MAIN | one-to-many | DEMOLITION_INSPECTION | requires | Thanh phan chinh yeu cau cac dot kiem tra kiem dinh |
| 3 | DEMOLITION_MAIN | one-to-many | DEMOLITION_RECORD | generates | Thanh phan chinh xuat cac ban ghi thong ke |
| 4 | DEMOLITION_MAIN | one-to-many | DEMOLITION_COMPLIANCE | verifies | Thanh phan chinh kiem tra tinh tuan thu quy chuan |
| 5 | DEMOLITION_MAIN | one-to-many | DEMOLITION_REPORT | produces | Thanh phan chinh xuat cac bao cao tong hop |
