# Conceptual ERD — Construction Risk Management System

## Mermaid Code

```mermaid
erDiagram
    CONSTRUCTI_MAIN {
        int id PK
        string code
        string title
        datetime created_at
        string status
    }

    CONSTRUCTI_DETAIL {
        int detail_id PK
        int main_id FK
        string item_name
        decimal capacity_vol
        string remarks
    }

    CONSTRUCTI_INSPECTION {
        int inspect_id PK
        int main_id FK
        string inspector_name
        datetime inspect_date
        string result
    }

    CONSTRUCTI_RECORD {
        int record_id PK
        int main_id FK
        string record_code
        decimal value_amount
        datetime record_date
    }

    CONSTRUCTI_COMPLIANCE {
        int comp_id PK
        int main_id FK
        string rule_name
        string compliance_status
    }

    CONSTRUCTI_REPORT {
        int report_id PK
        int main_id FK
        string report_no
        datetime issue_date
        string summary
    }

    CONSTRUCTI_MAIN ||--o{ CONSTRUCTI_DETAIL : "contains"
    CONSTRUCTI_MAIN ||--o{ CONSTRUCTI_INSPECTION : "requires"
    CONSTRUCTI_MAIN ||--o{ CONSTRUCTI_RECORD : "generates"
    CONSTRUCTI_MAIN ||--o{ CONSTRUCTI_COMPLIANCE : "verifies"
    CONSTRUCTI_MAIN ||--o{ CONSTRUCTI_REPORT : "produces"
```

## Entity Description Table | Bang mo ta Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|-------------------|
| 1 | CONSTRUCTI_MAIN | Entity constructi_main | Stores constructi_main data for Construction Risk Management System | id | Main core entity |
| 2 | CONSTRUCTI_DETAIL | Entity constructi_detail | Stores constructi_detail data for Construction Risk Management System | detail_id | Main core entity |
| 3 | CONSTRUCTI_INSPECTION | Entity constructi_inspection | Stores constructi_inspection data for Construction Risk Management System | inspect_id | Main core entity |
| 4 | CONSTRUCTI_RECORD | Entity constructi_record | Stores constructi_record data for Construction Risk Management System | record_id | Main core entity |
| 5 | CONSTRUCTI_COMPLIANCE | Entity constructi_compliance | Stores constructi_compliance data for Construction Risk Management System | comp_id | Main core entity |
| 6 | CONSTRUCTI_REPORT | Entity constructi_report | Stores constructi_report data for Construction Risk Management System | report_id | Main core entity |

## Relationship Description | Mo ta Quan he

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | CONSTRUCTI_MAIN | one-to-many | CONSTRUCTI_DETAIL | contains | Thanh phan chinh bao gom nhieu chi tiet nghiep vu |
| 2 | CONSTRUCTI_MAIN | one-to-many | CONSTRUCTI_INSPECTION | requires | Thanh phan chinh yeu cau cac dot kiem tra kiem dinh |
| 3 | CONSTRUCTI_MAIN | one-to-many | CONSTRUCTI_RECORD | generates | Thanh phan chinh xuat cac ban ghi thong ke |
| 4 | CONSTRUCTI_MAIN | one-to-many | CONSTRUCTI_COMPLIANCE | verifies | Thanh phan chinh kiem tra tinh tuan thu quy chuan |
| 5 | CONSTRUCTI_MAIN | one-to-many | CONSTRUCTI_REPORT | produces | Thanh phan chinh xuat cac bao cao tong hop |
