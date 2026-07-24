# Swimlane Diagram — Gig Economy Worker Management System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Job Submission"])

    subgraph WorkerLane["Gig Worker"]
        W1["Upload Job Proof"]
        W2["Submit for Review"]
        W3["Receive Payment Notification"]
    end

    subgraph SystemLane["Gig Economy Worker Management System"]
        S1["Verify Proof Format"]
        S2{"Is Valid Format?"}
        S3["Show Format Error"]
        S4["Update Status to In Review & Notify Client"]
        S5["Process Payment Transfer"]
        S6["Send Final Notifications"]
    end

    subgraph ClientLane["Client"]
        C1["Review Job Proof"]
        C2{"Approve?"}
        C3["Request Revision"]
    end

    Finish(["End Process"])

    Start --> W1 --> W2 --> S1
    S1 --> S2
    S2 -->|"No"| S3 --> W1
    S2 -->|"Yes"| S4 --> C1
    
    C1 --> C2
    C2 -->|"No"| C3 --> W2
    C2 -->|"Yes (Approve)"| S5
    
    S5 --> S6 --> W3 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Gig Worker | Nguoi thuc hien tai len bang chung hoan thanh cong viec va cho nhan thanh toan. |
| 2 | Gig Economy Worker Management System | He thong kiem tra dinh dang file, dieu phoi trang thai cong viec, xu ly thanh toan va thong bao. |
| 3 | Client | Nguoi kiem tra ket qua cong viec va ra quyet dinh phe duyet hoac yeu cau sua doi. |
