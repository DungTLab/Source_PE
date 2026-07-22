# Use Case Diagram — VIP Guest Management System

## Mermaid Code

```mermaid
flowchart LR
    actor_Personal_Butler["Personal Butler"]
    actor_Hotel_Guest["Hotel Guest"]
    actor_Payment_Gateway["Payment Gateway"]
    actor_PMS_Central_Database["PMS Central Database"]
    actor_VIP_Relations_Director["VIP Relations Director"]
    actor_Audit___Compliance_System["Audit & Compliance System"]
    actor_System_Administrator["System Administrator"]
    actor_Notification_Service["Notification Service"]

    subgraph SystemBoundary[" VIP Guest Management System "]
        UC01(["Register VIP Request"])
        UC02(["Process VIP Transaction"])
        UC03(["Update VIP Status"])
        UC04(["Approve VIP Request"])
        UC05(["Generate VIP Report"])
        UC06(["Configure VIP Settings"])
        UC07(["Send Service Notification"])
        UC08(["Search VIP History"])
        UC09(["Synchronize PMS Data"])
        UC10(["Cancel VIP Task"])
        UC11(["Audit VIP Logs"])
        UC12(["Export Performance Analytics"])
    end

    actor_Personal_Butler --> UC01
    UC01 --> actor_Hotel_Guest
    actor_Personal_Butler --> UC02
    UC02 --> actor_Payment_Gateway
    actor_Personal_Butler --> UC03
    UC03 --> actor_PMS_Central_Database
    actor_VIP_Relations_Director --> UC04
    actor_VIP_Relations_Director --> UC05
    UC05 --> actor_Audit___Compliance_System
    actor_System_Administrator --> UC06
    actor_Personal_Butler --> UC07
    UC07 --> actor_Notification_Service
    actor_Personal_Butler --> UC08
    actor_PMS_Central_Database --> UC09
    actor_Personal_Butler --> UC10
    UC10 --> actor_Hotel_Guest
    actor_VIP_Relations_Director --> UC11
    UC11 --> actor_Audit___Compliance_System
    actor_VIP_Relations_Director --> UC12
    UC01 -.->|"<<include>>"| UC02
    UC03 -.->|"<<extend>>"| UC04
```

## Actor Table | Bảng Actor

| # | Actor | Actor Type | Role Description | Related Use Cases |
|---|-------|------------|------------------|-------------------|
| 1 | Personal Butler | Primary | Phụ trách các tác vụ liên quan đến Personal Butler trong hệ thống | UC01, UC02, UC03, UC07, UC08, UC10 |
| 2 | Hotel Guest | Primary | Phụ trách các tác vụ liên quan đến Hotel Guest trong hệ thống | UC01, UC10 |
| 3 | Payment Gateway | Supporting | Phụ trách các tác vụ liên quan đến Payment Gateway trong hệ thống | UC02 |
| 4 | PMS Central Database | Supporting | Phụ trách các tác vụ liên quan đến PMS Central Database trong hệ thống | UC03, UC09 |
| 5 | VIP Relations Director | Primary | Phụ trách các tác vụ liên quan đến VIP Relations Director trong hệ thống | UC04, UC05, UC11, UC12 |
| 6 | Audit & Compliance System | Regulatory | Phụ trách các tác vụ liên quan đến Audit & Compliance System trong hệ thống | UC05, UC11 |
| 7 | System Administrator | Primary | Phụ trách các tác vụ liên quan đến System Administrator trong hệ thống | UC06 |
| 8 | Notification Service | Supporting | Phụ trách các tác vụ liên quan đến Notification Service trong hệ thống | UC07 |

## Use Case Table | Bảng Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Register VIP Request | Personal Butler | Hotel Guest | Create new operational request in VIP Guest Management System. | High |
| 2 | UC02 | Process VIP Transaction | Personal Butler | Payment Gateway | Execute payment or billing charge for VIP Guest Management System. | High |
| 3 | UC03 | Update VIP Status | Personal Butler | PMS Central Database | Modify operational status and update PMS database. | High |
| 4 | UC04 | Approve VIP Request | VIP Relations Director | None | Review and approve high-value or special requests. | High |
| 5 | UC05 | Generate VIP Report | VIP Relations Director | Audit & Compliance System | Compile performance metrics and operational summaries. | High |
| 6 | UC06 | Configure VIP Settings | System Administrator | None | Maintain system master data, roles, and rules. | Medium |
| 7 | UC07 | Send Service Notification | Personal Butler | Notification Service | Dispatch automated alerts to guests or staff. | Medium |
| 8 | UC08 | Search VIP History | Personal Butler | None | Query historical logs and previous records. | Medium |
| 9 | UC09 | Synchronize PMS Data | PMS Central Database | None | Sync real-time guest and room data with central PMS. | High |
| 10 | UC10 | Cancel VIP Task | Personal Butler | Hotel Guest | Cancel active request upon guest cancellation. | Low |
| 11 | UC11 | Audit VIP Logs | VIP Relations Director | Audit & Compliance System | Review user audit trails and security compliance. | Medium |
| 12 | UC12 | Export Performance Analytics | VIP Relations Director | None | Export operational data to Excel or PDF format. | Low |

