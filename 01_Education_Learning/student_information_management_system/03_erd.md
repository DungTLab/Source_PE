# Conceptual ERD — Student Information Management System

## Mermaid Code

```mermaid
erDiagram
    USER {
        int user_id PK
        string username
        string password_hash
        string role
        string status
        datetime created_at
    }
    STUDENT {
        int student_id PK
        int user_id FK
        string full_name
        date dob
        string email
        string major
    }
    TEACHER {
        int teacher_id PK
        int user_id FK
        string full_name
        string email
        string department
    }
    COURSE {
        int course_id PK
        string course_code
        string course_name
        int credits
        string department
    }
    CLASS {
        int class_id PK
        int course_id FK
        int teacher_id FK
        string semester
        int max_capacity
        string status
    }
    ENROLLMENT {
        int enrollment_id PK
        int student_id FK
        int class_id FK
        datetime enrollment_date
        string status
    }
    GRADE {
        int grade_id PK
        int enrollment_id FK
        decimal assignment_score
        decimal midterm_score
        decimal final_score
        decimal total_score
    }
    ATTENDANCE {
        int attendance_id PK
        int enrollment_id FK
        date session_date
        string status
        string notes
    }
    TUITION_FEE {
        int fee_id PK
        int student_id FK
        string semester
        decimal total_amount
        decimal paid_amount
        string status
    }
    PAYMENT_TRANSACTION {
        int transaction_id PK
        int fee_id FK
        string payment_method
        decimal amount
        datetime payment_date
        string gateway_ref
    }

    USER ||--o| STUDENT : "has profile"
    USER ||--o| TEACHER : "has profile"
    COURSE ||--o{ CLASS : "offered as"
    TEACHER ||--o{ CLASS : "teaches"
    STUDENT ||--o{ ENROLLMENT : "registers for"
    CLASS ||--o{ ENROLLMENT : "includes"
    ENROLLMENT ||--|| GRADE : "receives"
    ENROLLMENT ||--o{ ATTENDANCE : "records"
    STUDENT ||--o{ TUITION_FEE : "incurs"
    TUITION_FEE ||--o{ PAYMENT_TRANSACTION : "paid via"
```

## Entity Description Table | Bảng mô tả Entity

| # | Entity Name | Vietnamese Name | Description | Key Attributes | Main Relationships |
|---|-------------|-----------------|-------------|----------------|-------------------|
| 1 | USER | Người dùng | Lưu trữ tài khoản đăng nhập chung cho toàn bộ hệ thống | user_id, username, role | has profile STUDENT/TEACHER |
| 2 | STUDENT | Sinh viên | Hồ sơ cá nhân và học vụ của sinh viên | student_id, full_name, major | registers for ENROLLMENT, incurs TUITION_FEE |
| 3 | TEACHER | Giảng viên | Hồ sơ thông tin của đội ngũ giảng viên | teacher_id, full_name, department | teaches CLASS |
| 4 | COURSE | Môn học | Thông tin danh mục môn học chung của nhà trường | course_id, course_code, credits | offered as CLASS |
| 5 | CLASS | Lớp học phần | Các lớp học được mở cụ thể theo từng học kỳ | class_id, semester, status | includes ENROLLMENT |
| 6 | ENROLLMENT | Đăng ký học | Lưu thông tin sinh viên đăng ký vào các lớp học phần | enrollment_id, enrollment_date | receives GRADE, records ATTENDANCE |
| 7 | GRADE | Điểm số | Lưu trữ điểm thành phần và điểm tổng kết của môn học | grade_id, total_score | thuộc về 1 ENROLLMENT |
| 8 | ATTENDANCE | Điểm danh | Ghi nhận trạng thái điểm danh theo từng buổi học | attendance_id, session_date | thuộc về 1 ENROLLMENT |
| 9 | TUITION_FEE | Công nợ học phí | Tổng kết số tiền phải đóng và đã đóng của sinh viên | fee_id, total_amount, status | paid via PAYMENT_TRANSACTION |
| 10 | PAYMENT_TRANSACTION | Giao dịch | Lưu log các lần thanh toán học phí qua cổng trực tuyến | transaction_id, amount, date | thuộc về 1 TUITION_FEE |

## Relationship Description | Mô tả Quan hệ

| # | From Entity | Cardinality | To Entity | Relationship Label | Business Explanation |
|---|-------------|-------------|-----------|-------------------|----------------------|
| 1 | USER | one-to-zero-or-one | STUDENT | has profile | Một User có thể liên kết tới một hồ sơ Sinh viên (nếu role là student) |
| 2 | USER | one-to-zero-or-one | TEACHER | has profile | Một User có thể liên kết tới một hồ sơ Giảng viên (nếu role là teacher) |
| 3 | COURSE | one-to-many | CLASS | offered as | Một Môn học có thể được mở thành nhiều Lớp học phần khác nhau trong các kỳ |
| 4 | TEACHER | one-to-many | CLASS | teaches | Một Giảng viên có thể được phân công đứng lớp nhiều Lớp học phần |
| 5 | STUDENT | one-to-many | ENROLLMENT | registers for | Một Sinh viên có thể đăng ký nhiều Lớp học phần (nhiều bản ghi Enrollment) |
| 6 | CLASS | one-to-many | ENROLLMENT | includes | Một Lớp học phần chứa nhiều Sinh viên đăng ký tham gia |
| 7 | ENROLLMENT | one-to-one | GRADE | receives | Mỗi bản ghi đăng ký học của sinh viên ứng với duy nhất một bảng điểm môn đó |
| 8 | ENROLLMENT | one-to-many | ATTENDANCE | records | Mỗi bản ghi đăng ký học có thể có nhiều lượt điểm danh (theo từng buổi) |
| 9 | STUDENT | one-to-many | TUITION_FEE | incurs | Một Sinh viên có nhiều hóa đơn công nợ học phí phát sinh qua các học kỳ |
| 10 | TUITION_FEE | one-to-many | PAYMENT_TRANSACTION | paid via | Một khoản nợ học phí có thể được chia làm nhiều lần thanh toán khác nhau |
