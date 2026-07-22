# Conceptual ERD — Pet Adoption & Animal Shelter System

## Mermaid Code

```mermaid
erDiagram
    ANIMAL_SPECIES {
        int species_id PK
        string species_name
        string category
        string description
    }

    SHELTER_KENNEL {
        int kennel_id PK
        string kennel_code
        string building_wing
        string size_capacity
        string occupancy_status
    }

    ANIMAL_RESCUE {
        int animal_id PK
        int species_id FK
        int kennel_id FK
        string animal_name
        string primary_breed
        string age_group
        string gender
        string intake_type
        string shelter_status
        datetime intake_date
    }

    ADOPTER_PROFILE {
        int adopter_id PK
        string full_name
        string email
        string phone
        string residence_type
        string landlord_approval
    }

    ADOPTION_APPLICATION {
        int application_id PK
        int animal_id FK
        int adopter_id FK
        datetime application_date
        string status
        string review_notes
    }

    ADOPTION_CONTRACT {
        int contract_id PK
        int application_id FK
        int animal_id FK
        int adopter_id FK
        decimal adoption_fee
        datetime contract_date
        string status
    }

    VET_MEDICAL_RECORD {
        int medical_id PK
        int animal_id FK
        string vet_surgeon_name
        string spay_neuter_status
        decimal weight_lbs
        string health_condition
        datetime exam_date
    }

    VACCINATION_LOG {
        int vaccine_log_id PK
        int animal_id FK
        string vaccine_name
        string serial_lot_number
        datetime administered_date
        datetime next_due_date
    }

    MICROCHIP_REGISTRATION {
        int chip_id PK
        int animal_id FK
        int adopter_id FK
        string microchip_number
        string registry_name
        datetime registration_date
    }

    FOSTER_PLACEMENT {
        int foster_id PK
        int animal_id FK
        int foster_parent_id FK
        datetime placement_start
        datetime expected_return
        string placement_status
    }

    DONATION_FEE {
        int fee_id PK
        int contract_id FK
        decimal fee_amount
        string fee_type
        string transaction_token
        datetime payment_date
    }

    ANIMAL_SPECIES ||--o{ ANIMAL_RESCUE : "classifies"
    SHELTER_KENNEL ||--o{ ANIMAL_RESCUE : "houses"
    ANIMAL_RESCUE ||--o{ ADOPTION_APPLICATION : "applied_for"
    ADOPTER_PROFILE ||--o{ ADOPTION_APPLICATION : "submits"
    ADOPTION_APPLICATION ||--|| ADOPTION_CONTRACT : "finalized_in"
    ADOPTER_PROFILE ||--o{ ADOPTION_CONTRACT : "signs"
    ANIMAL_RESCUE ||--o{ VET_MEDICAL_RECORD : "receives_care"
    ANIMAL_RESCUE ||--o{ VACCINATION_LOG : "vaccinated_in"
    ANIMAL_RESCUE ||--|| MICROCHIP_REGISTRATION : "identified_by"
    ADOPTER_PROFILE ||--o{ MICROCHIP_REGISTRATION : "registered_owner"
    ANIMAL_RESCUE ||--o{ FOSTER_PLACEMENT : "placed_in"
    ADOPTER_PROFILE ||--o{ FOSTER_PLACEMENT : "fosters"
    ADOPTION_CONTRACT ||--o{ DONATION_FEE : "paid_via"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|-------------------|
| 1 | ANIMAL_SPECIES | Phân loại Loài | Species classification taxonomy (Dog, Cat, Rabbit, Bird, Exotic). | species_id (PK), species_name, category | Classifies Animal Rescues |
| 2 | SHELTER_KENNEL | Chuồng / Kennel | Physical kennel run, cattery condo, or isolation ward housing an animal inside the shelter. | kennel_id (PK), kennel_code, building_wing, occupancy_status | Houses Animal Rescues |
| 3 | ANIMAL_RESCUE | Thú cưng Cứu hộ | Primary rescue animal profile including intake details, species, breed, age, and shelter status. | animal_id (PK), species_id (FK), kennel_id (FK), animal_name, primary_breed, shelter_status | Classed by Species, housed in Kennel, applied for in Applications, receives Medical Records |
| 4 | ADOPTER_PROFILE | Hồ sơ Người Nhận nuôi | Profile of registered adopter or foster parent including residence details and vetting status. | adopter_id (PK), full_name, email, residence_type, landlord_approval | Submits Adoption Applications, signs Contracts, fosters Pets, registered in Microchips |
| 5 | ADOPTION_APPLICATION | Đơn Xin Nhận nuôi | Formal application submitted by an adopter for a specific rescue pet, including housing details. | application_id (PK), animal_id (FK), adopter_id (FK), status, application_date | Applied for Animal Rescue, submitted by Adopter, finalized in Adoption Contract |
| 6 | ADOPTION_CONTRACT | Hợp đồng Nhận nuôi | Legal contract executing adoption ownership transfer, fee payment, and post-care terms. | contract_id (PK), application_id (FK), animal_id (FK), adopter_id (FK), adoption_fee | Finalizes Adoption Application, signed by Adopter, paid via Donation Fees |
| 7 | VET_MEDICAL_RECORD | Hồ sơ Y tế Thú y | Clinical health checkup findings, weight tracking, medical treatments, and spay/neuter status. | medical_id (PK), animal_id (FK), vet_surgeon_name, spay_neuter_status, exam_date | Receives care for Animal Rescue |
| 8 | VACCINATION_LOG | Nhật ký Tiêm phòng | Immunization log tracking rabies, core vaccines, lot serial numbers, and expiration dates. | vaccine_log_id (PK), animal_id (FK), vaccine_name, serial_lot_number, administered_date | Vaccinated in for Animal Rescue |
| 9 | MICROCHIP_REGISTRATION | Đăng ký Microchip | National pet microchip registration record linking 15-digit ISO chip number to adopter. | chip_id (PK), animal_id (FK), adopter_id (FK), microchip_number, registry_name | Identifies Animal Rescue, registered to Adopter |
| 10 | FOSTER_PLACEMENT | Nhận Trông nuôi Foster | Temporary placement record for animals staying with approved foster care families. | foster_id (PK), animal_id (FK), foster_parent_id (FK), placement_start, placement_status | Placed in for Animal Rescue, fostered by Adopter |
| 11 | DONATION_FEE | Phí Nhận nuôi / Quyên góp | Financial fee payment or shelter donation transaction processing. | fee_id (PK), contract_id (FK), fee_amount, fee_type, transaction_token | Pays Adoption Contract |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | ANIMAL_SPECIES | one-to-many | ANIMAL_RESCUE | classifies | An Animal Species classifies multiple Animal Rescues. |
| 2 | SHELTER_KENNEL | one-to-many | ANIMAL_RESCUE | houses | A Shelter Kennel houses one or more Animal Rescues over time. |
| 3 | ANIMAL_RESCUE | one-to-many | ADOPTION_APPLICATION | applied_for | An Animal Rescue receives multiple Adoption Applications. |
| 4 | ADOPTER_PROFILE | one-to-many | ADOPTION_APPLICATION | submits | An Adopter Profile submits multiple Adoption Applications. |
| 5 | ADOPTION_APPLICATION | one-to-one | ADOPTION_CONTRACT | finalized_in | An approved Application is finalized in an Adoption Contract. |
| 6 | ADOPTER_PROFILE | one-to-many | ADOPTION_CONTRACT | signs | An Adopter Profile signs multiple Adoption Contracts. |
| 7 | ANIMAL_RESCUE | one-to-many | VET_MEDICAL_RECORD | receives_care | An Animal Rescue receives care recorded in Vet Medical Records. |
| 8 | ANIMAL_RESCUE | one-to-many | VACCINATION_LOG | vaccinated_in | An Animal Rescue receives vaccinations logged in Vaccination Logs. |
| 9 | ANIMAL_RESCUE | one-to-one | MICROCHIP_REGISTRATION | identified_by | An Animal Rescue is identified by a unique Microchip Registration. |
| 10 | ADOPTER_PROFILE | one-to-many | MICROCHIP_REGISTRATION | registered_owner | An Adopter Profile is the registered owner in Microchip Registrations. |
| 11 | ANIMAL_RESCUE | one-to-many | FOSTER_PLACEMENT | placed_in | An Animal Rescue is placed in multiple Foster Placements. |
| 12 | ADOPTER_PROFILE | one-to-many | FOSTER_PLACEMENT | fosters | An Adopter Profile fosters multiple animals via Foster Placements. |
| 13 | ADOPTION_CONTRACT | one-to-many | DONATION_FEE | paid_via | An Adoption Contract is paid via Donation Fees. |
