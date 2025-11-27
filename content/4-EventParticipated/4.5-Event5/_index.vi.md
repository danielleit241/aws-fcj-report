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
- **Tối ưu hóa ứng dụng (Containerization):** Nắm vững kiến trúc và chiến lược lựa chọn nền tảng chạy Container phù hợp: App Runner, ECS hay EKS.
- **Giám sát toàn diện (Observability):** Xây dựng hệ thống giám sát chủ động, phát hiện lỗi và tối ưu hiệu năng bằng CloudWatch và X-Ray.

### Danh Sách Diễn Giả

- **Đội ngũ chuyên gia AWS & Cloud Engineers:** Chia sẻ về kiến trúc hệ thống, chiến lược Platform Engineering và demo kỹ thuật chuyên sâu.

### Nội Dung Chi Tiết

#### **1. DevOps Mindset & CI/CD Pipeline (Nền Tảng Tư Duy)**

Sự kiện bắt đầu bằng việc xác định lại DevOps không đơn thuần là công cụ, mà là văn hóa tối ưu hóa dòng chảy giá trị.

- **The Value Cycle (Vòng Đời Giá Trị):**

  - Quy trình khép kín 5 bước: _Insights & Analysis -\> Portfolio & Backlog -\> Continuous Integration -\> Continuous Testing -\> Continuous Delivery_.
  - Mục tiêu cốt lõi: Tăng tốc độ phát hành (Speed) để đáp ứng thị trường nhanh hơn, nhưng vẫn phải đảm bảo sự ổn định (Stability) và chất lượng hệ thống.

- **Định nghĩa lại các khái niệm CI/CD:**

  - **Continuous Integration (CI):** Developer merge code thường xuyên (hàng ngày). Hệ thống tự động Build và chạy Unit Test. Mục tiêu là phát hiện lỗi sớm (Fail fast).
  - **Continuous Delivery:** Tự động hóa quy trình deploy đến môi trường Staging/Pre-prod. Việc deploy ra Production cần sự chấp thuận của con người (**Manual Trigger**).
  - **Continuous Deployment:** Tự động hóa hoàn toàn 100% từ lúc Commit code đến khi chạy trên Production (không cần can thiệp thủ công).

- **Chiến lược Pipeline hiệu quả:**

  - **Centralized CI:** Xây dựng hệ thống CI tập trung để quản lý bảo mật và tài nguyên, nhưng phải đảm bảo quyền tự phục vụ (Self-service) cho Developer để tránh tắc nghẽn.
  - **Artifact Management (Quản lý thành phẩm):** Áp dụng nguyên tắc **"Build Once, Deploy Anywhere"**. Mã nguồn chỉ được build một lần duy nhất thành gói Binary (Artifact). Các môi trường sau (Staging, Prod) sử dụng chính gói Artifact này để deploy, đảm bảo tính nhất quán tuyệt đối.
  - **Điều kiện đánh rớt Build:** Pipeline cần được thiết lập để Fail ngay lập tức nếu vi phạm: Lỗi biên dịch, Vi phạm Code Style, Security scan phát hiện lỗ hổng, hoặc Test chạy quá chậm.

- **Đo lường hiệu quả (Metrics):**

  - Sử dụng **Heatmap** để theo dõi sức khỏe Pipeline của toàn bộ tổ chức.
  - Các chỉ số vàng: _Deployment Frequency_ (Tần suất deploy), _Change Failure Rate_ (Tỷ lệ lỗi), _MTTR_ (Thời gian phục hồi).

#### **2. Infrastructure as Code (IaC) - Từ ClickOps Đến Code**

Phần này đi sâu vào việc loại bỏ thói quen thao tác tay (ClickOps) và chuyển sang tự động hóa hoàn toàn hạ tầng.

- **Vấn đề của "ClickOps":** Thao tác tay trên AWS Console dễ gây ra sai sót con người (Human Error), chậm chạp, khó mở rộng và thiếu sự nhất quán giữa Dev/Prod.
- **Giải pháp IaC:** Mang lại khả năng Tự động hóa (Automation), Khả năng mở rộng (Scalability), Tái tạo môi trường (Reproducibility) và Cộng tác (Collaboration).

