# Swimlane Diagram — Pet Adoption & Animal Shelter System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Adopter / Foster Parent"]
        A1["Search Available Pets Catalog"]
        A2["Submit Adoption Application"]
        A3["Sign Adoption Contract & Pay Fee"]
        A4["Receive Pet & Microchip Certificate"]
    end

    subgraph Lane2["System"]
        S1["Filter Available Pets & Show Profiles"]
        S2["Validate Landlord & Housing Data"]
        S3{"Vet Health Clearance Granted?"}
        S4["Generate Adoption Contract & Fee Charge"]
        S5["Execute Microchip Registry Transfer"]
    end

    subgraph Lane3["Shelter Staff"]
        S_Staff1["Process Rescue Intake & Assign Kennel"]
        S_Staff2["Review Application & Conduct Home Check"]
        S_Staff3{"Approve Adoption Application?"}
    end

    subgraph Lane4["Veterinary Surgeon"]
        V1["Perform Health Check & Rabies Shot"]
        V2["Execute Spay/Neuter Surgery"]
    end

    Finish(["End"])

    Start --> S_Staff1 --> V1 --> V2 --> S1 --> A1 --> A2 --> S2 --> S_Staff2 --> S_Staff3
    S_Staff3 -->|"Yes"| S3
    S_Staff3 -->|"No"| Finish
    S3 -->|"Yes"| S4 --> A3 --> S5 --> A4 --> Finish
    S3 -->|"No"| V1
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Adopter / Foster Parent | Searches adoption catalog, submits application with housing information, signs adoption agreement, pays fees, and receives pet with microchip certificate. |
| 2 | System | Filters pet profiles, verifies application housing rules, validates medical readiness, generates adoption agreements, and transfers microchip registration via API. |
| 3 | Shelter Staff | Registers animal intake, assigns kennels, evaluates adoption applications, conducts landlord/home vetting, and authorizes adoption approvals. |
| 4 | Veterinary Surgeon | Performs health examinations, administers rabies and core vaccinations, executes spay/neuter surgeries, and grants medical release. |
