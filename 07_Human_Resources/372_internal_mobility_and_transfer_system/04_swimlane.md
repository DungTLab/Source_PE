# Swimlane Diagram — Internal Mobility and Transfer System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Transfer Process"])

    subgraph EmployeeLane["Employee"]
        E1["Browse Internal Jobs"]
        E2["Submit Transfer Request"]
        E3["Attend Interview (if needed)"]
        E4["Receive Final Decision"]
    end

    subgraph SystemLane["Internal Mobility System"]
        S1["Verify Eligibility"]
        S2{"Is Eligible?"}
        S3["Reject Request"]
        S4["Notify Current Manager"]
        S5["Update Status to Release Approved"]
        S6["Notify HR & Employee"]
    end

    subgraph CurrentManagerLane["Current Department Manager"]
        CM1["Review Release Request"]
        CM2{"Approve Release?"}
    end

    subgraph NewManagerLane["Receiving Department Manager"]
        NM1["Review Candidate"]
        NM2{"Approve Acceptance?"}
    end

    subgraph HRLane["HR Manager"]
        HR1["Finalize Transfer"]
    end

    Finish(["End Process"])

    Start --> E1 --> E2 --> S1
    S1 --> S2
    S2 -->|"No"| S3 --> E4
    S2 -->|"Yes"| S4 --> CM1
    
    CM1 --> CM2
    CM2 -->|"No"| S3
    CM2 -->|"Yes"| S5 --> NM1

    NM1 --> E3 --> NM2
    NM2 -->|"No"| S3
    NM2 -->|"Yes"| HR1
    
    HR1 --> S6 --> E4 --> Finish
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Employee | Nguoi chu dong tim kiem co hoi, nop don luan chuyen va tham gia phong van neu can. |
| 2 | Internal Mobility System | He thong kiem tra tinh hop le, dieu phoi thong bao va luu tru trang thai. |
| 3 | Current Department Manager | Quan ly hien tai xem xet va quyet dinh cho phep nhan vien roi khoi phong ban hay khong. |
| 4 | Receiving Department Manager | Quan ly phong ban moi xem xet, phong van va quyet dinh tiep nhan nhan vien. |
| 5 | HR Manager | Kiem tra cuoi cung va hoan tat cac thu tuc nhan su de chot quy trinh luan chuyen. |
