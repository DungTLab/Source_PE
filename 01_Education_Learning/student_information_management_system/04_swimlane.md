# Swimlane Diagram — Student Information Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])
    
    subgraph STUDENT["Student"]
        S1["Login and select course assignment"]
        S2["Upload assignment file"]
        S3["Confirm assignment submission"]
    end
    
    subgraph SYSTEM["System"]
        Sys1{"Submission deadline met?"}
        Sys2["Display deadline violation alert"]
        Sys3["Store submission file in database"]
        Sys4["Run automated plagiarism detection"]
        Sys5["Send new submission alert to teacher"]
        Sys6["Update grade status and notify student"]
    end
    
    subgraph TEACHER["Teacher"]
        T1["Access assignment submission list"]
        T2["Review plagiarism report details"]
        T3["Evaluate work and enter grade & feedback"]
        T4["Publish grade results"]
    end
    
    Finish(["End"])
    
    Start --> S1 --> S2 --> S3 --> Sys1
    Sys1 -->|"Overdue"| Sys2 --> S2
    Sys1 -->|"Valid"| Sys3 --> Sys4 --> Sys5 --> T1
    T1 --> T2 --> T3 --> T4 --> Sys6 --> Finish
```

## Flow Description | Mô tả luồng

Luồng nghiệp vụ: Nộp bài và Chấm điểm bài tập (Assignment Submission & Grading)

| Lane | Actor | Role in Flow / Vai trò trong luồng |
|------|-------|------------------------------------|
| 1 | Student | Khởi tạo quy trình bằng việc chọn bài tập, tải tệp bài làm lên và xác nhận nộp bài. Sinh viên phải bảo đảm nộp bài trước hạn chót. Cuối luồng, sinh viên nhận thông báo kết quả điểm số. |
| 2 | System | Xử lý logic nghiệp vụ tự động: kiểm tra thời hạn nộp bài (decision node), hiển thị cảnh báo nếu quá hạn, lưu trữ file bài làm, chạy tự động kiểm tra đạo văn, gửi thông báo cho giảng viên và cập nhật điểm số. |
| 3 | Teacher | Tiếp nhận danh sách bài nộp, tham khảo báo cáo đạo văn, nhập điểm cùng nhận xét chi tiết, và xuất bản (publish) kết quả cho sinh viên. |
