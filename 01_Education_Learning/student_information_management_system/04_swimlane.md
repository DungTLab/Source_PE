# Swimlane Diagram — Student Information Management System

## Mermaid Code

```mermaid
graph LR
    Start(["▶ Start"])
    
    subgraph STUDENT["👤 Student"]
        S1["Đăng nhập và chọn môn học"]
        S2["Tải tệp bài làm (Assignment) lên"]
        S3["Xác nhận nộp bài"]
    end
    
    subgraph SYSTEM["🖥️ System"]
        Sys1{"Còn hạn nộp bài?"}
        Sys2["Hiển thị cảnh báo quá hạn"]
        Sys3["Lưu bài nộp vào CSDL"]
        Sys4["Chạy hệ thống kiểm tra đạo văn (Plagiarism Check)"]
        Sys5["Gửi thông báo có bài mới"]
        Sys6["Cập nhật điểm và thông báo cho sinh viên"]
    end
    
    subgraph TEACHER["👤 Teacher"]
        T1["Truy cập danh sách bài nộp"]
        T2["Đọc báo cáo tỉ lệ đạo văn"]
        T3["Thực hiện chấm điểm và ghi nhận xét"]
        T4["Lưu và Công bố kết quả điểm"]
    end
    
    End(["⏹ End"])
    
    Start --> S1 --> S2 --> S3 --> Sys1
    Sys1 -->|"Quá hạn"| Sys2 --> S2
    Sys1 -->|"Trong hạn"| Sys3 --> Sys4 --> Sys5 --> T1
    T1 --> T2 --> T3 --> T4 --> Sys6 --> End
```

## Flow Description | Mô tả luồng

Luồng nghiệp vụ: Nộp bài và Chấm điểm bài tập (Assignment Submission & Grading)

| Lane | Actor | Vai trò trong luồng |
|------|-------|---------------------|
| 1 | Student | Khởi tạo quy trình bằng việc tải lên và nộp tệp bài làm. Sinh viên phải đảm bảo bài làm được nộp trong thời hạn cho phép. Kết thúc luồng, sinh viên sẽ nhận được thông báo điểm số. |
| 2 | System | Xử lý logic nghiệp vụ tự động: kiểm tra thời hạn nộp bài (decision node), chặn thao tác nếu quá hạn, lưu trữ file, quét đạo văn tự động để hỗ trợ giảng viên, và điều phối các thông báo giữa hai bên. |
| 3 | Teacher | Tiếp nhận thông báo hệ thống, xem xét bài nộp và báo cáo đạo văn để đưa ra đánh giá. Giảng viên nhập điểm, phản hồi và quyết định publish (công bố) điểm số lên hệ thống cho sinh viên. |
