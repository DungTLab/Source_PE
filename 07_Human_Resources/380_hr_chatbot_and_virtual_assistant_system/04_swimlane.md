# Swimlane Diagram — HR Chatbot and Virtual Assistant System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Chat"])

    subgraph EmployeeLane["Employee"]
        E1["Send HR Question"]
        E2["Receive Answer"]
        E3["Provide Feedback"]
    end

    subgraph BotLane["Chatbot System"]
        S1["Analyze NLP Intent"]
        S2{"High Confidence?"}
        S3["Search Knowledge Base"]
        S4["Generate Bot Reply"]
        S5["Log Interaction & Feedback"]
        S6["Create Support Ticket"]
    end

    subgraph HumanLane["Human HR Agent"]
        H1["Review Escalated Ticket"]
        H2["Respond to Employee"]
    end

    Finish(["End Chat"])

    Start --> E1 --> S1
    S1 --> S2
    S2 -->|"Yes"| S3 --> S4 --> E2 --> E3 --> S5 --> Finish
    S2 -->|"No"| S6 --> H1 --> H2 --> E2
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Employee | Nguoi dung khoi tao cau hoi, nhan ket qua va the hien danh gia cuoi cung. |
| 2 | Chatbot System | He thong phan tich y dinh (NLP), dua ra quyet dinh tra loi tu dong hoac chuyen cho nhan vien that neu do tin cay thap. |
| 3 | Human HR Agent | Nhan vien tiep nhan nhung yeu cau vuot qua kha nang cua bot, xu ly va tra loi bu lai cho nguoi dung. |
