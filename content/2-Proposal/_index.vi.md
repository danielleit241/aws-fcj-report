---
title: "Bản đề xuất"
date: "2025-09-09"
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Personal Finance Management App

### 1. Tóm tắt điều hành

Dự án Personal Finance Management App hướng đến việc cung cấp một nền tảng quản lý tài chính cá nhân thông minh, hiện đại và mang tính tự động hóa cao. Ứng dụng cho phép người dùng ghi nhận thu chi, tạo và quản lý nhiều hũ tiền (money jars) theo mục đích khác nhau, lập kế hoạch chi tiêu, nhận cảnh báo thông minh và tạo báo cáo phân tích trực quan.

Ứng dụng được xây dựng với kiến trúc microservices trên nền tảng .NET Aspire và FastAPI, triển khai trên AWS Cloud, đảm bảo tính linh hoạt, khả năng mở rộng và an toàn dữ liệu. Quy trình phát triển tuân theo mô hình Agile/Scrum (2 tuần/sprint), với thời gian hoàn thành MVP trong 2 tháng.

### 2. Tuyên bố vấn đề

_Vấn đề hiện tại_  
Trên thị trường đã có rất nhiều ứng dụng quản lý tài chính, tuy nhiên phần lớn vẫn yêu cầu người dùng nhập liệu thủ công — một công việc tốn thời gian, dễ sai sót và khiến người dùng nhanh chóng bỏ cuộc. Các ứng dụng hiện có chỉ tập trung vào thống kê chi tiêu mà chưa thực sự giúp người dùng tự động hóa quy trình quản lý tài chính cá nhân.

_Giải pháp_  
Giải pháp sử dụng AWS Cloud kết hợp kiến trúc microservices để xây dựng một nền tảng quản lý tài chính cá nhân tự động hóa, tích hợp AI trong xử lý giọng nói và nhận diện hóa đơn. Hệ thống được triển khai trên AWS ECS Fargate cho các service backend (.NET Aspire), FastAPI cho xử lý AI, và Next.js cho frontend. So với các nền tảng tài chính phổ biến như Money Lover hay Misa Money Keeper, ứng dụng này tập trung vào tự động hóa hoàn toàn nhập liệu tài chính thông qua AI voice-to-text và bill scanning chi tiết tiếng Việt, giúp giảm thao tác thủ công và sai sót. Hệ thống phù hợp cho người dùng cá nhân và nhóm nhỏ, đồng thời có thể mở rộng khi cần cho quy mô doanh nghiệp hoặc ứng dụng ngân hàng số.

_Lợi ích và hoàn vốn đầu tư (ROI)_  
Giải pháp mang lại nhiều lợi ích thiết thực cả về mặt kỹ thuật và giá trị kinh doanh:

- Tự động hóa nhập liệu: Giảm hơn 70% thao tác thủ công nhờ AI nhận diện giọng nói và hóa đơn.
- Tăng độ chính xác: Hạn chế sai sót nhập liệu, đảm bảo tính toàn vẹn của dữ liệu tài chính (>90% chính xác).
- Cải thiện hiệu suất người dùng: Ghi nhận và phân loại giao dịch chỉ trong vài giây, tối ưu trải nghiệm sử dụng.
- Tiết kiệm chi phí: Chi phí hạ tầng thấp nhờ tận dụng AWS Free Tier đến năm 2026; chỉ ước tính ~60 USD/tháng cho AWS và ~30 USD cho compute AI.
- Hoàn vốn nhanh: Dự kiến hoàn vốn trong 6–12 tháng, nhờ tiết kiệm thời gian nhập liệu và tăng hiệu suất vận hành.
- Khả năng mở rộng & tích hợp: Kiến trúc microservices trên AWS cho phép dễ dàng bổ sung tính năng (mobile app, phân tích nâng cao, tích hợp ngân hàng).

### 3. Kiến trúc giải pháp

Hệ thống được triển khai theo mô hình **microservices** trên nền tảng **AWS Cloud**, kết hợp các dịch vụ serverless, container, và cơ sở dữ liệu quản lý để đảm bảo hiệu năng và khả năng mở rộng.

![IoT Weather Sofware Architecture](/images/2-Proposal/development_architecture.drawio.png)

Người dùng truy cập ứng dụng web **Next.js** thông qua **Amazon CloudFront**, nội dung tĩnh được lưu trữ trong **Amazon S3**.  
Khi người dùng đăng nhập, quá trình xác thực được xử lý bởi **Amazon Cognito**, cấp token truy cập để frontend gửi các yêu cầu API qua **Amazon API Gateway**.

