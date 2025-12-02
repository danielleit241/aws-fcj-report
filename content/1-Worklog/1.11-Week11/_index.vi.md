---
title: "Worklog Tuần 11"
date: "2025-09-09"
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu tuần 11:

- Hoàn thành việc triển khai **Report Service** sử dụng kiến trúc **CQRS** để tách biệt luồng đọc/ghi, đảm bảo hiệu năng cao cho các báo cáo phức tạp.
- Triển khai các tính năng phân tích nâng cao: **Xu hướng chi tiêu**, **So sánh Ngân sách vs Thực tế**, và tính năng **Xuất báo cáo Excel** đa sheet.
- Xây dựng **Notification Service** toàn diện hỗ trợ đa kênh: **Email** (qua AWS SES) và **In-App** (qua SignalR), cho phép người dùng tùy chỉnh cấu hình nhận tin.
- Thiết lập quy trình **Tự động hóa cuối kỳ (Period End Automation)** để xử lý tiền dư và chuẩn bị Backend sẵn sàng cho tích hợp **AI (OCR/Voice)**.

### Công việc thực hiện trong tuần này:

| Day | Task                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Start Date | Completion Date | Reference Material                                                                                                   |
| :-- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :------------------------------------------------------------------------------------------------------------------- |
| 1   | **Report Service Foundation & CQRS Setup** <br> - Khởi tạo **Report Service**, thiết lập Database PostgreSQL (`report_service_db`) và các Read Model entities (`TransactionSummary`, `JarAnalytics`). <br> - Triển khai mẫu **CQRS**: Xử lý các sự kiện từ Transaction Service (`TransactionCreated`, `Updated`, `Deleted`) để cập nhật dữ liệu báo cáo theo thời gian thực. <br> - Xây dựng các **Basic Report APIs** để lấy tóm tắt kỳ và thống kê cơ bản theo hũ. | 17/11/2025 | 17/11/2025      | [Day 11 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-3/day-11.md?ref_type=heads) |
| 2   | **Advanced Analytics & Excel Export** <br> - Phát triển các API phân tích nâng cao: Xu hướng chi tiêu (ngày/tuần/tháng), so sánh ngân sách thực tế (Budget vs Actual), và tiến độ mục tiêu. <br> - Tích hợp thư viện Excel (EPPlus/ClosedXML) để xuất báo cáo **Multi-sheet** (Lịch sử giao dịch, Phân tích hũ, Phân tích danh mục). <br> - Cấu hình **Caching** cho các báo cáo để tối ưu hiệu năng truy vấn.                                                       | 18/11/2025 | 18/11/2025      | [Day 12 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-3/day-12.md?ref_type=heads) |
| 3   | **Notification Service & Email Integration** <br> - Khởi tạo **Notification Service** kết nối MongoDB (`UserPreferences`, `EmailHistory`). <br> - Tích hợp **AWS SES** và tạo template email cho các cảnh báo quan trọng (Vượt ngân sách, Số dư thấp, Đạt mục tiêu tiết kiệm). <br> - Xây dựng API quản lý **Preferences** cho phép người dùng tùy chọn tần suất nhận tin (Daily/Weekly) và loại thông báo.                                                          | 19/11/2025 | 19/11/2025      | [Day 13 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-3/day-13.md?ref_type=heads) |
| 4   | **Period End Automation & In-App Alerts** <br> - Thiết lập **Job Scheduler** (Hangfire/Quartz) để tự động hóa quy trình cuối kỳ: Tính toán tiền dư, hoàn về ví chính và tạo báo cáo tổng kết. <br> - Triển khai hệ thống thông báo **In-App** thời gian thực qua **SignalR Hub**. <br> - Xây dựng API đánh dấu đã đọc (`mark-as-read`) và quản lý số lượng thông báo chưa đọc (badge count).                                                                         | 20/11/2025 | 20/11/2025      | [Day 14 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-3/day-14.md?ref_type=heads) |
| 5   | **AI Service Integration (Backend Side)** <br> - Cập nhật Transaction Entity bổ sung các trường metadata AI (`AiExtracted`, `ConfidenceScore`, `OriginalText`). <br> - Phát triển API **Batch Transaction** (`POST /batch`) hỗ trợ xử lý hóa đơn OCR nhiều món trong một lần gọi. <br> - Cập nhật luồng xử lý để Backend nhận dữ liệu đã được người dùng review từ Client thay vì tự động tạo từ sự kiện AI.                                                         | 21/11/2025 | 21/11/2025      | [Day 15 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-3/day-15.md?ref_type=heads) |

### Thành tựu Tuần 11:

- **Report Service & Analytics Toàn diện:**
  - Đã vận hành ổn định hệ thống báo cáo với mẫu **CQRS**, cung cấp số liệu phân tích theo thời gian thực.
  - Tính năng **Xuất Excel** hoạt động hoàn hảo với nhiều sheet chi tiết (Lịch sử giao dịch, Phân tích hũ, Phân tích danh mục).
- **Hệ thống Thông báo Đa kênh:**
  - **AWS SES** đã được tích hợp để gửi email cảnh báo (Vượt ngân sách, Số dư thấp).
  - Hệ thống **SignalR** hoạt động ổn định cho các thông báo thời gian thực ngay trên ứng dụng.
- **Tự động hóa & Sẵn sàng cho AI:**
  - Job **xử lý cuối kỳ** đã hoạt động tự động: tính toán tiền dư và hoàn về ví chính chính xác.
  - Backend đã hoàn tất API hỗ trợ **Batch Transaction** và lưu trữ **AI Metadata** (Confidence Score, Original Text).
