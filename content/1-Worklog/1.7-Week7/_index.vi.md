---
title: "Worklog Tuần 7"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7:

- Ôn tập và củng cố kiến thức lý thuyết về các dịch vụ cốt lõi của AWS và nguyên tắc kiến trúc tốt nhất.
- Luyện làm các câu hỏi thi AWS Cloud Practitioner hàng ngày để cải thiện khả năng nhận diện dịch vụ và phân tích tình huống.
- Tăng cường hiểu biết về bảo mật AWS, thiết kế mạng, chiến lược lưu trữ, các lựa chọn compute và mô hình sẵn sàng của cơ sở dữ liệu.
- Xây dựng khả năng lựa chọn dịch vụ AWS phù hợp dựa trên yêu cầu doanh nghiệp, chi phí và kỳ vọng vận hành.

### Công việc thực hiện trong tuần này:

| Day | Task                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | Start Date | Completion Date | Reference Material                                                                  |
| :-- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :---------------------------------------------------------------------------------- |
| 1   | **Cloud Concepts & Well-Architected Framework** <br> - **Cloud Value:** Nghiên cứu lợi ích của Cloud: chuyển đổi CapEx sang OpEx, khả năng co giãn (Elasticity) và đổi mới nhanh chóng. <br> - **Performance Services:** Phân biệt kịch bản sử dụng: **CloudFront** (Caching content), **Global Accelerator** (Routing qua AWS backbone), và **Route 53** (DNS Management). <br> - **Well-Architected Framework:** Ôn tập 6 trụ cột (Operational Excellence, Security, Reliability, Performance, Cost, Sustainability) và các từ khóa liên quan. <br> - **Infrastructure as Code:** Hiểu vai trò của **CloudFormation** (Automated deployment) và **AWS Service Catalog** (Quản lý danh mục dịch vụ). | 20/10/2025 | 20/10/2025      | [Module Review](https://github.com/danielleit241/aws-fcj-learning/tree/main/Review) |
| 2   | **Networking, VPC Components & Hybrid Connectivity** <br> - **VPC Structure:** Ôn tập CIDR, Subnet isolation và quy hoạch mạng Public/Private. <br> - **Hybrid Connectivity:** So sánh **AWS Site-to-Site VPN** (Internet, encrypted) và **AWS Direct Connect** (Dedicated, low latency). <br> - **Gateways:** Phân biệt **Internet Gateway** (Inbound/Outbound cho Public subnet) và **NAT Gateway** (Outbound only cho Private subnet). <br> - **Security Layers:** So sánh **Security Groups** (Stateful, cấp Instance) và **Network ACLs** (Stateless, cấp Subnet). <br> - **Routing:** Nghiên cứu các chính sách Route 53: Failover, Weighted, Geolocation.                                      | 21/10/2025 | 21/10/2025      | [Module Review](https://github.com/danielleit241/aws-fcj-learning/tree/main/Review) |
| 3   | **Databases, High Availability & Migration** <br> - **Amazon RDS:** Phân biệt **Multi-AZ** (High Availability/Disaster Recovery) và **Read Replicas** (Scaling read workloads). <br> - **Security:** Tìm hiểu mã hóa Database (KMS) và xác thực bằng IAM Auth cho MySQL/PostgreSQL. <br> - **Migration Tools:** Sử dụng **DMS** cho việc di chuyển dữ liệu liên tục và **SCT** để chuyển đổi schema giữa các engine khác nhau. <br> - **Use Cases:** Phân biệt **DynamoDB** (NoSQL, micro-second latency) và **Redshift** (Analytics, Petabyte-scale).                                                                                                                                                | 22/10/2025 | 22/10/2025      | [Module Review](https://github.com/danielleit241/aws-fcj-learning/tree/main/Review) |
| 4   | **S3 Storage Architecture & Security Controls** <br> - **Storage Classes:** Lựa chọn lớp lưu trữ tối ưu: Standard, Intelligent-Tiering (tự động tối ưu chi phí), Glacier/Deep Archive (lưu trữ lâu dài). <br> - **Storage Comparison:** Phân biệt S3 (Object), EFS/FSx (Shared File), và EBS (Block storage cho EC2). <br> - **Access Control:** Phân biệt **IAM Policies** (User-based) và **S3 Bucket Policies** (Resource-based). Cấu hình Block Public Access. <br> - **Disaster Recovery:** Tìm hiểu tính năng Cross-Region Replication (CRR) để đảm bảo an toàn dữ liệu cấp vùng.                                                                                                               | 23/10/2025 | 23/10/2025      | [Module Review](https://github.com/danielleit241/aws-fcj-learning/tree/main/Review) |
| 5   | **Compute, Pricing & Operational Efficiency** <br> - **EC2 Pricing Models:** Lựa chọn mô hình giá: **On-Demand** (ngắn hạn, không đoán trước), **Reserved/Savings Plans** (dài hạn, ổn định), **Spot** (linh hoạt, giá rẻ). <br> - **Architecture:** Thiết kế kiến trúc HA với **Elastic Load Balancer** kết hợp **Auto Scaling Group**. <br> - **Serverless:** Ôn tập **AWS Lambda** cho các tác vụ event-driven và tối ưu chi phí vận hành. <br> - **Operational Tools:** Sử dụng **EC2 Image Builder** để tạo AMI chuẩn và **Compute Optimizer** để gợi ý tối ưu tài nguyên.                                                                                                                       | 24/10/2025 | 24/10/2025      | [Module Review](https://github.com/danielleit241/aws-fcj-learning/tree/main/Review) |

### Thành tựu tuần 7:

- Hoàn thành 2–3 bộ đề luyện thi AWS Cloud Practitioner mỗi ngày với sự tiến bộ đều đặn về hiệu suất.
- Ôn lại lý thuyết và các tình huống thực tế liên quan các miền chính của AWS bao gồm Compute, Storage, Networking, Security và Databases.
- Cải thiện khả năng phân biệt các dịch vụ AWS có chức năng tương tự như:
  Elastic Load Balancing vs Route 53 vs Global Accelerator,
  S3 storage classes vs EBS vs EFS,
  Multi-AZ vs Read Replicas trong RDS.
- Hiểu sâu cơ sở lý thuyết về các lựa chọn tối ưu hóa chi phí (On-Demand, Reserved Instances, Savings Plans, Spot Instances).
- Củng cố kiến thức lý thuyết về quản lý danh tính và truy cập: IAM users, roles, policies, MFA, nguyên tắc least privilege.
- Nâng cao hiểu biết về AWS Well-Architected Framework và sáu trụ cột của nó cho các câu hỏi yêu cầu trong kỳ thi.