API Gateway định tuyến yêu cầu đến **Application Load Balancer (ALB)**, sau đó chuyển đến **Amazon ECS (Fargate)** — nơi triển khai các container backend bao gồm:

- **Aspire Service (.NET Aspire)**: Xử lý nghiệp vụ chính như người dùng, giao dịch và ngân sách.
- **FastAPI Service (AI Service)**: Xử lý hóa đơn, nhận dạng giọng nói và các tác vụ AI.

Khi người dùng tải hóa đơn hoặc ghi âm, file tạm thời được lưu trong **Amazon S3**.  
**AI Service** truy cập tệp từ S3 để xử lý và trả kết quả lại cho **Aspire Service** hoặc ghi metadata vào **MongoDB Cloud (Free Tier)**.  
Dữ liệu nghiệp vụ chính như người dùng, giao dịch, và ngân sách được lưu trong **Amazon Aurora PostgreSQL (RDS)**.

Tất cả logs, metrics, và cảnh báo từ ECS, API Gateway, và ALB được gửi về **Amazon CloudWatch** để giám sát tập trung.  
Hình ảnh container được lưu trong **Amazon ECR**, và quá trình triển khai được tự động hóa qua **GitHub Actions**.

![IoT Weather Platform Architecture](/images/2-Proposal/cloud_architecture.drawio.png)

_Dịch vụ AWS sử dụng_

- _Amazon CloudFront_: Phân phối nội dung tĩnh toàn cầu và tăng tốc truy cập frontend.
- _Amazon S3_: Lưu trữ website tĩnh, file hóa đơn, và tệp ghi âm.
- _Amazon Cognito_: Xác thực và quản lý người dùng.
- _Amazon API Gateway_: Cổng vào của hệ thống, định tuyến request từ frontend đến backend.
- _Application Load Balancer (ALB)_: Cân bằng tải giữa các container backend trên ECS.
- _Amazon ECS (Fargate)_: Chạy các microservices Aspire (.NET) và FastAPI (AI).
- _Amazon ECR_: Kho lưu trữ image container cho ECS.
- _Amazon Aurora PostgreSQL (RDS)_: Lưu trữ dữ liệu nghiệp vụ chính.
- _MongoDB Cloud (Free 512MB)_: Lưu metadata AI và notification service.
- _Amazon CloudWatch_: Giám sát logs, hiệu năng và cảnh báo hệ thống.
- _Amazon Route 53_: Quản lý DNS và tên miền truy cập.
- _GitHub Actions_: Tự động hóa CI/CD pipeline cho việc build và deploy container.

---

### 4. Triển khai kỹ thuật

_Các giai đoạn triển khai_  
Dự án được chia thành 3 giai đoạn chính, tập trung vào việc xây dựng, tối ưu và triển khai nền tảng quản lý tài chính cá nhân trên AWS:

1. _Nghiên cứu và vẽ kiến trúc_: Nghiên cứu các mô hình microservices và thiết kế kiến trúc tổng thể trên AWS (bao gồm CloudFront, ECS Fargate, RDS, S3, API Gateway, Cognito) — (Tháng 1).
2. _Tính toán chi phí và điều chỉnh giải pháp_: Sử dụng AWS Pricing Calculator để ước tính chi phí, tối ưu lựa chọn dịch vụ nhằm đảm bảo chi phí thấp và dễ triển khai cho người mới học — (Tháng 1–2).
3. _Phát triển, kiểm thử, triển khai_: Xây dựng frontend (Next.js), backend (.NET Aspire), và AI service (FastAPI); kiểm thử tích hợp microservices, sau đó triển khai toàn bộ hệ thống lên AWS bằng ECS Fargate và thiết lập giám sát qua CloudWatch — (Tháng 2–3).

_Yêu cầu kỹ thuật_

- _Frontend_:  
  Ứng dụng web **Next.js** được lưu trữ trên **Amazon S3** và phân phối qua **CloudFront**, giao tiếp với backend thông qua **API Gateway**.  
  Người dùng đăng nhập qua **Amazon Cognito**, nhận token để gọi API bảo mật.

- _Backend_:  
  Viết bằng **.NET Aspire**, triển khai trên **ECS Fargate**.  
  Các service xử lý nghiệp vụ người dùng, giao dịch, ngân sách, kết nối với **RDS PostgreSQL** và **S3**.  
  Container image lưu trong **ECR**, được cập nhật qua pipeline CI/CD từ **GitHub Actions**.

