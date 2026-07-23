# Swimlane Diagram — Compliance and Labor Law Management System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Incident Reporting"])

    subgraph EmployeeLane["Employee"]
        E1["Login to System"]
        E2["Submit Incident Form"]
        E3["Receive Resolution Update"]
    end

    subgraph SystemLane["Compliance and Labor Law Management System"]
        S1["Validate Incident Details"]
        S2{"Is Form Valid?"}
        S3["Show Error Message"]
        S4["Save and Notify Officer"]
        S5["Update Incident Status"]
    end

    subgraph OfficerLane["Compliance Officer"]
        O1["Review Incident"]
        O2{"Requires Legal Action?"}
        O3["Escalate to Legal Case"]
        O4["Resolve Internally"]
    end

    Finish(["End Process"])

    Start --> E1 --> E2 --> S1
    S1 --> S2
    S2 -->|"No"| S3 --> E2
    S2 -->|"Yes"| S4 --> O1
    O1 --> O2
    O2 -->|"Yes"| O3 --> S5
    O2 -->|"No"| O4 --> S5
    S5 --> E3 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Employee | Nguoi chu dong bao cao su co lao dong va nhan phan hoi ket qua. |
| 2 | Compliance and Labor Law Management System | He thong kiem tra du lieu, luu tru bao cao, cap nhat trang thai va dieu phoi thong bao. |
| 3 | Compliance Officer | Nguoi tiep nhan, danh gia muc do vi pham va quyet dinh huong xu ly (noi bo hoac phap ly). |
