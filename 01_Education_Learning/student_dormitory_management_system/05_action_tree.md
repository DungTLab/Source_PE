# Action Tree — Student Dormitory Management System

## Mermaid Code
```mermaid
graph TD
    %%{init: {'theme': 'default'}}%%
    Root[Student Dormitory Management System]
    
    M1[Room Management]
    M2[Tenant Management]
    M3[Billing & Finance]
    M4[Maintenance Management]
    
    Root --> M1
    Root --> M2
    Root --> M3
    Root --> M4
    
    M1 --> M1_1[Add/Edit Buildings & Rooms]
    M1 --> M1_2[Track Room Availability]
    
    M2 --> M2_1[Process Applications]
    M2 --> M2_2[Manage Contracts]
    M2 --> M2_3[View Student Profiles]
    
    M3 --> M3_1[Generate Invoices]
    M3 --> M3_2[Process Payments]
    M3 --> M3_3[Track Unpaid Bills]
    
    M4 --> M4_1[Log Maintenance Requests]
    M4 --> M4_2[Assign Tasks to Staff]
    M4 --> M4_3[Update Resolution Status]
```

## Mô tả | Description
- **Room Management (Quản lý phòng ốc)**: Khởi tạo và thiết lập các tòa nhà, phòng ở, theo dõi trạng thái số giường trống của từng phòng.
- **Tenant Management (Quản lý người lưu trú)**: Tiếp nhận và xử lý đơn đăng ký của sinh viên, quản lý hợp đồng thuê và hồ sơ thông tin sinh viên đang lưu trú.
- **Billing & Finance (Quản lý hóa đơn & Tài chính)**: Sinh hóa đơn định kỳ (tiền phòng, điện, nước), xử lý thanh toán và theo dõi các hóa đơn đang nợ.
- **Maintenance Management (Quản lý bảo trì)**: Tiếp nhận các báo cáo hỏng hóc từ sinh viên, phân công nhân viên kỹ thuật và cập nhật trạng thái sửa chữa.
