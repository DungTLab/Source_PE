# Swimlane Diagram — Social Insurance Management System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Claim Process"])

    subgraph EmployeeLane["Employee"]
        E1["Login & Select Claim Type"]
        E2["Upload Medical Documents"]
        E3["Submit Claim Request"]
        E4["Receive Status Notification"]
    end

    subgraph SystemLane["Social Insurance Management System"]
        S1["Validate Documents"]
        S2{"Is Valid?"}
        S3["Notify Validation Error"]
        S4["Change Status to Pending"]
        S5["Update Final Status"]
    end

    subgraph HRLane["HR Manager"]
        H1["Review Claim"]
        H2{"Approve?"}
        H3["Sign & Send to Gov Portal"]
    end
    
    subgraph GovLane["Government Insurance Portal"]
        G1["Process Claim"]
        G2["Return Processing Status"]
    end

    Finish(["End Process"])

    Start --> E1 --> E2 --> E3 --> S1
    S1 --> S2
    S2 -->|"No"| S3 --> E2
    S2 -->|"Yes"| S4 --> H1
    
    H1 --> H2
    H2 -->|"No (Reject)"| S5
    H2 -->|"Yes (Approve)"| H3 --> G1
    
    G1 --> G2 --> S5 --> E4 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Employee | Nguoi chu dong tao ho so, tai len chung tu va nop len he thong. |
| 2 | Social Insurance Management System | He thong kiem tra tinh hop le, chuyen trang thai va gui thong bao. |
| 3 | HR Manager | Nguoi quan ly nhan su kiem tra thong tin, duyet va ky so gui len co quan BHXH. |
| 4 | Government Insurance Portal | He thong cua co quan BHXH tiep nhan, xu ly va tra ve ket qua cuoi cung. |
