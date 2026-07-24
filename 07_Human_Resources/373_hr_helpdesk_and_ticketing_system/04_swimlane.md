# Swimlane Diagram — HR Helpdesk and Ticketing System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Ticket Process"])

    subgraph EmployeeLane["Employee"]
        E1["Login to Portal"]
        E2["Submit New Ticket"]
        E3["Provide Additional Info (If Requested)"]
        E4["Receive Resolution Notification"]
    end

    subgraph SystemLane["HR Helpdesk and Ticketing System"]
        S1["Validate Ticket Data"]
        S2{"Is Data Valid?"}
        S3["Show Error Message"]
        S4["Assign Ticket via Routing Rules"]
        S5["Update Ticket Status & Notify HR"]
        S6["Send Final Email to Employee"]
    end

    subgraph HRLane["HR Representative"]
        H1["Review Assigned Ticket"]
        H2{"More Info Needed?"}
        H3["Request Info (Pending User)"]
        H4["Resolve Ticket"]
    end

    Finish(["End Process"])

    Start --> E1 --> E2 --> S1
    S1 --> S2
    S2 -->|"No"| S3 --> E2
    S2 -->|"Yes"| S4 --> S5 --> H1
    
    H1 --> H2
    H2 -->|"Yes"| H3 --> E3 --> H1
    H2 -->|"No (Can Resolve)"| H4 --> S6
    
    S6 --> E4 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Employee | Nhan vien chu dong dang nhap, gui yeu cau (ticket), bo sung thong tin khi duoc yeu cau va nhan thong bao cuoi cung. |
| 2 | HR Helpdesk and Ticketing System | He thong tu dong kiem tra hop le, phan luong dua vao rule, cap nhat trang thai va gui thong bao email cho cac ben. |
| 3 | HR Representative | Nhan vien Nhan su tiep nhan ticket, xem xet, yeu cau bo sung thong tin (neu can) va truc tiep giai quyet van de. |