## Use Case Specification | Đặc tả Use Case

---

### UC01 — Register VIP Request

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Register VIP Request |
| **Actor(s)** | Primary: Personal Butler / Secondary: Hotel Guest |
| **Description** | Thực hiện tiếp nhận và tạo mới yêu cầu nghiệp vụ trong hệ thống VIP Guest Management System. |
| **Precondition** | 1. Người dùng đã đăng nhập hệ thống với quyền hạn hợp lệ.<br>2. Danh mục dịch vụ và khách hàng đã sẵn sàng. |
| **Main Flow** | 1. Personal Butler truy cập màn hình tạo yêu cầu dịch vụ mới.<br>2. System hiển thị biểu mẫu nhập liệu chuẩn hóa.<br>3. Personal Butler chọn thông tin Hotel Guest và chi tiết dịch vụ yêu cầu.<br>4. System kiểm tra tính hợp lệ của thông tin và tình trạng khả dụng.<br>5. Personal Butler nhấn Xác nhận khởi tạo yêu cầu.<br>6. System tạo mới hồ sơ, lưu vào CSDL và gửi thông báo xác nhận. |
| **Alternative Flow** | AF1 — Tạo yêu cầu nhanh từ ứng dụng di động: Guest tự tạo yêu cầu qua mobile app, System tự đồng bộ.<br>AF2 — Đơn yêu cầu theo gói dịch vụ: System tự động điền các hạng mục theo gói hợp đồng. |
| **Exception Flow** | EX1 — Khách hàng chưa đăng ký thông tin lưu trú: System báo lỗi và yêu cầu xác minh phòng trước.<br>EX2 — Dịch vụ tạm ngưng phục vụ: System cảnh báo không khả dụng và gợi ý dịch vụ thay thế. |
| **Postcondition** | Hồ sơ yêu cầu được tạo ở trạng thái Pending/Active, mã định danh duy nhất được khởi tạo. |
| **Business Rule** | BR1: Mọi yêu cầu khởi tạo phải gắn liền với mã khách hàng hoặc phòng cụ thể. |

---

### UC02 — Process VIP Transaction

| Field | Detail |
|-------|--------|
| **UC ID** | UC02 |
| **Use Case Name** | Process VIP Transaction |
| **Actor(s)** | Primary: Personal Butler / Secondary: Payment Gateway |
| **Description** | Xử lý thanh toán hoặc ghi nợ tài khoản dịch vụ cho VIP Guest Management System. |
| **Precondition** | 1. Yêu cầu dịch vụ đã hoàn thành hoặc ở trạng thái chờ thanh toán.<br>2. Cổng thanh toán hoặc Folio PMS đang kết nối. |
| **Main Flow** | 1. Personal Butler mở yêu cầu cần thanh toán và kiểm tra bảng chi tiết chi phí.<br>2. System tổng hợp giá dịch vụ, thuế VAT và phí phục vụ.<br>3. Personal Butler chọn phương thức thanh toán (Ghi nợ phòng Folio / Tiền mặt / Thẻ ngân hàng).<br>4. System gửi lệnh tính phí sang Folio PMS hoặc Payment Gateway.<br>5. Payment Gateway trả về kết quả giao dịch thành công.<br>6. System cập nhật trạng thái đơn dịch vụ thành Paid và in hóa đơn thanh toán. |
| **Alternative Flow** | AF1 — Ghi nợ về tài khoản công ty: Personal Butler chọn nợ công ty, kiểm tra hạn mức nợ hợp lệ.<br>AF2 — Thanh toán bằng voucher: System trừ giá trị voucher trước khi tính số tiền còn lại. |
| **Exception Flow** | EX1 — Thẻ ngân hàng từ chối: System báo giao dịch thất bại, yêu cầu quẹt thẻ khác.<br>EX2 — Folio bị khóa không cho ghi nợ: System yêu cầu liên hệ Lễ tân mở khóa Folio. |
| **Postcondition** | Giao dịch được hạch toán, hóa đơn được xuất, trạng thái hoàn tất thanh toán. |
| **Business Rule** | BR1: Mọi giao dịch tài chính phải có mã giao dịch duy nhất từ cổng thanh toán hoặc PMS. |

---

### UC03 — Update VIP Status

