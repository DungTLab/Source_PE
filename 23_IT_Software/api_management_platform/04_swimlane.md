# Swimlane Diagram — API Management Platform

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Third-Party Client App"]
        C1["Send HTTP Request with Bearer Token"]
        C2["Receive HTTP 429 / 401 Error & Retry"]
        C3["Receive HTTP 200 OK JSON Response"]
    end

    subgraph Lane2["API Gateway Proxy"]
        G1["Receive Inbound HTTP Request"]
        G2["Extract Token & Check Route Mapping"]
        G3["Apply Header & Payload Transformation"]
        G4["Proxy Request to Upstream URL"]
        G5["Format Response & Send to Client"]
    end

    subgraph Lane3["Security & Rate Limiter Engine"]
        S1["Verify OAuth JWT & Scope Claims"]
        S2{"Is Token Valid & Authorized?"}
        S3["Check Redis Sliding Window Counter"]
        S4{"Exceeds RPS Rate Limit?"}
    end

    subgraph Lane4["Backend Microservice"]
        M1["Process Business Logic Query"]
        M2["Return JSON Payload & Status 200"]
    end

    Finish(["End"])

    Start --> C1 --> G1 --> G2 --> S1 --> S2
    
    S2 -->|"No - Invalid Token"| C2 --> Finish
    S2 -->|"Yes"| S3 --> S4

    S4 -->|"Yes - Rate Limited"| C2
    S4 -->|"No"| G3 --> G4 --> M1 --> M2 --> G5 --> C3 --> Finish
```

## Flow Description | Mô tả luồng xử lý

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Third-Party Client App | Khởi tạo yêu cầu HTTP đính kèm mã Token, nhận phản hồi kết quả JSON thành công hoặc xử lý thử lại nếu bị chối do quá cước/hết hạn. |
| 2 | API Gateway Proxy | Tiếp nhận lưu lượng HTTP đầu vào, khớp tuyến đường (Routing), thực hiện biến đổi header/dữ liệu và chuyển tiếp (Proxy) yêu cầu tới ứng dụng Backend. |
| 3 | Security & Rate Limiter Engine | Xác thực chữ ký số JWT và quyền hạn Scope, kiểm tra hạn mức tần suất truy cập (RPS) trên cache Redis và từ chối truy cập nếu vi phạm. |
| 4 | Backend Microservice | Tiếp nhận các yêu cầu đã qua kiểm duyệt an ninh từ Gateway, thực thi logic nghiệp vụ và trả về kết quả JSON cho Gateway. |
