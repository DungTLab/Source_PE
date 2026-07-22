# Source_PE — Huong dan su dung

> He thong tai lieu thi tu dong cho mon **SWR302**
> AI dong vai BA Senior tu dong sinh diagram Mermaid + bang mo ta song ngu
>
> **Version**: 3.0 | **Updated**: 2026-07-22

---

## Cau truc thu muc

```text
Source_PE/
|-- README.md              <-- File nay
|-- AGENTS.md              <-- Dinh nghia vai tro AI (BA Senior) + tieu chuan chat luong
|-- PROMPT.md              <-- Master prompt de goi AI tao he thong moi
|
|-- 01_Education_Learning/         <-- Moi domain = 1 folder
|   |-- _systems_list.md           <-- Danh sach he thong thuoc domain
|   |-- student_information_system/    <-- Moi he thong = 1 folder con
|   |   |-- 01_context_diagram.md
|   |   |-- 02_usecase_diagram.md
|   |   |-- 03_erd.md
|   |   |-- 04_swimlane.md
|   |   |-- 05_action_tree.md
|   |-- ...
|
|-- 02_Healthcare_Medical/
|-- 03_Finance_Banking/
|-- ... (den 25_Miscellaneous_Emerging)
```

---

## Cach tao tai lieu cho he thong moi

### Buoc 1: Mo PROMPT.md
Doc file `PROMPT.md` va copy phan prompt mau (trong khung ``` ```).

### Buoc 2: Dien ten he thong
Thay `[TEN HE THONG]` bang ten he thong trong de thi.
Neu co de bai, paste them noi dung de vao phia sau.

### Buoc 3: Gui cho AI (Gemini/Antigravity)
Paste prompt vao chat -> AI tu xac dinh domain -> tao folder trong domain -> tao 5 file.

### Buoc 4: Dung trong draw.io
1. Mo [draw.io Desktop](https://github.com/jgraph/drawio-desktop/releases)
2. **Extras** -> **Edit Diagram** (hoac Insert -> Advanced -> Mermaid)
3. Paste Mermaid code -> **OK**
4. Tu dong render so do

---

## Y nghia 5 file output

| File | So do | Muc dich | Tieu chuan v3.0 |
|------|-------|----------|-----------------|
| 01_context_diagram.md | Context Diagram | Xac dinh boundary & external actors | >= 6 actors, system hinh tron, actor hinh vuong |
| 02_usecase_diagram.md | Use Case Diagram | Liet ke UC + dac ta 4-5 UC chinh | >= 12 UC, 10 truong/UC spec |
| 03_erd.md | Conceptual ERD | Mo hinh du lieu cot loi | >= 8 entities, 4-8 attributes/entity |
| 04_swimlane.md | Swimlane Diagram | Luong xu ly theo vai tro | >= 3 lanes, decision node |
| 05_action_tree.md | Action Tree | Phan ra chuc nang he thong | >= 5 modules, >= 3 actions/module |

---

## Cac he thong da co tai lieu

| # | Ten he thong | Domain | Folder | Ngay tao |
|---|-------------|--------|--------|----------|
| 1 | Restaurant Management System at Vincom | 05_Food_Restaurant | restaurant_management_vincom/ | 2026-07-21 |

*(Cap nhat bang nay moi khi them he thong moi)*

---

## Convention dat ten folder

- Dung `snake_case` (viet thuong, cach nhau bang `_`)
- Khong dung dau tieng Viet
- Dat ten theo **ten he thong**, khong theo ten de bai

| Dung | Sai |
|------|-----|
| `hospital_management_system` | `Hospital Management` |
| `online_banking_system` | `he thong ngan hang` |
| `hotel_booking_system` | `HotelBooking` |

---

## Lien he & dong gop

Neu format can chinh sua, cap nhat `AGENTS.md` va `PROMPT.md` -> AI se tu ap dung cho cac he thong tiep theo.
