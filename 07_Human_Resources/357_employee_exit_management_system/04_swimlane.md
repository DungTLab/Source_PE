# Swimlane Diagram — Employee Exit Management System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Offboarding"])

    subgraph EmployeeLane["Resigning Employee"]
        E1["Submit Resignation"]
        E2["Complete Handover Tasks"]
        E3["Return IT Assets"]
        E4["Receive Final Documents"]
    end

    subgraph SystemLane["Employee Exit Management System"]
        S1["Notify Manager"]
        S2["Initiate Clearance Workflows"]
        S3{"All Cleared?"}
        S4["Trigger Final Settlement"]
        S5["Generate Relieving Letter"]
    end

    subgraph ManagerLane["Department Manager"]
        M1["Approve Resignation"]
        M2["Approve Handover"]
    end
    
    subgraph IRLane["HR & IT Dept"]
        HR1["Conduct Exit Interview"]
        IT1["Verify Asset Return & Revoke Access"]
        HR2["Process Settlement"]
    end

    Finish(["End Offboarding"])

    Start --> E1 --> S1 --> M1
    M1 --> S2
    S2 --> E2
    S2 --> E3
    S2 --> HR1
    
    E2 --> M2
    E3 --> IT1
    
    M2 --> S3
    IT1 --> S3
    HR1 --> S3
    
    S3 -->|"No"| S2
    S3 -->|"Yes"| S4 --> HR2 --> S5 --> E4 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Resigning Employee | Nguoi khoi tao don, hoan thanh ban giao cong viec va tai san de duoc nghi viec. |
| 2 | Employee Exit Management System | He thong dieu pho luong cong viec, kiem tra tien do cua cac ben, va sinh tai lieu tu dong. |
| 3 | Department Manager | Quan ly truc tiep phe duyet don va xac nhan hoan tat ban giao cong viec. |
| 4 | HR & IT Dept | Bo phan thuc hien kiem tra tai san, thu hoi quyen, phong van nhan su va xu ly che do luong cuoi. |
