# Swimlane Diagram — Student Dormitory Management System

## Mermaid Code
```mermaid
graph TD
    %%{init: {'theme': 'default'}}%%
    subgraph Student [Student]
        ST1[Submit Room Application]
        ST2[Receive Allocation Notification]
        ST3[Sign Contract & Move In]
    end

    subgraph System [Student Dormitory Management System]
        S1[Validate Application Info]
        S2[Check Room Availability]
        S3[Update Room Status & Generate Contract]
        S4[Send Notification via Email/App]
    end

    subgraph Admin [Dormitory Admin]
        A1[Review Application]
        A2[Approve / Reject]
        A3[Allocate Room manually if needed]
    end

    ST1 --> S1
    S1 --> A1
    A1 --> A2
    A2 -- Approved --> S2
    A2 -- Rejected --> S4
    S2 --> A3
    A3 --> S3
    S3 --> S4
    S4 --> ST2
    ST2 --> ST3
```

## Mô tả luồng | Flow Description
1. **Student**: Nộp đơn đăng ký ở ký túc xá qua hệ thống.
2. **System**: Kiểm tra tính hợp lệ của đơn và chuyển đến Ban quản lý.
3. **Admin**: Xem xét hồ sơ và quyết định Phê duyệt (Approve) hoặc Từ chối (Reject). Nếu phê duyệt, Admin tiến hành xếp phòng (nếu hệ thống không tự động xếp).
4. **System**: Cập nhật trạng thái phòng (giảm số giường trống), tạo hợp đồng lưu trú và gửi thông báo cho sinh viên.
5. **Student**: Nhận thông báo xếp phòng thành công, ký hợp đồng và chuẩn bị chuyển vào KTX.
