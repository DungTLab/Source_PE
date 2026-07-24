# Swimlane Diagram — HR Document Management System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Signature Flow"])

    subgraph HRLane["HR Manager"]
        H1["Create & Send Document"]
    end

    subgraph SystemLane["HR Document Management System"]
        S1["Notify Employee"]
        S2["Initialize E-Signature Session"]
        S3["Update Document Status"]
        S4["Store Signed Document & Audit Log"]
    end

    subgraph EmployeeLane["Employee"]
        E1["Receive Notification"]
        E2["Review Document"]
        E3{"Agree to Sign?"}
        E4["Decline Document"]
    end

    subgraph ESignatureLane["E-Signature Provider"]
        ES1["Authenticate Signature"]
        ES2["Return Digital Certificate"]
    end

    Finish(["End Flow"])

    Start --> H1 --> S1 --> E1 --> E2 --> E3
    E3 -->|"No"| E4 --> S3
    E3 -->|"Yes"| S2 --> ES1
    
    ES1 --> ES2 --> S3
    S3 --> S4 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | HR Manager | Nguoi soan thao tai lieu hoac hop dong va khoi tao quy trinh yeu cau chu ky. |
| 2 | HR Document Management System | He thong dieu phoi luong, thong bao, luu tru lich su va cap nhat trang thai tai lieu. |
| 3 | Employee | Nguoi nhan yeu cau, xem xet noi dung va quyet dinh ky hoac tu choi tai lieu. |
| 4 | E-Signature Provider | Doi tac thu ba (API) cung cap chung thu so va xac thuc chu ky dien tu hop phap. |
