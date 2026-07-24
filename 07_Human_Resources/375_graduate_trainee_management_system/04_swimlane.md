# Swimlane Diagram — Graduate Trainee Management System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Assignment Process"])

    subgraph TraineeLane["Graduate Trainee"]
        T1["Login to System"]
        T2["View Assignment Details"]
        T3["Upload Assignment File"]
        T4["View Evaluation & Feedback"]
    end

    subgraph SystemLane["Graduate Trainee Management System"]
        S1["Check Deadline Rules"]
        S2{"Is Before Deadline?"}
        S3["Reject Submission & Show Error"]
        S4["Save Submission & Notify Mentor"]
        S5["Update Trainee Progress Score"]
        S6["Send Result Notification"]
    end

    subgraph MentorLane["Mentor"]
        M1["Review Assignment File"]
        M2["Input Score and Feedback"]
    end

    Finish(["End Process"])

    Start --> T1 --> T2 --> T3 --> S1
    S1 --> S2
    S2 -->|"No"| S3 --> T2
    S2 -->|"Yes"| S4 --> M1
    
    M1 --> M2 --> S5
    S5 --> S6 --> T4 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Graduate Trainee | Doc de bai, hoan thanh va nop file bai tap, sau do nhan diem va phan hoi. |
| 2 | Graduate Trainee Management System | Kiem soat thoi gian nop bai, luu tru du lieu, tinh toan diem va gui thong bao cac ben. |
| 3 | Mentor | Nhan duoc thong bao co bai moi, vao xem xet cham diem va de lai nhan xet cho thuc tap sinh. |
