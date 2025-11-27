---
title: "Event 5"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 4.5. </b> "
---

# Bài thu hoạch “AWS Cloud Mastery Series #2: Từ DevOps, IaC đến Container & Observability”

### Mục Đích Của Sự Kiện

- **Chuẩn hóa tư duy (Mindset):** Hiểu rõ vòng đời giá trị (Value Cycle) và vai trò của DevOps trong việc chuyển giao phần mềm liên tục, tin cậy.
- **Hiện đại hóa hạ tầng (IaC):** Chuyển dịch từ thao tác thủ công (ClickOps) sang quản lý hạ tầng bằng mã (Infrastructure as Code) với CloudFormation, Terraform và CDK.
- **Tối ưu hóa ứng dụng (Containerization):** Nắm vững chiến lược lựa chọn nền tảng chạy Container phù hợp: App Runner, ECS hay EKS.
- **Giám sát toàn diện (Observability):** Xây dựng hệ thống giám sát chủ động, phát hiện lỗi và tối ưu hiệu năng bằng CloudWatch và X-Ray.

### Danh Sách Diễn Giả

- **Đội ngũ chuyên gia AWS & Cloud Engineers:** Chia sẻ về kiến trúc hệ thống, chiến lược Platform Engineering và demo kỹ thuật chuyên sâu.

### Nội Dung Nổi Bật

#### **1. DevOps Mindset & CI/CD Pipeline (Nền Tảng Tư Duy)**

DevOps không đơn thuần là công cụ, mà là văn hóa tối ưu hóa dòng chảy giá trị từ ý tưởng đến người dùng cuối.

- **The Value Cycle:** Quy trình khép kín từ _Insights -\> Backlog -\> CI -\> Testing -\> CD_ nhằm tăng tốc độ phát hành (Speed) nhưng vẫn đảm bảo sự ổn định (Stability).
- **Chiến lược Pipeline:**
  - **Centralized CI:** Hệ thống tập trung nhưng đảm bảo quyền tự phục vụ (Self-service) cho Developer.
  - **Build Once, Deploy Anywhere:** Mã nguồn chỉ build một lần thành Artifact và dùng nó để deploy qua các môi trường (Staging, Prod) để đảm bảo nhất quán.
  - **Fail Fast:** Đánh rớt build ngay lập tức nếu vi phạm Code Style, Security hoặc Performance.

#### **2. Infrastructure as Code (IaC) - Từ ClickOps Đến Code**

Loại bỏ thói quen thao tác tay (ClickOps) gây sai sót và khó đồng bộ, chuyển sang tự động hóa hoàn toàn.

- **AWS CloudFormation (Native):** Sử dụng YAML/JSON, quản lý qua Stack và xử lý khác biệt vùng miền bằng Mappings.
- **Terraform (Multi-Cloud):** Mã nguồn mở, dùng ngôn ngữ HCL. Nổi bật với tính năng **Plan** (Xem trước thay đổi) và quản lý trạng thái qua State File.
- **AWS CDK (Programming):** Viết hạ tầng bằng ngôn ngữ lập trình (Python, TS...). Sử dụng các **Constructs** (L2, L3) để dựng kiến trúc phức tạp nhanh chóng theo chuẩn Best Practices.
- **Drift Detection:** Tính năng quan trọng để phát hiện sự sai lệch giữa Code và Thực tế, giúp duy trì kỷ luật vận hành.

#### **3. Containerization - Chiến Lược Chạy Ứng Dụng**

Phân tích và lựa chọn nền tảng phù hợp dựa trên nhu cầu của dự án:

- **Amazon ECS:** Đơn giản, tích hợp sâu với AWS. Phù hợp cho team muốn giảm tải vận hành.
- **Amazon EKS:** Dựa trên Kubernetes. Mạnh mẽ, linh hoạt, chuẩn mở. Dành cho hệ thống lớn hoặc Hybrid-cloud.
- **AWS Fargate (Serverless Compute):** Không cần quản lý server (EC2), chỉ cần lo ứng dụng. An toàn và tiện lợi.
- **AWS App Runner:** Giải pháp "mì ăn liền" cho Web App, tự động từ Code ra URL (HTTPS).

#### **4. Observability - Giám Sát & Tối Ưu Hóa**

Khép kín vòng đời phát triển bằng khả năng quan sát sâu rộng:

- **Amazon CloudWatch:** Thu thập Metrics & Logs tập trung. Sử dụng **Alarms** để tự động kích hoạt hành động sửa lỗi (Auto Scaling, Restart Server).
- **AWS X-Ray:** Giải quyết bài toán "mò kim đáy bể" trong Microservices bằng **Distributed Tracing**, giúp tìm ra nút thắt cổ chai (Bottlenecks).
- **AWS Observability Best Practices:** Sử dụng các mẫu thiết kế (Patterns) và công thức (Recipes) chuẩn chỉnh từ AWS.

### Trải nghiệm chi tiết trong Event

Tham gia chuyên đề này giúp tôi hệ thống hóa lại toàn bộ kiến thức về DevOps hiện đại và chiến lược quản lý hạ tầng.

#### 1\. Sự chuyển dịch tư duy sang "Platform Engineering"

Tôi nhận ra vai trò của DevOps không phải là "người đi deploy thuê". DevOps là người kiến tạo ra **"Đường cao tốc" (Pipeline & Platform)** để Developer có thể tự vận hành (Self-service) một cách nhanh chóng nhưng vẫn tuân thủ các quy tắc an toàn.

#### 2\. Kỷ luật trong vận hành (Operational Discipline)

Các bài học về **Artifact Management** và **Drift Detection** là những nguyên tắc vàng. Trong môi trường Enterprise, sự nhất quán (Consistency) là yếu tố sống còn. Tuyệt đối không được phép sửa đổi thủ công (Manual changes) vào hệ thống đã được quản lý bằng Code.

#### 3\. Chiến lược lựa chọn công cụ

Không có công cụ tốt nhất, chỉ có công cụ phù hợp nhất:

- Cần ổn định, thuần AWS: Chọn **CloudFormation**.
- Cần Multi-cloud: Chọn **Terraform**.
- Team mạnh lập trình, cần build nhanh: Chọn **CDK**.
- Chạy Web App đơn giản: Dùng **App Runner** thay vì "gồng mình" với Kubernetes.

### Kết Luận

Chuyên đề **"DevOps & IaC Mastery"** đã cung cấp một tấm bản đồ hoàn chỉnh cho hành trình lên Cloud:

- **Tư duy:** Chuyển từ làm thủ công sang tự động hóa và đo lường bằng dữ liệu.
- **Hạ tầng:** Làm chủ IaC để hệ thống có thể mở rộng và tái tạo dễ dàng.
- **Vận hành:** Kết hợp Containerization và Observability để đảm bảo hệ thống luôn ổn định và hiệu năng cao.

#### Một số hình ảnh khi tham gia sự kiện