**Phân tích chi tiết 3 công cụ IaC hàng đầu:**

- **1. AWS CloudFormation (Native Tool):**

  - Sử dụng file văn bản (**YAML** hoặc **JSON**) để mô tả trạng thái mong muốn.
  - **Template Anatomy:** Cấu trúc gồm _Parameters_ (Tham số động), _Mappings_ (Xử lý khác biệt vùng miền - ví dụ AMI ID khác nhau giữa các Region), và _Resources_ (Tài nguyên cần tạo).
  - **Stack:** Đơn vị quản lý vòng đời tài nguyên. Xóa Stack là xóa sạch tài nguyên liên quan.

- **2. Terraform (Multi-Cloud Powerhouse):**

  - Công cụ mã nguồn mở, sử dụng ngôn ngữ **HCL** (HashiCorp Configuration Language).
  - **Điểm mạnh:** Hỗ trợ đa nền tảng (Multi-cloud: AWS, Azure, GCP...).
  - **Quy trình (Workflow):** _Write_ (Viết code) -\> _Plan_ (Xem trước thay đổi - Preview) -\> _Apply_ (Thực thi). Bước **Plan** là cực kỳ quan trọng để kiểm tra an toàn.
  - **State File:** File lưu trạng thái thực tế của hạ tầng để đồng bộ.

- **3. AWS CDK (Cloud Development Kit):**

  - Cho phép viết hạ tầng bằng **ngôn ngữ lập trình** (Python, TypeScript, Java...).
  - **Constructs (Khối xây dựng):**
    - _L1 (Cfn Resources):_ Cấu hình chi tiết từng dòng (giống CloudFormation).
    - _L2 (Curated):_ Tự động áp dụng Best Practices và cấu hình mặc định an toàn.
    - _L3 (Patterns):_ Dựng cả một kiến trúc phức tạp (ví dụ: VPC + ALB + ECS) chỉ trong vài dòng code.

- **Drift Detection:** Tính năng quan trọng giúp phát hiện sự sai lệch cấu hình giữa Code và Thực tế (do ai đó sửa tay - ClickOps), giúp duy trì kỷ luật vận hành.

#### **3. Containerization - Chiến Lược Chạy Ứng Dụng**

Phân tích sâu về các nền tảng điều phối container (Orchestration):

- **Kubernetes (K8s):**

  - Kiến trúc gồm **Control Plane** (API Server, etcd, Scheduler) và **Worker Nodes** (Kubelet, Pods).
  - Mạnh mẽ, linh hoạt nhưng phức tạp trong vận hành.

- **So sánh Amazon ECS vs. Amazon EKS:**

  - **Amazon ECS:** Đơn giản, tích hợp sâu với AWS (ALB, IAM). Phù hợp cho team muốn giảm tải vận hành, deploy nhanh.
  - **Amazon EKS:** Dựa trên Kubernetes chuẩn. Mạnh mẽ, hệ sinh thái mở rộng lớn. Phù hợp cho Enterprise, hệ thống phức tạp hoặc Hybrid-cloud.

- **Mô hình tính toán (Compute Options):**

  - **EC2 Launch Type:** Tự quản lý server (Patching, Scaling). Kiểm soát cao nhất nhưng tốn công vận hành.
  - **AWS Fargate (Serverless):** Không cần quản lý server. AWS lo hạ tầng, người dùng chỉ cần định nghĩa CPU/RAM cho Task. An toàn và tiện lợi.

- **AWS App Runner:**

  - Giải pháp "Zero-ops" cho Web App/API.
  - Tự động hoàn toàn từ Source Code/Image -\> Public URL (HTTPS) mà không cần cấu hình hạ tầng mạng hay server.

#### **4. Observability - Giám Sát & Tối Ưu Hóa**

Khép kín vòng đời phát triển bằng khả năng quan sát sâu rộng để đảm bảo hệ thống vận hành ổn định.