- _AI Service_:  
  Viết bằng **FastAPI**, xử lý hình ảnh hóa đơn và giọng nói, kết nối đến **S3** để đọc dữ liệu.  
  Kết quả được lưu vào **MongoDB Cloud (Free Tier)** và gửi phản hồi cho **Aspire Service** qua API nội bộ hoặc hàng đợi sự kiện.

- _Database_:  
  **Amazon Aurora PostgreSQL** lưu trữ dữ liệu chính (user, transaction, budget).  
  **MongoDB Cloud** lưu metadata AI, notification và dữ liệu phi cấu trúc.  
  Aurora chạy trong Private Subnet để đảm bảo bảo mật và chỉ cho phép truy cập từ ECS.

- _Hạ tầng Cloud_:  
  Sử dụng **Amazon VPC** (multi-AZ), **Application Load Balancer**, và **CloudWatch** để giám sát.  
  Hình ảnh container được lưu trữ trên **ECR** và triển khai qua **ECS Fargate**.  
  CI/CD được thực hiện qua **GitHub Actions** để tự động hóa build và deploy.

- _Bảo mật_:  
  Quản lý quyền truy cập người dùng bằng **Amazon Cognito**.  
  Sử dụng **IAM Roles** cho ECS, S3 và CloudWatch để giới hạn quyền truy cập.  
  **Security Group** được cấu hình chặt chẽ giữa ECS, ALB và RDS để đảm bảo an toàn mạng.

### 5. Lộ trình & Mốc triển khai

- _Trước thực tập (Tháng 0)_: 1 tháng lên kế hoạch.
- _Thực tập (Tháng 1–3)_:
  - Tháng 1: Học AWS và nâng cấp kỹ năng lập trình.
  - Tháng 2: Thiết kế và điều chỉnh kiến trúc.
  - Tháng 3: Triển khai, kiểm thử, đưa vào sử dụng.
- _Sau triển khai_: Nghiên cứu thêm về mobile và triển khai sau tháng thứ 4.

### 6. Ước tính ngân sách

