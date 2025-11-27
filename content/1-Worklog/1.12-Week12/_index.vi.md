---
title: "Worklog Tuần 12"
date: "2025-09-09"
weight: 2
chapter: false
pre: " <b> 1.12 </b> "
---

### Mục tiêu tuần 12:

- Hoàn tất **Kiểm thử tích hợp toàn hệ thống (End-to-End)**, đảm bảo các luồng nghiệp vụ phức tạp (đăng ký, giao dịch, chuyển tiền giữa các hũ) hoạt động trơn tru.
- Thực hiện **Tối ưu hóa hiệu năng** toàn diện: Đánh chỉ mục Database, Caching API và thực hiện Load Testing hỗ trợ 100 người dùng đồng thời.
- Tăng cường **Bảo mật hệ thống**: Rà soát xác thực/phân quyền, quản lý secrets qua biến môi trường và thiết lập HTTPS.
- **Đóng gói và Tài liệu hóa**: Hoàn thiện Docker hóa các dịch vụ, viết tài liệu Swagger đầy đủ và sẵn sàng kịch bản triển khai lên AWS.

### Các công việc cần triển khai trong tuần này:

| Day | Task                                                                                                                                                                                                                                                                                                                                                                                            | Start Date | Completion Date | Reference Material                                                                                                   |
| :-- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :------------------------------------------------------------------------------------------------------------------- |
| 1   | **Integration Testing - Full System** <br> - Thực hiện kiểm thử luồng End-to-End: Từ đăng ký User, tạo Wallet, Budget đến Giao dịch và Xử lý cuối kỳ. <br> - Kiểm thử hệ thống sự kiện (Event-Driven): Xác minh tính toàn vẹn dữ liệu qua RabbitMQ và khả năng xử lý lỗi (retry, dead letter). <br> - Kiểm thử các kịch bản lỗi (Error Scenarios): Token không hợp lệ, mất kết nối DB/RabbitMQ. | 24/11/2025 | 24/11/2025      | [Day 16 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-4/day-16.md?ref_type=heads) |
| 2   | **Performance Optimization** <br> - Tối ưu hóa Database: Thêm Index cho các truy vấn chậm, cấu hình Connection Pooling. <br> - Tối ưu hóa API: Áp dụng Response Caching, nén Gzip và phân trang cho dữ liệu lớn. <br> - Thực hiện Load Testing (k6/JMeter): Mô phỏng 50-100 người dùng đồng thời, đảm bảo response time < 2s.                                                                   | 25/11/2025 | 25/11/2025      | [Day 17 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-4/day-17.md?ref_type=heads) |
| 3   | **Security Hardening** <br> - Rà soát bảo mật (Security Audit): Kiểm tra phân quyền (Authorization), validate đầu vào và chống SQL Injection. <br> - Quản lý Secrets: Chuyển toàn bộ thông tin nhạy cảm sang biến môi trường và .NET User Secrets. <br> - Cấu hình HTTPS: Thiết lập SSL self-signed cho local và cập nhật chính sách CORS.                                                      | 26/11/2025 | 26/11/2025      | [Day 18 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-4/day-18.md?ref_type=heads) |
| 4   | **Bug Fixes & Code Quality** <br> - Sửa lỗi (Bug Fixing): Tập trung xử lý triệt để các lỗi P0, P1 phát hiện trong quá trình test. <br> - Cải thiện chất lượng Code: Refactor các hàm phức tạp, thêm XML documentation và Unit tests cho logic quan trọng. <br> - Nâng cấp Logging: Tích hợp Serilog với cấu trúc log chuẩn (Structured Logging) và Correlation IDs.                             | 27/11/2025 | 27/11/2025      | [Day 19 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-4/day-19.md?ref_type=heads) |
| 5   | **Documentation & Deployment Prep** <br> - Hoàn thiện tài liệu API: Cập nhật Swagger đầy đủ ví dụ request/response và xuất Postman Collection. <br> - Chuẩn bị triển khai: Viết Dockerfile cho từng service, file docker-compose.yml <br> - Demo & Bàn giao: Cập nhật README, sơ đồ kiến trúc và thực hiện demo toàn bộ quy trình cho team.                                                     | 28/11/2025 | 28/11/2025      | [Day 20 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-4/day-20.md?ref_type=heads) |

### Kết quả đạt được tuần 12:

- **Chất lượng hệ thống được đảm bảo:**
  - Đã vượt qua các bài kiểm thử tích hợp (Integration Tests) bao gồm cả các kịch bản lỗi và xử lý sự kiện bất đồng bộ.
  - Các lỗi nghiêm trọng (P0/P1) đã được xử lý triệt để, Code coverage đạt mục tiêu > 80%.
- **Hiệu năng và Bảo mật tối ưu:**
  - Thời gian phản hồi API đạt mục tiêu < 2s nhờ tối ưu hóa Database và áp dụng Caching.
  - Hệ thống được bảo vệ với Rate limiting, Input validation và cấu hình CORS chặt chẽ.
- **Sẵn sàng triển khai (Deployment Ready):**
  - Toàn bộ 6 microservices đã có Dockerfile và chạy ổn định trên môi trường local với docker-compose.
  - Tài liệu kỹ thuật (Architecture diagram, Swagger, Postman) đã hoàn tất.
