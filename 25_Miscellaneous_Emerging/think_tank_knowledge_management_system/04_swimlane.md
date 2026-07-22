# Swimlane Diagram — Think Tank Knowledge Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Policy Fellow"]
        F1["Draft Policy Report & Recommendations"]
        F2["Attach Datasets & Tag Taxonomy"]
        F3["Revise Draft Based on Review Feedback"]
        F4["Track Media Mentions & Citations"]
    end

    subgraph Lane2["System"]
        S1["Extract Text & Split into Chunks"]
        S2["Route Dossier to Peer Reviewers"]
        S3{"Peer & Editorial Approval Granted?"}
        S4["Mint DOI & Publish Open-Access Report"]
        S5["Dispatch Newsletter & Press Releases"]
        S6["Crawl News Outlets & Update Impact Score"]
    end

    subgraph Lane3["Peer Reviewer / Editor"]
        E1["Evaluate Methodology & Policy Value"]
        E2{"Revisions Required?"}
        E3["Execute Final Editorial Approval"]
    end

    subgraph Lane4["AI Vector Search Engine"]
        V1["Generate Text Embedding Vectors"]
        V2["Index Vectors in Knowledge Database"]
    end

    Finish(["End"])

    Start --> F1 --> F2 --> S1 --> V1 --> V2 --> S2 --> E1 --> E2
    E2 -->|"Yes"| F3 --> S1
    E2 -->|"No"| E3 --> S3
    S3 -->|"Yes"| S4 --> S5 --> F4 --> S6 --> Finish
    S3 -->|"No"| Finish
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Policy Fellow | Authors research reports, defines policy recommendations, uploads datasets, tags taxonomies, and monitors citation analytics. |
| 2 | System | Automates text chunking, triggers AI vector embedding generation, handles peer routing, mints DOIs, publishes open-access web reports, and tracks impact metrics. |
| 3 | Peer Reviewer / Editor | Conducts rigorous peer evaluations, checks policy argument validity, requests revisions, and executes final editorial approval. |
| 4 | AI Vector Search Engine | Computes high-dimensional text embeddings from document chunks and indexes vector records for natural language semantic search. |
