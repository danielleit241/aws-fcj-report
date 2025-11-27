---
title: "Worklog Tuần 10"
date: "2025-09-09"
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---

### Mục tiêu tuần 10:

- Hoàn thành việc triển khai **Transaction Service** (Tạo, Đọc, Cập nhật, Xóa) với luồng dòng tiền được kiểm soát chặt chẽ qua **Wallet Service** (kiểm tra và trừ số dư).
- Triển khai các tính năng nâng cao cho Transaction: **Lọc nâng cao**, **Tìm kiếm toàn văn**, **Tags**, và hỗ trợ **AI Metadata**.
- Thiết lập hoàn chỉnh **Kiến trúc hướng sự kiện (Event-Driven Architecture)** sử dụng **RabbitMQ/MassTransit** để đồng bộ dữ liệu giữa các dịch vụ (User, Wallet, Transaction).
- Hoàn tất **Integration Testing** và **tối ưu hóa hiệu năng** cho các luồng nghiệp vụ cốt lõi.

### Các công việc cần triển khai trong tuần này:

| Day | Task                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Start Date | Completion Date | Reference Material                                                                                                 |
| :-- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :----------------------------------------------------------------------------------------------------------------- |
| 1   | **Thiết lập Kiến trúc Microservice & Thư viện Chia sẻ** <br> - Khởi tạo giải pháp **.NET Aspire** và cấu trúc hóa **6 Microservices** (User, Wallet, Transaction, Report, Notification, AI Integration Service). <br> - Cấu hình Service Discovery và **Docker Compose** cho môi trường phát triển cục bộ. <br> - Xây dựng các **Shared Libraries** cốt lõi: `Common.DTOs` (với `ApiResponse<T>`), `Common.Authentication` (JWT), `Common.Messaging` (**MassTransit/RabbitMQ**), `Common.Repositories` (UoW Pattern), và `Common.Middlewares` (Rate Limiting, Correlation ID).                       | 10/11/2025 | 10/11/2025      | [Day 1 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-1/day-1.md?ref_type=heads) |
| 2   | **Triển khai User Service & Tích hợp Xác thực** <br> - Thiết lập **PostgreSQL Database** (`user_service_db`) và thiết kế Entity `User` (sử dụng `Guid.CreateVersion7()`, Soft Delete Filter). <br> - Tích hợp xác thực **AWS Cognito** (**JWT Bearer Authentication**) và tạo middleware trích xuất `CognitoSub`. <br> - Triển khai logic **tự động tạo user record** khi đăng nhập lần đầu tiên. <br> - Triển khai Core APIs: `GET /api/users/me` (Lấy/Tạo profile), `PUT /api/users/me` (Cập nhật), và `POST /api/users/complete-profile`.                                                         | 11/11/2025 | 11/11/2025      | [Day 2 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-1/day-2.md?ref_type=heads) |
| 3   | **Wallet Service - Phần 1: Quản lý Ví & Logic Phân bổ** <br> - Thiết lập **PostgreSQL Database** (`wallet_service_db`) và thiết kế Entities `Wallet`, `MoneyJar`, `BudgetPeriod`. <br> - Triển khai **Message Consumer** để **tự động tạo Wallet** khi nhận sự kiện `UserCreated`, đồng thời tạo hũ **"Thu nhập" mặc định**. <br> - Triển khai các Wallet APIs cốt lõi: **Deposit**, **Withdraw** (chỉ từ Available Balance), **Reconcile** (Đồng bộ số dư tổng), và **Soft Delete/Archive Wallet**. <br> - Triển khai **Money Jar CRUD APIs** cơ bản.                                               | 12/11/2025 | 12/11/2025      | [Day 3 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-1/day-3.md?ref_type=heads) |
| 4   | **Wallet Service - Phần 2: Money Jar, Goals & Budget** <br> - Hoàn thành **CRUD** cho Money Jar, bao gồm logic tính toán lại `AvailableBalance` khi update `AllocatedAmount`. <br> - Tích hợp **Goals Tracking** (tính `ProgressPercent`) và logic phát sự kiện `GoalAchieved`. <br> - Triển khai **Jar Operations**: **Deposit**, **Withdraw**, **Transfer** giữa các hũ, và **Reconcile Jar Balance**. <br> - Triển khai **Budget Threshold & Over-Budget Logic** (phát events cảnh báo) và **Jar Expiry Processing Service** (xử lý Income Jar auto-reset, Expense Jar Grace Period/Auto-Return). | 13/11/2025 | 13/11/2025      | [Day 4 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-1/day-4.md?ref_type=heads) |
| 5   | **Tích hợp End-to-End & Thử nghiệm** <br> - Thiết lập **API Gateway** (Routing, CORS, Rate Limiting). <br> - Cấu hình giao tiếp **Service-to-Service** với **HTTP Client Factory** và **Polly** (Retry Policy, Circuit Breaker). <br> - Thực hiện **Integration Testing** cho luồng End-to-End: New User Onboarding, Jar Creation, Wallet/Jar Operations (Deposit/Withdraw/Transfer/Reconcile), và **Goal Achievement**. <br> - Thử nghiệm **Security** (JWT Expiration, Authorization) và **Concurrency** (Balance Updates).                                                                        | 14/11/2025 | 14/11/2025      | [Day 5 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-1/day-5.md?ref_type=heads) |

### Kết quả đạt được tuần 10:

- **Transaction Service Hoàn thiện:**
  - Đã triển khai đầy đủ CRUD, luồng dòng tiền chặt chẽ, và cơ chế hoàn tiền tự động khi xóa.
- **Hỗ trợ Tính năng Nâng cao:**
  - **Lọc đa chiều** và **Tìm kiếm** hiệu quả đã được tích hợp.
  - Hỗ trợ **Transaction Tags** và lưu trữ **AI Metadata** (JSONB).
- **Kiến trúc Hướng Sự kiện Ổn định:**
  - **RabbitMQ/MassTransit** đã hoạt động, đảm bảo sự đồng bộ số dư Jar giữa Transaction Service và Wallet Service.
  - Đã xử lý thành công các sự kiện tạo giao dịch tự động.
- **Hệ thống Ổn định và Được Kiểm thử:**
  - Toàn bộ Sprint đã được kiểm thử tích hợp (Integration Testing) và tối ưu hóa hiệu năng.
