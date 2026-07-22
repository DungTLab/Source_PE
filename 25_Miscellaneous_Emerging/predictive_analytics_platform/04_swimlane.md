# Swimlane Diagram — Predictive Analytics Platform

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Data Scientist / Analyst"]
        D1["Define Feature Store & Setup AutoML Run"]
        D2["Review Model Leaderboard & SHAP Plots"]
        D3["Approve Model Deployment to Production"]
    end

    subgraph Lane2["System"]
        S1["Extract & Transform Features to Redis"]
        S2["Dispatch AutoML Model Candidate Search"]
        S3{"Validation Accuracy AUC > 0.85?"}
        S4["Flag Low Model Performance & Re-Tune"]
        S5["Register Model Artifact & Version Tag"]
        S6["Deploy Model Container to REST Endpoint"]
    end

    subgraph Lane3["Distributed Computing Cluster"]
        C1["Execute Parallel Spark/Ray Training Jobs"]
        C2["Compute Cross-Validation & Loss Metrics"]
    end

    subgraph Lane4["Model Inference Service API"]
        I1["Ingest Real-Time Prediction Requests"]
        I2["Return Sub-20ms Prediction Score Payload"]
    end

    Finish(["End"])

    Start --> D1 --> S1 --> S2 --> C1 --> C2 --> S3
    S3 -->|"No"| S4 --> D1
    S3 -->|"Yes"| S5 --> D2 --> D3 --> S6 --> I1 --> I2 --> Finish
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Data Scientist / Analyst | Configures feature store transformations, initiates AutoML training runs, evaluates candidate leaderboard rankings and SHAP feature importance plots, and approves production deployment. |
| 2 | System | Extracts features into offline/online stores, dispatches AutoML candidate searches, checks validation accuracy thresholds, registers model version artifacts, and deploys model containers. |
| 3 | Distributed Computing Cluster | Executes parallel PySpark/Ray training jobs across distributed GPU worker nodes, computing cross-validation accuracy metrics and loss functions. |
| 4 | Model Inference Service API | Ingests real-time prediction REST/gRPC requests, fetches online features, computes model inference, and returns sub-20ms prediction score payloads. |
