# Swimlane Diagram — Vendor and Agency Management HR

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Process"])

    subgraph VendorLane["Vendor Representative"]
        V1["Login to System"]
        V2["Upload Invoice Document"]
        V3["Submit Invoice"]
        V4["Receive Payment Notification"]
    end

    subgraph SystemLane["Vendor and Agency Management HR"]
        S1["Validate Invoice Details"]
        S2{"Against Contract?"}
        S3["Show Validation Error"]
        S4["Save as Pending & Notify HR"]
        S5["Update Invoice Status"]
        S6["Trigger Payment Gateway"]
    end

    subgraph HRLane["HR Manager"]
        H1["Review Pending Invoice"]
        H2{"Approve?"}
    end

    Finish(["End Process"])

    Start --> V1 --> V2 --> V3 --> S1
    S1 --> S2
    S2 -->|"No"| S3 --> V2
    S2 -->|"Yes"| S4 --> H1
    
    H1 --> H2
    H2 -->|"Yes (Approve)"| S5
    H2 -->|"No (Reject)"| S5
    
    S5 --> S6 --> V4 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Vendor Representative | Nguoi chu dong tao va nop hoa don thanh toan cho cac dich vu da thuc hien. |
| 2 | Vendor and Agency Management HR | He thong kiem tra doi chieu voi hop dong, luu trang thai hoa don, ket noi voi he thong tai chinh va thong bao. |
| 3 | HR Manager | Nguoi quan ly chiu trach nhiem kiem tra cuoi cung va duyet/tu choi hoa don tu Vendor. |
