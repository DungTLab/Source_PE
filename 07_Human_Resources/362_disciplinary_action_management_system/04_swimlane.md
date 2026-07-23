# Swimlane Diagram — Disciplinary Action Management System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Process"])

    subgraph EmployeeLane["Employee"]
        E1["Submit Incident Report"]
        E2["Provide Additional Info"]
        E3["Receive Notification"]
    end

    subgraph SystemLane["Disciplinary Action Management System"]
        S1["Validate & Save Report"]
        S2["Route to HR"]
        S3["Update Status to Investigating"]
        S4["Save Final Decision"]
        S5["Generate Warning Letter"]
    end

    subgraph HRLane["HR Manager"]
        H1["Review Incident"]
        H2{"Needs Investigation?"}
        H3["Conduct Investigation"]
        H4["Apply Disciplinary Action"]
    end

    Finish(["End Process"])

    Start --> E1 --> S1 --> S2 --> H1
    H1 --> H2
    H2 -->|"Yes"| S3 --> H3 --> E2 --> H4
    H2 -->|"No"| H4
    
    H4 --> S4 --> S5 --> E3 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Employee | Nguoi bao cao su co, cung cap thong tin khi dieu tra va nhan ket qua. |
| 2 | Disciplinary Action Management System | He thong luu tru, validate, chuyen huong va tu dong sinh thu canh cao. |
| 3 | HR Manager | Nguoi doc bao cao, quyet dinh dieu tra va dua ra muc phat ky luat. |
