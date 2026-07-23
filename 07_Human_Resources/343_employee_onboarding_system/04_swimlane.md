# Swimlane Diagram — Employee Onboarding System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Pre-boarding Started"])

    subgraph HRCoordinatorLane["HR Coordinator"]
        HR1["Create Onboarding Plan"]
        HR2["Send IT Request"]
    end

    subgraph ITAdminLane["IT Admin"]
        IT1["Receive IT Request"]
        IT2{"Equipment Available?"}
        IT3["Order New Hardware"]
        IT4["Setup Accounts & Laptop"]
    end

    subgraph SystemLane["Onboarding System"]
        S1["Notify IT Admin"]
        S2["Update Task Status"]
        S3["Send Welcome Email with Credentials"]
    end

    subgraph NewHireLane["New Hire"]
        N1["Receive Welcome Email"]
        N2["Log in to Portal"]
    end

    Start --> HR1 --> HR2 --> S1 --> IT1
    
    IT1 --> IT2
    IT2 -->|"No"| IT3 --> IT4
    IT2 -->|"Yes"| IT4
    
    IT4 --> S2 --> S3 --> N1 --> N2 --> Finish(["Day 1 Ready"])
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | HR Coordinator | Nguoi khoi tao quy trinh, xac dinh cac nhu cau IT cho nhan vien moi va chuyen giao tiep. |
| 2 | Onboarding System | Dieu phoi luong cong viec, gui cac thong bao/nhiem vu den dung bo phan va theo doi trang thai. |
| 3 | IT Admin | Chuan bi thiet bi phan cung, tao tai khoan phan mem va cap nhat lai he thong khi hoan thanh. |
| 4 | New Hire | Nhan huong dan dang nhap ban dau tu he thong va thuc hien dang nhap vao ngay lam viec dau tien. |
