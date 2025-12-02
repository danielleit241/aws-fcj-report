---
title: "Worklog Tuần 3"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu tuần 3:

- Hiểu triết lý bảo mật AWS (“Security is Job Zero”) và **Mô hình Trách nhiệm chia sẻ**.
- Thành thạo các dịch vụ **Quản lý danh tính & truy cập**: IAM Users, Groups, Roles, Policies, Permission Boundaries, Organizations, Identity Center, Cognito.
- Ứng dụng **AWS KMS** để mã hóa dữ liệu, tích hợp CloudTrail và phân tích logs bằng Athena.
- Nắm vững các **dịch vụ cơ sở dữ liệu AWS**: RDS, Aurora, Redshift, ElastiCache và các khái niệm cơ bản SQL, NoSQL, OLTP, OLAP.
- Triển khai **Amazon RDS** với Multi-AZ, subnet groups, backup/restore để đảm bảo tính sẵn sàng và khả năng phục hồi.

### Công việc thực hiện trong tuần này:

| Day | Task                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | Start Date | Completion Date | Reference Material                                                                 |
| :-- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :--------------------------------------------------------------------------------- |
| 1   | **AWS Security & Identity Management** <br> - **Security Fundamentals:** Nghiên cứu Mô hình Trách nhiệm chung (Shared Responsibility Model) và nguyên tắc "Security is Job Zero". <br> - **Identity Management:** Phân tích chuyên sâu về **IAM** (Users, Groups, Roles, Policies) và quản lý truy cập tập trung qua **AWS Organizations** & **Identity Center**. <br> - **App Security:** Tìm hiểu **Amazon Cognito** (User/Identity Pools) cho xác thực ứng dụng. <br> - **Compliance:** Khám phá mã hóa dữ liệu với **AWS KMS** và giám sát tuân thủ qua **Security Hub**. | 22/09/2025 | 22/09/2025      | [Module 05](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-05) |
| 2   | **Hands-on Lab: IAM Policy & Role Configuration** <br> - **IAM Basics (Lab 02):** Thực hành tạo User/Group và áp dụng nguyên tắc đặc quyền tối thiểu (Least Privilege). <br> - **Advanced Roles (Lab 44):** Cấu hình **IAM Role** với các điều kiện (Conditions) nâng cao (IP, thời gian) để kiểm soát quyền truy cập chặt chẽ. <br> - **Instance Profile (Lab 48):** Cấu hình IAM Role cho EC2 Instance, loại bỏ việc hardcode Access Keys trong mã nguồn ứng dụng.                                                                                                          | 23/09/2025 | 23/09/2025      | [Module 05](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-05) |
| 3   | **Hands-on Lab: Advanced Security Implementation** <br> - **Federated Identity (Lab 18):** Cấu hình **Amazon Cognito** để liên kết danh tính và xác thực người dùng từ Identity Provider bên ngoài. <br> - **Permission Boundaries (Lab 30):** Thiết lập ranh giới quyền hạn (Permissions Boundaries) để giới hạn quyền tối đa cho User/Role. <br> - **Data Encryption (Lab 33):** Quản lý khóa mã hóa (CMK) với **AWS KMS** và tích hợp **CloudTrail** để kiểm toán hoạt động truy xuất khóa.                                                                                | 24/09/2025 | 24/09/2025      | [Module 05](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-05) |
| 4   | **AWS Database Services Fundamentals** <br> - **Database Concepts:** Phân biệt các mô hình cơ sở dữ liệu: Quan hệ (RDBMS) vs Phi quan hệ (NoSQL), OLTP vs OLAP. <br> - **Managed RDBMS:** Nghiên cứu **Amazon RDS** (Multi-AZ, Read Replicas) và **Amazon Aurora** (Cloud-native, Serverless). <br> - **Specialized DBs:** Tìm hiểu **Amazon Redshift** cho kho dữ liệu (Data Warehousing) và **Amazon ElastiCache** cho bộ nhớ đệm (Caching).                                                                                                                                | 25/09/2025 | 25/09/2025      | [Module 06](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-06) |
| 5   | **Hands-on Lab: Deploying & Managing Amazon RDS** <br> - **Infrastructure Setup:** Thiết lập mạng VPC, Subnet Groups và Security Groups tách biệt cho tầng Database (Lab 05). <br> - **Deployment:** Khởi tạo **Amazon RDS** Instance (Multi-AZ) và kết nối an toàn từ Web Server (EC2). <br> - **Operations:** Thực hành quy trình Backup & Restore, quản lý Snapshots và khôi phục dữ liệu theo thời điểm (Point-in-Time Recovery).                                                                                                                                         | 26/09/2025 | 26/09/2025      | [Module 06](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-06) |

### Thành tựu Tuần 3:

- **Dịch vụ bảo mật:**

  - Áp dụng thực tế **Mô hình Trách nhiệm chia sẻ**.
  - Quản lý IAM với Users, Groups, Roles, Policies, Conditions và Permission Boundaries.
  - Tích hợp IAM Role với EC2 để loại bỏ rủi ro khi dùng Access Keys cố định.
  - Thực hành **Liên kết danh tính (Identity Federation)** với Cognito (Google, Facebook, SAML).
  - Quản lý tập trung nhiều tài khoản bằng AWS Organizations và Identity Center.

- **Mã hóa & Giám sát:**

  - Tạo và quản lý **KMS CMK** cho việc mã hóa.
  - Mã hóa dữ liệu trong S3 bằng KMS.
  - Ghi lại hoạt động khóa với CloudTrail và phân tích bằng Athena.

- **Dịch vụ cơ sở dữ liệu:**

  - Hiểu sự khác biệt giữa **RDBMS và NoSQL**, OLTP và OLAP.
  - Triển khai **Amazon RDS** với Multi-AZ, subnet groups, backup tự động, snapshots, và phục hồi theo thời gian (point-in-time recovery).
  - Nghiên cứu **Aurora** (Backtrack, Global DB, Cloning), **Redshift** (MPP, Spectrum), và **ElastiCache** (Redis, Memcached).

- **Thực hành:**
  - Hoàn thành nhiều bài lab: IAM Basics, IAM Roles & Conditions, IAM Roles for Applications, Cognito Federation, IAM Permission Boundaries, KMS Encryption, RDS Deployment.
  - Xây dựng được môi trường RDS an toàn với khả năng backup và phục hồi dữ liệu.
