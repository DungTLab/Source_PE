# Swimlane Diagram — Employee Communication Platform

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Announcement Process"])

    subgraph HRManagerLane["HR Manager"]
        H1["Login to Platform"]
        H2["Draft New Announcement"]
        H3["Select Target Audience & Importance"]
        H4["Publish Announcement"]
    end

    subgraph SystemLane["Employee Communication Platform"]
        S1["Save to Database"]
        S2{"Is Marked Urgent?"}
        S3["Post on Dashboard Main Feed"]
        S4["Trigger Email / Push Alert"]
    end

    subgraph EmployeeLane["Employee"]
        E1["Receive Notification"]
        E2["Open Announcement"]
        E3["Read & Acknowledge"]
    end

    Finish(["End Process"])

    Start --> H1 --> H2 --> H3 --> H4 --> S1
    S1 --> S2
    S2 -->|"No"| S3
    S2 -->|"Yes"| S4 --> S3
    
    S3 --> E2
    S4 --> E1 --> E2
    E2 --> E3 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | HR Manager | Nguoi khoi tao, soan thao va quyet dinh doi tuong/muc do quan trong cua thong bao truoc khi publish. |
| 2 | Employee Communication Platform | He thong luu tru thong bao, xu ly phan luong (kiem tra do khan cap) de gui canh bao cho nhan vien neu can thiet. |
| 3 | Employee | Nhan vien nhan duoc thong bao qua app hoac email, truy cap vao nen tang de doc va ghi nhan. |
