# Swimlane Diagram — Payroll Management System

## Mermaid Code

```mermaid
%%{init: {'theme': 'default'}}%%
flowchart LR
    Start(["Start Month End"])

    subgraph PayrollManagerLane["Payroll Manager"]
        P1["Sync Attendance Data"]
        P2["Calculate Payroll"]
        P3["Review Draft Payroll"]
        P4["Disburse Salary"]
    end

    subgraph SystemLane["Payroll System"]
        S1["Pull data from Time System"]
        S2["Apply Tax & Deduction Rules"]
        S3["Generate Draft & Total Cost"]
        S4["Lock Payroll Period"]
        S5["Send API Request to Bank"]
        S6["Publish Payslips to Employees"]
    end

    subgraph FinanceDirectorLane["Finance Director"]
        F1["Review Total Payroll Cost"]
        F2{"Approve?"}
    end

    subgraph BankSystemLane["Bank System"]
        B1["Process Salary Transfers"]
        B2["Return Status codes"]
    end

    Start --> P1 --> S1 --> P2 --> S2 --> S3 --> P3 --> F1
    
    F1 --> F2
    F2 -->|"No (Reject)"| P3
    F2 -->|"Yes (Approve)"| S4 --> P4
    
    P4 --> S5 --> B1 --> B2 --> S6 --> Finish(["Payroll Completed"])
```

## Flow Description | Mo ta luong

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Payroll Manager | Khoi tao qua trinh dong bo du lieu, chay tinh toan va cuoi cung la nhan nut chi tra. |
| 2 | Payroll System | Chay cac thuat toan tinh toan phuc tap, luu tru du lieu, tich hop ngan hang va phan phoi phieu luong. |
| 3 | Finance Director | Kiem soat dong tien, xet duyet tong ngan sach chi tra truoc khi tien thuc su duoc chuyen ra khoi cong ty. |
| 4 | Bank System | He thong ngoai, thuc thi viec chuyen khoan thuc te den tai khoan cua nhan vien va bao cao ket qua. |