- **Amazon CloudWatch (Tai mắt của hệ thống):**

  - **Metrics:** Thu thập dữ liệu hiệu năng (CPU, Memory, Disk).
  - **Logs:** Thu thập nhật ký ứng dụng tập trung. Dùng Logs Insights để truy vấn lỗi.
  - **Alarms:** Tự động kích hoạt hành động (Auto Scaling, Restart Server, gửi thông báo) khi đạt ngưỡng cảnh báo.

- **AWS X-Ray (Truy vết phân tán):**

  - Giải quyết bài toán "mò kim đáy bể" trong Microservices.
  - **Distributed Tracing:** Theo dõi hành trình của một request đi qua nhiều service để tìm ra nút thắt cổ chai (Bottlenecks) và nguyên nhân gốc rễ (Root cause).

- **AWS Observability Best Practices:**

  - Sử dụng trang tài nguyên của AWS để tham khảo các **Patterns** (Mẫu thiết kế) và **Recipes** (Công thức cấu hình) chuẩn chỉnh.
  - Phân biệt rõ: **Logs** (Sự kiện rời rạc) khác với **Traces** (Hành trình liên kết).

### Trải nghiệm chi tiết trong Event

Tham gia chuyên đề này mang lại cho tôi những thay đổi lớn về nhận thức và kỹ năng kỹ thuật:

#### 1\. Sự chuyển dịch từ "Ops" sang "Platform Engineering"

Tôi nhận ra vai trò của DevOps hiện đại không phải là người chạy theo Developer để deploy code thủ công. DevOps là người kiến tạo ra **"Đường cao tốc" (Pipeline & Platform)**. Một nền tảng tốt cho phép Developer tự phục vụ (Self-service) việc khởi tạo môi trường và deploy code một cách nhanh chóng, nhưng vẫn nằm trong khuôn khổ an toàn (Governance) mà đội ngũ DevOps đã thiết lập.

#### 2\. Kỷ luật trong vận hành (Operational Discipline)

Những bài học về **Artifact Management** và **Drift Detection** là những nguyên tắc vàng. Trong môi trường Enterprise, sự nhất quán (Consistency) là yếu tố sống còn. Tuyệt đối không được phép có sự khác biệt về cách build giữa các môi trường (Dev/Test/Prod) và không được phép sửa đổi thủ công (Manual changes) vào hệ thống đã được quản lý bằng Code.

#### 3\. Chiến lược lựa chọn công cụ thông minh

Không có công cụ "tốt nhất", chỉ có công cụ "phù hợp nhất":

- Cần sự ổn định tuyệt đối và hỗ trợ sâu nhất các dịch vụ AWS mới: Chọn **CloudFormation**.
- Doanh nghiệp sử dụng Multi-cloud hoặc Hybrid-cloud: **Terraform** là lựa chọn tối ưu.
- Team Development mạnh về lập trình, cần xây dựng nhanh các kiến trúc phức tạp và tái sử dụng code: **AWS CDK** là vũ khí mạnh nhất.
- Với ứng dụng Web đơn giản: Dùng **App Runner** thay vì lãng phí nguồn lực để vận hành cụm Kubernetes.

### Kết Luận

Chuyên đề **"DevOps & IaC Mastery"** đã cung cấp một tấm bản đồ hoàn chỉnh cho hành trình lên Cloud:

- **Về Tư duy:** Chuyển từ làm thủ công sang tự động hóa và đo lường bằng dữ liệu thực tế.
- **Về Hạ tầng:** Làm chủ IaC để hệ thống có thể mở rộng, tái tạo dễ dàng và kiểm soát được sự sai lệch.
- **Về Vận hành:** Kết hợp Containerization linh hoạt và Observability sâu rộng để đảm bảo hệ thống luôn ổn định, hiệu năng cao và có khả năng tự phục hồi.

Đây là nền tảng kiến thức vững chắc để xây dựng các hệ thống phần mềm quy mô lớn, hiện đại trên AWS.

#### Một số hình ảnh khi tham gia sự kiện
