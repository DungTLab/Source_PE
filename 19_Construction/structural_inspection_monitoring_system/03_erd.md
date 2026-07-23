# Conceptual ERD — Structural Inspection & Monitoring System

## Mermaid Code

```mermaid
erDiagram
    STRUCTURAL_MAIN {
        int id PK
        string code
        string title
        datetime created_at
        string status
    }

    STRUCTURAL_DETAIL {
        int detail_id PK
        int main_id FK
        string item_name
        decimal capacity_vol
        string remarks
    }

    STRUCTURAL_INSPECTION {
        int inspect_id PK
        int main_id FK
        string inspector_name
        datetime inspect_date
        string result
    }

    STRUCTURAL_RECORD {
        int record_id PK
        int main_id FK
        string record_code
        decimal value_amount
        datetime record_date
    }

    STRUCTURAL_COMPLIANCE {
        int comp_id PK
        int main_id FK
        string rule_name
        string compliance_status
    }

    STRUCTURAL_REPORT {
        int report_id PK
        int main_id FK
        string report_no
        datetime issue_date
        string summary
    }

    STRUCTURAL_MAIN ||--o{ STRUCTURAL_DETAIL : "contains"
    STRUCTURAL_MAIN ||--o{ STRUCTURAL_INSPECTION : "requires"
    STRUCTURAL_MAIN ||--o{ STRUCTURAL_RECORD : "generates"
    STRUCTURAL_MAIN ||--o{ STRUCTURAL_COMPLIANCE : "verifies"
    STRUCTURAL_MAIN ||--o{ STRUCTURAL_REPORT : "produces"
```

## Entity Description Table | Bang mo ta Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|-------------------|
| 1 | STRUCTURAL_MAIN | Entity structural_main | Stores structural_main data for Structural Inspection & Monitoring System | id | Main core entity |
| 2 | STRUCTURAL_DETAIL | Entity structural_detail | Stores structural_detail data for Structural Inspection & Monitoring System | detail_id | Main core entity |
| 3 | STRUCTURAL_INSPECTION | Entity structural_inspection | Stores structural_inspection data for Structural Inspection & Monitoring System | inspect_id | Main core entity |
| 4 | STRUCTURAL_RECORD | Entity structural_record | Stores structural_record data for Structural Inspection & Monitoring System | record_id | Main core entity |
| 5 | STRUCTURAL_COMPLIANCE | Entity structural_compliance | Stores structural_compliance data for Structural Inspection & Monitoring System | comp_id | Main core entity |
| 6 | STRUCTURAL_REPORT | Entity structural_report | Stores structural_report data for Structural Inspection & Monitoring System | report_id | Main core entity |

## Relationship Description | Mo ta Quan he

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | STRUCTURAL_MAIN | one-to-many | STRUCTURAL_DETAIL | contains | Thanh phan chinh bao gom nhieu chi tiet nghiep vu |
| 2 | STRUCTURAL_MAIN | one-to-many | STRUCTURAL_INSPECTION | requires | Thanh phan chinh yeu cau cac dot kiem tra kiem dinh |
| 3 | STRUCTURAL_MAIN | one-to-many | STRUCTURAL_RECORD | generates | Thanh phan chinh xuat cac ban ghi thong ke |
| 4 | STRUCTURAL_MAIN | one-to-many | STRUCTURAL_COMPLIANCE | verifies | Thanh phan chinh kiem tra tinh tuan thu quy chuan |
| 5 | STRUCTURAL_MAIN | one-to-many | STRUCTURAL_REPORT | produces | Thanh phan chinh xuat cac bao cao tong hop |
