# Swimlane Diagram — Hotel Property Management System (PMS)

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Guest[" Hotel Guest "]
        A1["Arrive & show ID"]
    end

    subgraph FrontDesk[" Front Desk Agent "]
        F1["Search reservation & scan ID"]
        F2["Collect deposit & confirm"]
        F3["Hand keycard & welcome guest"]
        F4["Notify Housekeeping to expedite"]
    end

    subgraph System[" PMS System "]
        S1["Verify room availability"]
        D1{"Is room clean & ready?"}
        S2["Send key encoding payload"]
    end

    subgraph KeySystem[" Key Card Encoder "]
        K1["Encode keycard & return status"]
    end

    Finish(["End"])

    Start --> A1
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Hotel Guest | Yêu cầu làm thủ tục check-in |
| 2 | Front Desk Agent | Tiếp nhận thông tin và làm thủ tục |
| 3 | PMS System | Xử lý dữ liệu và kiểm tra phòng |
| 4 | Key Card Encoder | Mã hóa thẻ từ phòng |
