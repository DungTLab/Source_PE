# Swimlane Diagram — Employee Wellness Program System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Log Activity"])

    subgraph EmployeeLane["Employee"]
        E1["Login to System"]
        E2["Enter Activity Details"]
        E3["Submit Activity Log"]
        E4["Receive Points Notification"]
    end

    subgraph SystemLane["Employee Wellness Program System"]
        S1["Validate Activity Data"]
        S2{"Is Data Normal?"}
        S3["Calculate & Update Points"]
        S4["Flag as Suspicious"]
        S5["Notify Coordinator"]
    end

    subgraph CoordinatorLane["Wellness Coordinator"]
        C1["Review Suspicious Log"]
        C2{"Approve?"}
    end

    Finish(["End Process"])

    Start --> E1 --> E2 --> E3 --> S1
    S1 --> S2
    
    S2 -->|"Yes"| S3
    S2 -->|"No (Out of range)"| S4 --> S5 --> C1
    
    C1 --> C2
    C2 -->|"Yes (Valid)"| S3
    C2 -->|"No (Invalid)"| Reject["Reject Log"] --> Finish
    
    S3 --> E4 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Employee | Nguoi chu dong nhap thong tin hoat dong the chat va nhan thong bao khi diem duoc cap nhat. |
| 2 | Employee Wellness Program System | He thong tu dong kiem tra su bat thuong cua du lieu, tinh toan diem thuong va danh dau cac ban ghi nghi ngo. |
| 3 | Wellness Coordinator | Nguoi quan ly nhan duoc thong bao, vao he thong de xem xet thu cong va ra quyet dinh phe duyet cac hoat dong bi nghi ngo. |
