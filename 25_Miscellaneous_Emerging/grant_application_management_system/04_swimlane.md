# Swimlane Diagram — Grant Application & Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Grant Applicant"]
        A1["Prepare Proposal & Budget Narrative"]
        A2["Submit Application & Tax ID"]
        A3["Sign Digital Award Agreement"]
        A4["Submit Milestone Progress & Receipts"]
    end

    subgraph Lane2["System"]
        S1["Verify Tax Eligibility & Complete Dossier"]
        S2{"Eligibility & Pre-Screen Passed?"}
        S3["Assign Dossier to Peer Reviewers"]
        S4["Aggregate Scores & Rank Applications"]
        S5{"Award Approved by Board?"}
        S6["Generate Award Contract & Agreement"]
        S7["Validate Milestone Claims & Receipts"]
        S8["Execute Banking Wire Tranche Payout"]
    end

    subgraph Lane3["Peer Reviewer"]
        R1["Declare Conflict of Interest"]
        R2["Evaluate Dossier & Score Rubric"]
    end

    subgraph Lane4["Grantor Board"]
        B1["Review Application Ranking Roster"]
        B2["Approve Final Grant Awards"]
        B3["Authorize Milestone Tranche Release"]
    end

    Finish(["End"])

    Start --> A1 --> A2 --> S1 --> S2
    S2 -->|"Yes"| S3 --> R1 --> R2 --> S4 --> B1 --> B2 --> S5
    S2 -->|"No"| Finish
    S5 -->|"Yes"| S6 --> A3 --> A4 --> S7 --> B3 --> S8 --> Finish
    S5 -->|"No"| Finish
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Grant Applicant | Authors project proposals, submits tax documentation, executes signed award contracts, and logs milestone deliverables with expense receipts. |
| 2 | System | Automates tax verification checks, routes application dossiers, calculates composite rubric scores, generates award contracts, and triggers electronic bank wire payouts. |
| 3 | Peer Reviewer | Discloses potential conflicts of interest, reviews assigned application narratives, and submits weighted scoring rubrics. |
| 4 | Grantor Board | Evaluates candidate ranking rosters, makes final award selection decisions, and approves milestone tranche releases. |
