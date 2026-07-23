# Swimlane Diagram — Job Description and Grading System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Process"])

    subgraph Lane1["HR Specialist"]
        H1["Draft Job Description"]
        H2["Assign Preliminary Grade"]
        H3["Submit for Approval"]
        H4["Publish Job Profile"]
    end

    subgraph Lane2["Job Description and Grading System"]
        S1["Validate Grade Constraints"]
        S2{"Is Valid?"}
        S3["Show Error & Prompt Revision"]
        S4["Notify Department Manager"]
        S5["Update Status to Published"]
    end

    subgraph Lane3["Department Manager"]
        M1["Review Job Description"]
        M2{"Approve?"}
        M3["Request Revision"]
    end

    Start --> H1 --> H2 --> H3 --> S1
    S1 --> S2
    S2 -->|"No"| S3 --> H2
    S2 -->|"Yes"| S4 --> M1
    
    M1 --> M2
    M2 -->|"No (Reject)"| M3 --> H1
    M2 -->|"Yes (Approve)"| S5 --> H4 --> Finish(["End Process"])
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | HR Specialist | Nguoi chu dong soan thao mo ta cong viec, de xuat ngach luong va phat hanh ho so sau khi duoc duyet. |
| 2 | Job Description and Grading System | He thong kiem tra tinh hop le cua ngach luong, gui thong bao va cap nhat trang thai tu dong. |
| 3 | Department Manager | Nguoi quan ly nhan thong bao, vao xem xet va ra quyet dinh phe duyet hoac yeu cau chinh sua mo ta cong viec. |
