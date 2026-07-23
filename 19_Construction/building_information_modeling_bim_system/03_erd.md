# Conceptual ERD — Building Information Modeling (BIM) System

## Mermaid Code

```mermaid
erDiagram
    BIM_PROJECT {
        int project_id PK
        string project_code
        string bim_standard
        datetime created_at
    }

    FEDERATED_MODEL {
        int model_id PK
        int project_id FK
        string model_name
        string file_format
        decimal file_size_mb
    }

    BIM_ELEMENT {
        int element_id PK
        int model_id FK
        string guid
        string category
        string material_type
    }

    CLASH_RECORD {
        int clash_id PK
        int model_id FK
        string element_a_guid
        string element_b_guid
        string status
    }

    RFI_ISSUE {
        int rfi_id PK
        int element_id FK
        string title
        string priority
        string status
    }

    SCHEDULE_4D_LINK {
        int link_id PK
        int element_id FK
        string wbs_code
        datetime planned_start
    }

    QTO_5D_ITEM {
        int qto_id PK
        int element_id FK
        decimal volume_m3
        decimal unit_rate
        decimal total_cost
    }

    ASSET_COBIE_DATA {
        int cobie_id PK
        int element_id FK
        string serial_number
        string manufacturer
        datetime warranty_end
    }

    BIM_PROJECT ||--o{ FEDERATED_MODEL : "contains"
    FEDERATED_MODEL ||--o{ BIM_ELEMENT : "defines"
    FEDERATED_MODEL ||--o{ CLASH_RECORD : "identifies"
    BIM_ELEMENT ||--o{ RFI_ISSUE : "generates"
    BIM_ELEMENT ||--o{ SCHEDULE_4D_LINK : "associates"
    BIM_ELEMENT ||--o{ QTO_5D_ITEM : "calculates"
    BIM_ELEMENT ||--o{ ASSET_COBIE_DATA : "exports"
```

## Entity Description Table | Bang mo ta Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|-------------------|
| 1 | BIM_PROJECT | Entity bim_project | Stores bim_project data for Building Information Modeling (BIM) System | project_id | Main core entity |
| 2 | FEDERATED_MODEL | Entity federated_model | Stores federated_model data for Building Information Modeling (BIM) System | model_id | Main core entity |
| 3 | BIM_ELEMENT | Entity bim_element | Stores bim_element data for Building Information Modeling (BIM) System | element_id | Main core entity |
| 4 | CLASH_RECORD | Entity clash_record | Stores clash_record data for Building Information Modeling (BIM) System | clash_id | Main core entity |
| 5 | RFI_ISSUE | Entity rfi_issue | Stores rfi_issue data for Building Information Modeling (BIM) System | rfi_id | Main core entity |
| 6 | SCHEDULE_4D_LINK | Entity schedule_4d_link | Stores schedule_4d_link data for Building Information Modeling (BIM) System | link_id | Main core entity |
| 7 | QTO_5D_ITEM | Entity qto_5d_item | Stores qto_5d_item data for Building Information Modeling (BIM) System | qto_id | Main core entity |
| 8 | ASSET_COBIE_DATA | Entity asset_cobie_data | Stores asset_cobie_data data for Building Information Modeling (BIM) System | cobie_id | Main core entity |

## Relationship Description | Mo ta Quan he

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | BIM_PROJECT | one-to-many | FEDERATED_MODEL | contains | Mot du an BIM chua nhieu file mo hinh thanh phan |
| 2 | FEDERATED_MODEL | one-to-many | BIM_ELEMENT | defines | Mo hinh dinh nghia nhieu doi tuong BIM chi tiet |
| 3 | FEDERATED_MODEL | one-to-many | CLASH_RECORD | identifies | Mo hinh phat hien nhieu va chạm hinh hoc |
| 4 | BIM_ELEMENT | one-to-many | RFI_ISSUE | generates | Doi tuong BIM phat sinh yeu cau lam ro RFI |
| 5 | BIM_ELEMENT | one-to-many | SCHEDULE_4D_LINK | associates | Doi tuong BIM lien ket voi tien do 4D |
| 6 | BIM_ELEMENT | one-to-many | QTO_5D_ITEM | calculates | Doi tuong BIM xuat khoi luong va chi phi 5D |
| 7 | BIM_ELEMENT | one-to-many | ASSET_COBIE_DATA | exports | Doi tuong BIM xuat du lieu quan ly tai san COBie |
