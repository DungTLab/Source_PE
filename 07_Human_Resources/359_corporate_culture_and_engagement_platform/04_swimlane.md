# Swimlane Diagram — Corporate Culture And Engagement Platform

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Recognition"])

    subgraph SenderLane["Sender (Employee)"]
        S1["Select Colleague"]
        S2["Enter Points & Message"]
        S3["Submit Recognition"]
    end

    subgraph SystemLane["Corporate Culture Platform"]
        C1["Check Point Balance"]
        C2{"Sufficient Points?"}
        C3["Show Error"]
        C4{"Points > Auto-approve Limit?"}
        C5["Save as Pending"]
        C6["Transfer Points & Publish Post"]
        C7["Send Notification"]
    end

    subgraph ManagerLane["Department Manager"]
        M1["Review Pending Recognition"]
        M2{"Approve?"}
    end

    subgraph ReceiverLane["Receiver (Employee)"]
        R1["Receive Notification"]
        R2["View Recognition & Points"]
    end

    Finish(["End Process"])

    Start --> S1 --> S2 --> S3 --> C1
    C1 --> C2
    C2 -->|"No"| C3 --> S2
    C2 -->|"Yes"| C4
    
    C4 -->|"Yes"| C5 --> M1
    M1 --> M2
    M2 -->|"Yes"| C6
    M2 -->|"No"| Finish
    
    C4 -->|"No"| C6
    
    C6 --> C7 --> R1 --> R2 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Sender (Employee) | Nguoi chu dong chon dong nghiep va tang diem ghi nhan. |
| 2 | Corporate Culture Platform | He thong kiem tra so diem, chuyen diem, xuat ban bai viet va gui thong bao. |
| 3 | Department Manager | Nguoi quan ly duyet cac khoan thuong diem lon vuot muc tu dong. |
| 4 | Receiver (Employee) | Nguoi nhan loi khen ngai, diem thuong va xem thong bao tu he thong. |
