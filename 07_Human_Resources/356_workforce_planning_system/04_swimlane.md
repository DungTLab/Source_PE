# Swimlane Diagram — Workforce Planning System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Process"])

    subgraph HRPlannerLane["HR Planner"]
        P1["Analyze Workforce Gaps"]
        P2["Draft Workforce Plan"]
        P3["Submit Plan"]
        P4["Review Feedback"]
    end

    subgraph SystemLane["Workforce Planning System"]
        S1["Consolidate Data"]
        S2["Check Budget Limits"]
        S3{"Within Budget?"}
        S4["Flag as Over Budget"]
        S5["Update Status to Pending"]
        S6["Save Plan & Notify Executive"]
        S7["Update Final Status"]
    end

    subgraph ExecutiveLane["Executive"]
        E1["Review Workforce Plan"]
        E2{"Approve Plan?"}
    end

    Finish(["End Process"])

    Start --> P1 --> P2 --> P3 --> S1
    S1 --> S2 --> S3
    
    S3 -->|"No"| S4 --> S5
    S3 -->|"Yes"| S5
    
    S5 --> S6 --> E1
    
    E1 --> E2
    E2 -->|"Yes (Approve)"| S7
    E2 -->|"No (Reject)"| S7
    
    S7 --> P4 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | HR Planner | Phan tich thuc trang, lap ke hoach nhan su va gui len de phe duyet. |
| 2 | Workforce Planning System | He thong kiem tra tinh toan ngan sach, danh dau trang thai va dieu phoi thong bao. |
| 3 | Executive | Ban Giam doc kiem tra ban ke hoach va ra quyet dinh phe duyet hoac tu choi. |
