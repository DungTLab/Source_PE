# Swimlane Diagram — International Assignment Management System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Process"])

    subgraph EmployeeLane["Employee"]
        E1["Fill Assignment Form"]
        E2["Submit Form"]
        E3["Receive Approval Notification"]
    end

    subgraph SystemLane["System"]
        S1["Validate Data"]
        S2{"Is Data Valid?"}
        S3["Show Error"]
        S4["Save and Notify Manager"]
        S5["Update Status to Approved"]
        S6["Notify HR for Logistics"]
    end

    subgraph ManagerLane["Assignment Manager"]
        M1["Review Application"]
        M2{"Approve?"}
    end

    subgraph HRLane["HR Manager"]
        H1["Process Visa & Travel"]
    end

    Finish(["End Process"])

    Start --> E1 --> E2 --> S1
    S1 --> S2
    S2 -->|"No"| S3 --> E1
    S2 -->|"Yes"| S4 --> M1
    
    M1 --> M2
    M2 -->|"Yes"| S5 --> S6 --> H1
    M2 -->|"No"| S3
    
    H1 --> E3 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Employee | Nguoi khoi tao don xin cong tac va nhan thong bao cuoi cung. |
| 2 | System | Kiem tra tinh hop le, cap nhat trang thai va gui cac canh bao, thong bao cho cac ben lien quan. |
| 3 | Assignment Manager | Nguoi quan ly danh gia va ra quyet dinh duyet don. |
| 4 | HR Manager | Nhan su phu trach cac thu tuc hau can (visa, ve may bay) sau khi don duoc duyet. |
