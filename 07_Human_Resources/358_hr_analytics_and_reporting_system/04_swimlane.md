# Swimlane Diagram — HR Analytics and Reporting System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Report Generation"])

    subgraph UserLane["HR Manager"]
        U1["Login to System"]
        U2["Select Report Parameters"]
        U3["Click Generate Request"]
        U4["Download Exported File"]
    end

    subgraph SystemLane["HR Analytics and Reporting System"]
        S1["Validate Parameters"]
        S2{"Are Parameters Valid?"}
        S3["Show Error Notification"]
        S4["Query Aggregated Data"]
        S5["Render Charts & Tables"]
        S6["Generate Export File"]
    end

    subgraph DataLane["Core Data Storage"]
        D1["Retrieve Data Records"]
    end

    Finish(["End Process"])

    Start --> U1 --> U2 --> U3 --> S1
    S1 --> S2
    S2 -->|"No"| S3 --> U2
    S2 -->|"Yes"| S4 --> D1
    
    D1 --> S5
    S5 --> S6
    S6 --> U4 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | HR Manager | Nguoi dung chon tieu chi va thuc hien yeu cau tao bao cao, sau do nhan ket qua de phan tich. |
| 2 | HR Analytics and Reporting System | He thong kiem tra tinh hop le, xu ly logic, tong hop thanh bieu do va xuat ra file tai ve. |
| 3 | Core Data Storage | Kho du lieu luu tru cac thong tin nhan su da dong bo tu cac he thong ben ngoai. |
