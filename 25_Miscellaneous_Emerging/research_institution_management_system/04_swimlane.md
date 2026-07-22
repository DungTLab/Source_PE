# Swimlane Diagram — Research Institution Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Principal Investigator"]
        P1["Draft Research Proposal & Budget"]
        P2["Submit Proposal & Ethics Protocol"]
        P3["Conduct Experiments & Log Data"]
        P4["Submit Publication Manuscript & DOI"]
    end

    subgraph Lane2["System"]
        S1["Validate Proposal Completeness"]
        S2{"Requires Human/Animal Subjects?"}
        S3["Route IRB Protocol to Ethics Board"]
        S4{"Ethics Approval Granted?"}
        S5["Submit Grant Proposal Dossier"]
        S6{"Grant Awarded?"}
        S7["Create Project Ledger Account"]
        S8["Link DOI & Update Investigator h-Index"]
    end

    subgraph Lane3["Institutional Review Board"]
        E1["Review Protocol & Consent Forms"]
        E2["Issue IRB Clearance Certificate"]
    end

    subgraph Lane4["Grant Funding Agency"]
        G1["Evaluate Proposal & Budget"]
        G2["Disburse Grant Funding Tranches"]
    end

    Finish(["End"])

    Start --> P1 --> P2 --> S1 --> S2
    S2 -->|"Yes"| S3 --> E1 --> E2 --> S4
    S2 -->|"No"| S5
    S4 -->|"Yes"| S5
    S4 -->|"No"| P1
    S5 --> G1 --> G2 --> S6
    S6 -->|"Yes"| S7 --> P3 --> P4 --> S8 --> Finish
    S6 -->|"No"| Finish
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Principal Investigator | Authors project proposal, drafts budget, submits ethics protocols, conducts experimental lab work, and registers publications. |
| 2 | System | Automates proposal routing, checks ethics prerequisites, transmits grant dossiers, sets up financial project ledgers, and tracks publication metrics. |
| 3 | Institutional Review Board | Evaluates research protocols for human/animal subjects safety, reviews consent documentation, and issues official IRB clearance certificates. |
| 4 | Grant Funding Agency | Conducts competitive peer review of grant applications, issues funding awards, and disburses research financial tranches. |