<!-- Có thể xem chi phí trên [AWS Pricing Calculator](https://calculator.aws/#/estimate?id=621f38b12a1ef026842ba2ddfe46ff936ed4ab01)
Hoặc tải [tệp ước tính ngân sách](../attachments/budget_estimation.pdf). -->

### _Chi phí hạ tầng_

**_Trong Free Tier (12 tháng đầu)_**

- _Amazon ECS (Fargate)_: 0,00 USD/tháng (≤ 50 GB-hr CPU, 200 GB-hr RAM).
- _Amazon API Gateway_: 0,00 USD/tháng (≤ 1 triệu request).
- _Amazon RDS (PostgreSQL)_: 0,00 USD/tháng (db.t3.micro 750 giờ, 20 GB lưu trữ).
- _Amazon S3_: 0,00 USD/tháng (≤ 5 GB lưu trữ hóa đơn và file giọng nói).
- _Amazon SQS_: 0,00 USD/tháng (≤ 1 triệu message).
- _Amazon CloudWatch_: 0,00 USD/tháng (≤ 10 custom metrics + 5 GB logs).
- _Amazon Cognito_: 0,00 USD/tháng (≤ 50.000 người dùng hoạt động).
- _Amazon ECR_: 0,00 USD/tháng (500 MB lưu trữ image).
- _Amazon Route 53_: 1,00 USD/tháng (1 domain).
- _MongoDB Atlas (Free Tier)_: 0,00 USD/tháng (M0 Sandbox – 512 MB RAM, Shared Cluster).
- _GitHub Actions_: 0,00 USD/tháng (≤ 2.000 phút build miễn phí).

_Tổng_: **≈ 1,00 USD/tháng**, tương đương **12,00 USD/năm** trong giai đoạn Free Tier.


**_Sau khi hết Free Tier (với 50–100 người dùng)_**

- _Amazon ECS (Fargate)_: 18,00 USD/tháng (3 container nhỏ chạy 24/7, ~0.25 vCPU, 0.5 GB RAM mỗi container).
- _Amazon API Gateway_: 3,50 USD/tháng (≈ 2–3 triệu request).
- _Amazon RDS (PostgreSQL)_: 12,00 USD/tháng (db.t3.micro, 20 GB lưu trữ).
- _Amazon S3_: 2,50 USD/tháng (50 GB lưu trữ + 10.000 request).
- _Amazon SQS / RabbitMQ_: 1,00 USD/tháng (vài triệu message).
- _Amazon CloudWatch_: 3,50 USD/tháng (log + metric cơ bản).
- _Amazon Cognito_: 0,50 USD/tháng (50–100 active user).
- _Amazon ECR_: 0,50 USD/tháng (1 GB image lưu trữ).
- _MongoDB Atlas (Free Tier hoặc M2 Shared Cluster)_: 9,00 USD/tháng (M2 – 2 GB RAM).
- _Amazon Route 53_: 1,00 USD/tháng (1 domain).
- _GitHub Actions_: 2,00 USD/tháng (vượt giới hạn free).

_Tổng_: **≈ 53,50 USD/tháng**, tương đương **642,00 USD/năm** sau khi hết Free Tier.

### 7. Đánh giá rủi ro

_Ma trận rủi ro_

- Mô hình AI nhận dạng sai (voice/bill): Ảnh hưởng trung bình, xác suất trung bình.
- Mất kết nối AWS hoặc lỗi dịch vụ vùng (region): Ảnh hưởng cao, xác suất thấp.
- Vượt ngân sách sử dụng AWS: Ảnh hưởng trung bình, xác suất thấp.
- Lỗi đồng bộ dữ liệu giữa các microservices: Ảnh hưởng trung bình, xác suất trung bình.
- Lộ thông tin người dùng (Cognito/Database): Ảnh hưởng cao, xác suất thấp.

_Chiến lược giảm thiểu_

- AI: Cải thiện mô hình OCR và voice-to-text qua huấn luyện thêm, kiểm thử định kỳ với dữ liệu thực tế.
- AWS Region: Thiết lập triển khai đa vùng (multi-AZ) và backup định kỳ cơ sở dữ liệu RDS.
- Chi phí: Cấu hình **AWS Budget Alert** và tối ưu ECS, S3 theo mức sử dụng thực tế.
- Microservices: Dùng **SQS/RabbitMQ** để đảm bảo xử lý bất đồng bộ và retry khi lỗi.
- Bảo mật: Mã hóa dữ liệu (AES-256, HTTPS), kiểm soát IAM theo nguyên tắc “Least Privilege”.

_Kế hoạch dự phòng_

- Nếu AWS gặp sự cố: Tạm thời chuyển sang lưu trữ dữ liệu giao dịch cục bộ và đồng bộ lại sau khi khôi phục.
- Khôi phục hạ tầng bằng **AWS CloudFormation** hoặc **IaC (Infrastructure as Code)** đã lưu sẵn.
- Giữ bản sao cơ sở dữ liệu định kỳ (RDS snapshot) để phục hồi trong tình huống mất dữ liệu.

### 8. Kết quả kỳ vọng của dự án

- **Tự động hóa nhập liệu tài chính:** Ứng dụng giúp người dùng không cần nhập thủ công, chỉ cần chụp hóa đơn hoặc ghi âm giọng nói để hệ thống tự phân loại chi tiêu.
- **Quản lý tài chính trực quan:** Người dùng có thể xem biểu đồ chi tiêu, báo cáo tháng, và nhận gợi ý tiết kiệm dựa trên hành vi tiêu dùng.
- **Trải nghiệm người dùng tối giản:** Giao diện web thân thiện, thiết kế hiện đại, tối ưu cho thiết bị di động và phù hợp với người mới quản lý tài chính.
- **Hệ thống ổn định, dễ mở rộng:** Kiến trúc microservices giúp dễ dàng bổ sung tính năng mới như nhắc nhở chi tiêu, phân tích dự báo AI, hoặc mở rộng sang mobile app.
- **Chi phí vận hành thấp:** Tận dụng Free Tier AWS và mô hình serverless để duy trì hệ thống với chi phí trung bình < 50 USD/tháng.
- **Nâng cao kỹ năng nhóm phát triển:** Thành viên dự án tiếp cận thực tế với quy trình DevOps, triển khai CI/CD, và tối ưu ứng dụng trên nền tảng cloud.

### 9. Hạn chế của dự án

- **Mô hình AI tiếng Việt còn hạn chế:** Khả năng nhận dạng giọng nói vùng miền hoặc hóa đơn viết tay chưa đạt độ chính xác cao.
- **Chưa có ứng dụng di động riêng:** Phiên bản MVP chỉ hỗ trợ nền web, chưa có mobile app native.
- **Giới hạn người dùng:** Kiến trúc hiện tại chỉ tối ưu cho 50–100 người dùng hoạt động; khi mở rộng quy mô cần tái cấu trúc hạ tầng.
- **Phụ thuộc kết nối Internet:** Mọi thao tác xử lý và lưu trữ đều qua cloud, không thể hoạt động offline.
- **Chưa triển khai hệ thống bảo mật nâng cao:** Mới dừng ở xác thực Cognito và mã hóa cơ bản, chưa có MFA (Multi-Factor Authentication) hay log bảo mật chuyên sâu.
