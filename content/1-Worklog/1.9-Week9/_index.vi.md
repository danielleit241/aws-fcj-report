---
title: "Worklog Tuần 9"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu tuần 9:

- Hoàn thành thiết lập kiến trúc **Microservice** bằng **.NET Aspire** và xây dựng toàn bộ **Shared Libraries** cốt lõi.
- Triển khai hoàn chỉnh **User Service** với tích hợp xác thực **AWS Cognito** và logic **tự động tạo user/profile**.
- Triển khai hoàn chỉnh **Wallet Service** với logic quản lý số dư, quản lý **Money Jar** (Hũ tiền), **Goals Tracking**, và cơ chế **Jar Expiry Processing**.
- Thiết lập **API Gateway**, cấu hình **Polly**, và hoàn tất **Integration Testing** cho luồng End-to-End (User-Wallet).

### Công việc thực hiện trong tuần này:

| Day | Task                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Start Date | Completion Date | Reference Material                                                                                                 |
| :-- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :----------------------------------------------------------------------------------------------------------------- |
| 1   | **Thiết lập Kiến trúc Microservice & Thư viện Chia sẻ** <br> - Khởi tạo giải pháp **.NET Aspire** và cấu trúc hóa **6 Microservices** (User, Wallet, Transaction, Report, Notification, AI Integration Service). <br> - Cấu hình Service Discovery và **Docker Compose** cho môi trường phát triển cục bộ. <br> - Xây dựng các **Shared Libraries** cốt lõi: `Common.DTOs` (với `ApiResponse<T>`), `Common.Authentication` (JWT), `Common.Messaging` (**MassTransit/RabbitMQ**), `Common.Repositories` (UoW Pattern), và `Common.Middlewares` (Rate Limiting, Correlation ID).                       | 03/11/2025 | 03/11/2025      | [Day 1 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-1/day-1.md?ref_type=heads) |
| 2   | **Triển khai User Service & Tích hợp Xác thực** <br> - Thiết lập **PostgreSQL Database** (`user_service_db`) và thiết kế Entity `User` (sử dụng `Guid.CreateVersion7()`, Soft Delete Filter). <br> - Tích hợp xác thực **AWS Cognito** (**JWT Bearer Authentication**) và tạo middleware trích xuất `CognitoSub`. <br> - Triển khai logic **tự động tạo user record** khi đăng nhập lần đầu tiên. <br> - Triển khai Core APIs: `GET /api/users/me` (Lấy/Tạo profile), `PUT /api/users/me` (Cập nhật), và `POST /api/users/complete-profile`.                                                         | 04/11/2025 | 04/11/2025      | [Day 2 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-1/day-2.md?ref_type=heads) |
| 3   | **Wallet Service - Phần 1: Quản lý Ví & Logic Phân bổ** <br> - Thiết lập **PostgreSQL Database** (`wallet_service_db`) và thiết kế Entities `Wallet`, `MoneyJar`, `BudgetPeriod`. <br> - Triển khai **Message Consumer** để **tự động tạo Wallet** khi nhận sự kiện `UserCreated`, đồng thời tạo hũ **"Thu nhập" mặc định**. <br> - Triển khai các Wallet APIs cốt lõi: **Deposit**, **Withdraw** (chỉ từ Available Balance), **Reconcile** (Đồng bộ số dư tổng), và **Soft Delete/Archive Wallet**. <br> - Triển khai **Money Jar CRUD APIs** cơ bản.                                               | 05/11/2025 | 05/11/2025      | [Day 3 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-1/day-3.md?ref_type=heads) |
| 4   | **Wallet Service - Phần 2: Money Jar, Goals & Budget** <br> - Hoàn thành **CRUD** cho Money Jar, bao gồm logic tính toán lại `AvailableBalance` khi update `AllocatedAmount`. <br> - Tích hợp **Goals Tracking** (tính `ProgressPercent`) và logic phát sự kiện `GoalAchieved`. <br> - Triển khai **Jar Operations**: **Deposit**, **Withdraw**, **Transfer** giữa các hũ, và **Reconcile Jar Balance**. <br> - Triển khai **Budget Threshold & Over-Budget Logic** (phát events cảnh báo) và **Jar Expiry Processing Service** (xử lý Income Jar auto-reset, Expense Jar Grace Period/Auto-Return). | 06/11/2025 | 06/11/2025      | [Day 4 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-1/day-4.md?ref_type=heads) |
| 5   | **Tích hợp End-to-End & Thử nghiệm** <br> - Thiết lập **API Gateway** (Routing, CORS, Rate Limiting). <br> - Cấu hình giao tiếp **Service-to-Service** với **HTTP Client Factory** và **Polly** (Retry Policy, Circuit Breaker). <br> - Thực hiện **Integration Testing** cho luồng End-to-End: New User Onboarding, Jar Creation, Wallet/Jar Operations (Deposit/Withdraw/Transfer/Reconcile), và **Goal Achievement**. <br> - Thử nghiệm **Security** (JWT Expiration, Authorization) và **Concurrency** (Balance Updates).                                                                        | 07/11/2025 | 07/11/2025      | [Day 5 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-1/day-5.md?ref_type=heads) |

### Thành tựu Tuần 9:

- **Kiến trúc Nền tảng Microservice Đã Thiết lập:**
  - Sử dụng **.NET Aspire** để định hình kiến trúc Microservice cho 6 dịch vụ.
  - Hoàn thiện bộ **Shared Libraries** cốt lõi, bao gồm cả cấu hình MassTransit/RabbitMQ.
- **User Service Đã Hoàn thiện:**
  - Tích hợp thành công **AWS Cognito** cho cơ chế xác thực JWT.
  - Triển khai logic **tự động tạo user profile** và API hoàn thiện hồ sơ.
- **Wallet Service Đã Hoàn thiện:**
  - Triển khai logic quản lý số dư ba thành phần: **TotalBalance, AllocatedBalance, AvailableBalance**.
  - Hoàn thành **Money Jar Management** với **Goals Tracking** (Target, Progress) và phát sự kiện `GoalAchieved`.
- **Logic Nghiệp vụ Phức tạp Đã triển khai:**
  - Hoàn thiện các nghiệp vụ như **Wallet/Jar Reconciliation** (Đồng bộ số dư) và **Jar Expiry Processing** (cho phép Income Jar auto-reset và Expense Jar có grace period).
- **Hệ thống Ổn định và Đã Tích hợp:**
  - **API Gateway** và cơ chế chịu lỗi **Polly** (Retry, Circuit Breaker) đã được cấu hình.
  - Toàn bộ luồng nghiệp vụ chính đã được **Integration Testing** thành công (từ Cognito -> User Service -> Wallet Service).
