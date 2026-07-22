# Swimlane Diagram — IT Asset Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Enterprise Employee"]
        E1["Submit Asset Request for New Laptop"]
        E2["Inspect Hardware & Sign Digital Receipt"]
        E3["Return Laptop upon Job Change"]
    end

    subgraph Lane2["IT Support Technician"]
        T1["Scan Asset Tag & Verify Device Condition"]
        T2["Prepare Hardware Specs & Install Image"]
        T3["Execute Checkin & Reset Device"]
    end

    subgraph Lane3["IT Asset Management System"]
        S1["Verify Inventory Stock Availability"]
        S2{"Is Asset Available in Stock?"}
        S3["Update Asset Status to In Use & Log Assignment"]
        S4["Run Automated Network Scan & Update Specs"]
        S5["Update Asset Status to In Stock & Archived"]
    end

    subgraph Lane4["IT Asset Manager"]
        M1["Approve Equipment Purchase Request"]
        M2["Review Annual Physical Inventory Audit"]
    end

    Finish(["End"])

    Start --> E1 --> S1 --> S2
    
    S2 -->|"No"| M1 --> S1
    S2 -->|"Yes"| T1 --> T2 --> E2 --> S3 --> S4 --> E3 --> T3 --> S5 --> M2 --> Finish
```

## Flow Description | Mô tả luồng xử lý

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Enterprise Employee | Gửi yêu cầu mượn/cấp phát máy tính làm việc, kiểm tra và ký xác nhận nhận thiết bị số, và trả lại thiết bị khi luân chuyển công tác. |
| 2 | IT Support Technician | Quét mã vạch kiểm tra tình trạng máy, cài đặt hệ điều hành/phần mềm chuẩn, thực hiện thao tác bàn giao (Checkout) và thu hồi (Checkin). |
| 3 | IT Asset Management System | Kiểm tra tồn kho tự động, cập nhật trạng thái tài sản thành "In Use" hoặc "In Stock", tự động quét thông số qua mạng và lưu nhật ký. |
| 4 | IT Asset Manager | Phê duyệt mua bổ sung nếu hết hàng tồn kho, thực hiện kiểm kê tài sản định kỳ và quản lý tổng thể danh mục tài sản doanh nghiệp. |
