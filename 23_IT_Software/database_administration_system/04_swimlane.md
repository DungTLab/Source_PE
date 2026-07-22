# Swimlane Diagram — Database Administration System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Application Developer"]
        DEV1["Submit Schema Migration DDL Script"]
        DEV2["Review Lock Warnings & EXPLAIN Plan"]
        DEV3["Confirm Production Execution"]
    end

    subgraph Lane2["Database Administration System"]
        SYS1["Validate SQL Syntax & Lock Timeout Rules"]
        SYS2{"Is DDL Syntax Valid & Low Risk?"}
        SYS3["Create Pre-Migration Point-in-Time Snapshot"]
        SYS4["Apply Migration & Verify Schema Version"]
        SYS5["Send Success Notification & Update Audit"]
    end

    subgraph Lane3["DBMS Engine"]
        ENG1["Execute DDL Statements in Transaction"]
        ENG2{"Exclusive Lock Acquired within 5s?"}
        ENG3["Commit Transaction & Update Catalogs"]
        ENG4["Roll Back Transaction & Release Lock"]
    end

    subgraph Lane4["Database Administrator"]
        DBA1["Review High-Risk DDL Request"]
        DBA2{"Approve Structural Migration?"}
    end

    Finish(["End"])

    Start --> DEV1 --> SYS1 --> SYS2
    
    SYS2 -->|"No - High Risk DDL"| DBA1 --> DBA2
    DBA2 -->|"No - Rejected"| Finish
    DBA2 -->|"Yes"| SYS3

    SYS2 -->|"Yes"| SYS3 --> ENG1 --> ENG2

    ENG2 -->|"Yes"| ENG3 --> SYS4 --> SYS5 --> Finish
    ENG2 -->|"No - Lock Timeout"| ENG4 --> DEV2 --> DEV3 --> ENG1
```

## Flow Description | Mô tả luồng xử lý

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Application Developer | Soạn thảo kịch bản DDL thay đổi cấu trúc bảng, kiểm tra cảnh báo khóa bảng và kế hoạch thực thi, xác nhận chạy trên môi trường thực tế. |
| 2 | Database Administration System | Kiểm tra cú pháp SQL, kiểm soát quy tắc Lock Timeout, tạo bản sao lưu snapshot trước khi chạy, và tự động hóa quy trình cập nhật schema. |
| 3 | DBMS Engine (PostgreSQL/MySQL) | Thực thi các câu lệnh DDL trong transaction, kiểm tra khả năng chiếm khóa đĩa (Exclusive Lock), commit hoặc rollback an toàn nếu gặp sự cố. |
| 4 | Database Administrator (DBA) | Đóng vai trò phê duyệt cấp cao đối với các thao tác DDL nguy cơ cao (DROP, TRUNCATE), đảm bảo an toàn tuyệt đối cho dữ liệu production. |
