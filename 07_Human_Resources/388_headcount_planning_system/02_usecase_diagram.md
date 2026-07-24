# Use Case Diagram — Headcount Planning System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    actor_DeptManager["Department Manager"]
    actor_HRManager["HR Manager"]
    actor_FinanceManager["Finance Manager"]
    actor_ExecutiveBoard["Executive Board"]
    actor_Admin["System Admin"]

    subgraph SystemBoundary["Headcount Planning System"]
        UC01(["Login"])
        UC02(["Create Planning Cycle"])
        UC03(["Submit Headcount Request"])
        UC04(["Review HR Alignment"])
        UC05(["Allocate Budget"])
        UC06(["Approve Annual Plan"])
        UC07(["View Current Headcount"])
        UC08(["Generate Headcount Report"])
        UC09(["Export Data"])
        UC10(["Manage Users & Roles"])
        UC11(["Configure System Settings"])
        UC12(["Compare Actual vs Planned"])
        UC13(["Adjust Headcount Plan"])
    end

    actor_DeptManager --> UC01
    actor_DeptManager --> UC03
    actor_DeptManager --> UC07

    actor_HRManager --> UC01
    actor_HRManager --> UC02
    actor_HRManager --> UC04
    actor_HRManager --> UC08
    actor_HRManager --> UC12
    actor_HRManager --> UC13

    actor_FinanceManager --> UC01
    actor_FinanceManager --> UC05
    actor_FinanceManager --> UC12

    actor_ExecutiveBoard --> UC01
    actor_ExecutiveBoard --> UC06

    actor_Admin --> UC01
    actor_Admin --> UC10
    actor_Admin --> UC11

    UC02 -.->|«include»| UC01
    UC03 -.->|«include»| UC01
    UC04 -.->|«include»| UC01
    UC05 -.->|«include»| UC01
    UC06 -.->|«include»| UC01
    UC08 -.->|«include»| UC01

    UC09 -.->|«extend»| UC08
