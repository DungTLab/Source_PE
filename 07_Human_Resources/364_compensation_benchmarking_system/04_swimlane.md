# Swimlane Diagram — Compensation Benchmarking System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Benchmark Process"])

    subgraph AnalystLane["HR Analyst"]
        A1["Import Internal & Market Data"]
        A2["Map Internal Jobs to Market Jobs"]
        A3["Run Analysis & Generate Report"]
        A4["Submit Compensation Proposal"]
    end

    subgraph SystemLane["Compensation Benchmarking System"]
        S1["Validate Data Formats"]
        S2["Calculate Compa-ratio & Trends"]
        S3["Generate Dashboards & Alerts"]
        S4{"Within Budget?"}
        S5["Forward to Manager"]
        S6["Update Salary Bands in DB"]
    end

    subgraph ManagerLane["HR Manager"]
        M1["Review Proposal Details"]
        M2{"Approve?"}
    end

    Start --> A1 --> S1 --> A2 --> A3 --> S2 --> S3 --> A4 --> S4
    
    S4 -->|"Yes"| S5 --> M1
    S4 -->|"No"| S3
    
    M1 --> M2
    M2 -->|"Yes (Approve)"| S6
    M2 -->|"No (Reject)"| A4
    
    Finish(["End Process"])
    S6 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | HR Analyst | Nguoi chiu trach nhiem thu thap du lieu, ghep noi vi tri va tao de xuat dieu chinh luong. |
| 2 | Compensation Benchmarking System | He thong kiem tra du lieu, tinh toan cac chi so benchmark, va quan ly luong phe duyet giua cac ben. |
| 3 | HR Manager | Nguoi quan ly xem xet de xuat va dua ra quyet dinh phe duyet cuoi cung cho viec ap dung dai luong moi. |
