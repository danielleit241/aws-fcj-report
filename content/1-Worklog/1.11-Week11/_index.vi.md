---
title: "Worklog Tuần 11"
date: "2025-09-09"
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu tuần 11:

- Hoàn thành việc triển khai **Transaction Service** (Tạo, Đọc, Cập nhật, Xóa) với luồng dòng tiền được kiểm soát chặt chẽ qua **Wallet Service** (kiểm tra và trừ số dư).
- Triển khai các tính năng nâng cao cho Transaction: **Lọc nâng cao**, **Tìm kiếm toàn văn**, **Tags**, và hỗ trợ **AI Metadata**.
- Thiết lập hoàn chỉnh **Kiến trúc hướng sự kiện (Event-Driven Architecture)** sử dụng **RabbitMQ/MassTransit** để đồng bộ dữ liệu giữa các dịch vụ (User, Wallet, Transaction).
- Hoàn tất **Integration Testing** và **tối ưu hóa hiệu năng** cho các luồng nghiệp vụ cốt lõi.

---

### Các công việc cần triển khai trong tuần này:

| Day        | Task                                                                                                                                                                                                                                                                                                                                                                                                                                                             | Start Date | Completion Date | Reference Material                                                                                                   |
| :--------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :------------------------------------------------------------------------------------------------------------------- |
| **Day 6**  | **Transaction Service Foundation & Database Setup** <br> - Khởi tạo **Transaction Service**, thiết lập Database PostgreSQL với các Entities (`Transaction`, `TransactionTag`, v.v.). <br> - Cấu hình **HTTP Client Factory** với **Polly** (Retry/Circuit Breaker) để giao tiếp với Wallet Service.                                                                                                                                                              | 17/11/2025 | 17/11/2025      | [Day 6 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-2/day-6.md?ref_type=heads)   |
| **Day 7**  | **Transaction CRUD APIs & Wallet Integration** <br> - Triển khai đầy đủ **CRUD APIs** (Create, Read, Update, Delete) cho giao dịch. <br> - Đảm bảo tính **Atomic** (nguyên tử) trong luồng tạo giao dịch: **Deduct Balance** qua HTTP Client, sau đó mới lưu record vào DB. <br> - Xử lý logic **Soft Delete** với cơ chế **hoàn tiền (refund)** tự động vào Jar. <br> - Triển khai các API **Thống kê cơ bản** (tổng chi tiêu, chi tiêu hàng ngày).             | 18/11/2025 | 18/11/2025      | [Day 7 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-2/day-7.md?ref_type=heads)   |
| **Day 8**  | **Advanced Filtering, Tags & Budget Support** <br> - Hoàn thiện API **GET /api/transactions** với **Lọc nâng cao** (theo Date Range, Jar ID, Category ID, Amount Range) và **Tìm kiếm toàn văn** (`search=`). <br> - Triển khai hệ thống **Transaction Tags** (Thêm/Xóa tags) và API để lấy danh sách tags. <br> - Bổ sung API hỗ trợ **Budget Checking** cho Wallet Service.                                                                                    | 19/11/2025 | 19/11/2025      | [Day 8 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-2/day-8.md?ref_type=heads)   |
| **Day 9**  | **Event-Driven Architecture & Service Integration** <br> - Thiết lập **RabbitMQ** và **MassTransit** cho các dịch vụ. <br> - Triển khai **Consumers** tại Wallet Service để xử lý sự kiện `TransactionCreated` (cập nhật số dư Jar). <br> - Triển khai **Consumers** tại Transaction Service để tạo các giao dịch tự động từ sự kiện Wallet (như `WalletDeposited`, `WalletWithdrawn`). <br> - Đảm bảo **Idempotency** (tính bất biến) cho tất cả các Consumers. | 20/11/2025 | 20/11/2025      | [Day 9 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-2/day-9.md?ref_type=heads)   |
| **Day 10** | **Sprint 2 Testing, Bug Fixes & Polish** <br> - Thực hiện **Integration Testing End-to-End** cho toàn bộ luồng nghiệp vụ (Đăng ký -> Ví -> Hũ -> Giao dịch -> Cảnh báo ngân sách). <br> - **Load Test** với 50 concurrent requests. <br> - **Tối ưu hóa hiệu năng** (thêm Index DB, Caching). <br> - Cập nhật **Documentation** (Swagger, Postman, README).                                                                                                      | 21/11/2025 | 21/11/2025      | [Day 10 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-2/day-10.md?ref_type=heads) |

### Kết quả đạt được tuần 11:

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