```

## Actor Table | Bang Actor

| # | Actor | Actor Type | Role Description | Related Use Cases |
|---|-------|------------|------------------|-------------------|
| 1 | Department Manager | Primary | Nguoi quan ly phong ban de xuat nhan su | UC01, UC03, UC07 |
| 2 | HR Manager | Primary | Nhan su quan ly quy trinh va du lieu chung | UC01, UC02, UC04, UC08, UC12, UC13 |
| 3 | Finance Manager | Primary | Quan ly ngan sach cho ke hoach nhan su | UC01, UC05, UC12 |
| 4 | Executive Board | Primary | Ban giam doc phe duyet ke hoach cuoi cung | UC01, UC06 |
| 5 | System Admin | Primary | Quan tri vien he thong | UC01, UC10, UC11 |

## Use Case Table | Bang Use Case

| # | UC ID | Use Case Name | Primary Actor | Secondary Actor | Description | Priority |
|---|-------|---------------|---------------|-----------------|-------------|----------|
| 1 | UC01 | Login | Department Manager | | Authenticate user access | High |
| 2 | UC02 | Create Planning Cycle | HR Manager | | Initiate a new headcount planning cycle | High |
| 3 | UC03 | Submit Headcount Request | Department Manager | | Request new headcount for a department | High |
| 4 | UC04 | Review HR Alignment | HR Manager | | Review requests for HR policy compliance | High |
| 5 | UC05 | Allocate Budget | Finance Manager | | Allocate and approve budget for requests | High |
| 6 | UC06 | Approve Annual Plan | Executive Board | | Final approval of the entire headcount plan | High |
| 7 | UC07 | View Current Headcount | Department Manager | | View existing team headcount data | Medium |
| 8 | UC08 | Generate Headcount Report | HR Manager | | Create statistical headcount reports | Medium |
| 9 | UC09 | Export Data | HR Manager | | Download reports as files | Low |
| 10| UC10 | Manage Users & Roles | System Admin | | Manage user access and permissions | High |
| 11| UC11 | Configure System Settings | System Admin | | Update system-wide preferences | Medium |
| 12| UC12 | Compare Actual vs Planned | HR Manager | Finance Manager | Track variations against plan | Medium |
| 13| UC13 | Adjust Headcount Plan | HR Manager | | Modify approved plans during the year | Low |

## Use Case Specification | Dac ta Use Case

---

### UC01 — Login

| Field | Detail |
|-------|--------|
| **UC ID** | UC01 |
| **Use Case Name** | Login |
| **Actor(s)** | Primary: Department Manager, HR Manager, Finance Manager, Executive Board, System Admin |
| **Description** | Cho phep nguoi dung xac thuc de dang nhap vao he thong. |
| **Precondition** | 1. Nguoi dung phai co tai khoan hop le.<br> 2. He thong dang hoat dong binh thuong. |
| **Main Flow** | 1. Actor mo trang dang nhap.<br> 2. System hien thi form dang nhap.<br> 3. Actor nhap username va password.<br> 4. Actor nhan nut Submit.<br> 5. System xac thuc thong tin.<br> 6. System chuyen huong den trang chu. |
| **Alternative Flow** | **AF1** — Quen mat khau: Neu Actor chon "Forgot Password", System kich hoat chuc nang khoi phuc mat khau. |
| **Exception Flow** | **EX1** — Sai thong tin: Neu xac thuc that bai, System hien thi thong bao loi.<br> **EX2** — Tai khoan bi khoa: Neu nhap sai 5 lan, System khoa tai khoan. |
| **Postcondition** | Nguoi dung dang nhap thanh cong. |
| **Business Rule** | **BR1**: Mat khau phai duoc ma hoa.<br> **BR2**: Phien dang nhap tu dong het han sau 30 phut. |

---

### UC02 — Create Planning Cycle

| Field | Detail |
|-------|--------|
| **UC ID** | UC02 |
| **Use Case Name** | Create Planning Cycle |
| **Actor(s)** | Primary: HR Manager |
| **Description** | Khoi tao mot ky ke hoach nhan su moi cho nam hoac quy tiep theo. |
| **Precondition** | 1. HR Manager da dang nhap (Include UC01).<br> 2. Khong co ky ke hoach nao dang mo trung thoi gian. |
| **Main Flow** | 1. Actor chon "Create Planning Cycle".<br> 2. System hien thi form tao ky ke hoach.<br> 3. Actor nhap ten, thoi gian bat dau/ket thuc va han chot nop don.<br> 4. Actor nhan Submit.<br> 5. System kiem tra tinh hop le.<br> 6. System luu va kich hoat ky ke hoach, gui thong bao den cac Manager. |
| **Alternative Flow** | **AF1** — Huy tao: Actor chon Cancel de thoat ma khong luu. |
| **Exception Flow** | **EX1** — Trung thoi gian: System thong bao loi neu thoi gian bi chong cheo voi ky truoc. |
| **Postcondition** | Mot ky ke hoach moi duoc tao voi trang thai "Active". |
| **Business Rule** | **BR1**: Moi thoi diem chi co toi da mot ky ke hoach Active cho cung mot don vi. |

---

### UC03 — Submit Headcount Request

| Field | Detail |
|-------|--------|
| **UC ID** | UC03 |
| **Use Case Name** | Submit Headcount Request |
| **Actor(s)** | Primary: Department Manager |
| **Description** | Cho phep Department Manager nop don yeu cau bo sung nhan su. |
| **Precondition** | 1. Dept Manager da dang nhap (Include UC01).<br> 2. Co mot ky ke hoach dang "Active". |
| **Main Flow** | 1. Actor chon "New Headcount Request".<br> 2. System hien thi form yeu cau.<br> 3. Actor chon vi tri, so luong, muc luong du kien va ly do.<br> 4. Actor nhan Submit.<br> 5. System xac nhan du lieu.<br> 6. System luu yeu cau voi trang thai "Pending HR" va thong bao HR. |
| **Alternative Flow** | **AF1** — Luu nhap: Actor chon "Save Draft" de luu tam thoi. |
| **Exception Flow** | **EX1** — Qua han: Neu da qua han chot cua ky ke hoach, System chan Submit va thong bao loi. |
| **Postcondition** | Yeu cau nhan su duoc luu vao he thong voi trang thai cho duyet. |
| **Business Rule** | **BR1**: Tat ca yeu cau phai nam trong ky ke hoach hop le. |

---

### UC04 — Review HR Alignment

| Field | Detail |
|-------|--------|
| **UC ID** | UC04 |
| **Use Case Name** | Review HR Alignment |
| **Actor(s)** | Primary: HR Manager |
| **Description** | HR Manager kiem tra xem yeu cau nhan su co phu hop voi chinh sach HR hay khong. |
| **Precondition** | 1. HR Manager da dang nhap (Include UC01).<br> 2. Co yeu cau o trang thai "Pending HR". |
| **Main Flow** | 1. Actor chon xem danh sach yeu cau cho duyet.<br> 2. System hien thi danh sach "Pending HR".<br> 3. Actor chon mot yeu cau de xem chi tiet.<br> 4. Actor nhan "Approve" de dong y khao sat HR.<br> 5. System cap nhat trang thai thanh "Pending Finance" va thong bao Finance Manager. |
| **Alternative Flow** | **AF1** — Tu choi: Actor chon "Reject" va nhap ly do. System cap nhat trang thai thanh "Rejected by HR". |
| **Exception Flow** | **EX1** — Don da xu ly: Neu don da bi huy, System thong bao "Request unavailable". |
| **Postcondition** | Yeu cau chuyen sang trang thai cho Tai chinh hoac bi tu choi. |
| **Business Rule** | **BR1**: HR phai duyet truoc khi chuyen sang cho Finance. |

---

### UC05 — Allocate Budget

| Field | Detail |
|-------|--------|
| **UC ID** | UC05 |
| **Use Case Name** | Allocate Budget |
| **Actor(s)** | Primary: Finance Manager |
| **Description** | Finance Manager phan bo va phe duyet ngan sach cho yeu cau nhan su. |
| **Precondition** | 1. Finance Manager da dang nhap (Include UC01).<br> 2. Co yeu cau o trang thai "Pending Finance". |
| **Main Flow** | 1. Actor vao man hinh "Budget Approval".<br> 2. System hien thi cac yeu cau "Pending Finance".<br> 3. Actor xem chi tiet chi phi uoc tinh.<br> 4. Actor nhan "Approve Budget".<br> 5. System cap nhat trang thai "Approved by Finance" va thong bao cac ben. |
| **Alternative Flow** | **AF1** — Yeu cau dieu chinh: Actor chon "Request Revision", System chuyen don ve trang thai "Draft" kem ghi chu. |
| **Exception Flow** | **EX1** — Vuot ngan sach: Neu vuot qua ngan sach tong, System canh bao nhung van cho phep neu duoc vuot quyen (override). |
| **Postcondition** | Yeu cau duoc phe duyet ngan sach va cho Executive Board tong duyet. |
| **Business Rule** | **BR1**: Yeu cau chi chinh thuc hoan tat khi ca HR va Finance deu thong qua. |