| Field | Detail |
|-------|--------|
| **UC ID** | UC03 |
| **Use Case Name** | Update VIP Status |
| **Actor(s)** | Primary: Personal Butler / Secondary: PMS Central Database |
| **Description** | Cập nhật trạng thái tiến độ thực hiện của nghiệp vụ. |
| **Precondition** | 1. Hồ sơ nghiệp vụ đang ở trạng thái hoạt động.<br>2. Nhân viên có quyền cập nhật tiến độ. |
| **Main Flow** | 1. Personal Butler mở danh sách công việc được phân công.<br>2. System hiển thị các yêu cầu đang thực hiện.<br>3. Personal Butler chọn yêu cầu và thay đổi trạng thái sang In-Progress hoặc Completed.<br>4. System ghi nhận thời điểm cập nhật và nhân viên thực hiện.<br>5. System đồng bộ trạng thái mới sang PMS Central Database.<br>6. System gửi thông báo trạng thái mới tới khách hàng. |
| **Alternative Flow** | AF1 — Tạm dừng thực hiện: Nhân viên chọn trạng thái On-Hold và nhập lý do chờ phụ tùng/vật tư. |
| **Exception Flow** | EX1 — Mất kết nối PMS: System lưu trạng thái tạm thời và thử đồng bộ lại sau. |
| **Postcondition** | Trạng thái nghiệp vụ được cập nhật chính xác trên toàn hệ thống. |
| **Business Rule** | BR1: Chỉ nhân viên được phân công mới có quyền chuyển trạng thái Completed. |

---

### UC04 — Approve VIP Request

| Field | Detail |
|-------|--------|
| **UC ID** | UC04 |
| **Use Case Name** | Approve VIP Request |
| **Actor(s)** | Primary: VIP Relations Director / Secondary: None |
| **Description** | Quản lý xem xét và phê duyệt các yêu cầu dịch vụ đặc biệt hoặc có giá trị cao. |
| **Precondition** | 1. Có yêu cầu ở trạng thái Pending Approval.<br>2. Quản lý có thẩm quyền duyệt. |
| **Main Flow** | 1. VIP Relations Director truy cập danh sách yêu cầu chờ duyệt.<br>2. System hiển thị chi tiết nội dung, chi phí và lý do yêu cầu.<br>3. VIP Relations Director kiểm tra tính hợp lệ và hạn mức cho phép.<br>4. VIP Relations Director nhấn Phê duyệt (Approve).<br>5. System chuyển trạng thái yêu cầu sang Approved và chuyển tiếp cho nhân viên xử lý.<br>6. System lưu lại lịch sử phê duyệt của quản lý. |
| **Alternative Flow** | AF1 — Từ chối phê duyệt (Reject): Quản lý nhập lý do từ chối, System gửi thông báo hủy tới người tạo yêu cầu. |
| **Exception Flow** | EX1 — Quá hạn thời gian phê duyệt: System gửi cảnh báo nhắc nhở tới Quản lý trực ca. |
| **Postcondition** | Yêu cầu được chuyển sang bước thực thi tiếp theo. |
| **Business Rule** | BR1: Các giao dịch có giá trị vượt hạn mức chuẩn bắt buộc phải qua bước phê duyệt. |

---

### UC05 — Generate VIP Report

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Generate VIP Report |
| **Actor(s)** | Primary: VIP Relations Director / Secondary: Audit & Compliance System |
| **Description** | Tổng hợp và xuất báo cáo hiệu suất hoạt động nghiệp vụ. |
| **Precondition** | 1. Dữ liệu vận hành trong khoảng thời gian báo cáo đã được lưu trữ đầy đủ. |
| **Main Flow** | 1. VIP Relations Director chọn phân hệ Báo cáo và chọn khoảng thời gian (Ngày/Tuần/Tháng).<br>2. System truy vấn dữ liệu vận hành từ CSDL trung tâm.<br>3. System tính toán các chỉ số KPI, tổng doanh thu và biểu đồ xu hướng.<br>4. System xuất màn hình báo cáo tổng quan trực quan.<br>5. VIP Relations Director chọn Tải báo cáo dạng PDF/Excel.<br>6. System gửi bản sao báo cáo tới Audit & Compliance System. |
| **Alternative Flow** | AF1 — Đặt lịch gửi báo cáo tự động: Quản lý thiết lập gửi báo cáo định kỳ qua email hàng sáng. |
| **Exception Flow** | EX1 — Không có dữ liệu trong khoảng thời gian chọn: System hiển thị thông báo "Không tìm thấy dữ liệu phù hợp". |
| **Postcondition** | Báo cáo được khởi tạo và lưu vết trong hệ thống. |
| **Business Rule** | BR1: Báo cáo tài chính nghiệp vụ phải đối soát khớp 100% với dữ liệu hạch toán. |

