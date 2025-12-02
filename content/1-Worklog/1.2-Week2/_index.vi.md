---
title: "Worklog Tuần 2"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu tuần 2:

- Học và thực hành dịch vụ Compute của AWS (EC2, AMI, EBS, Auto Scaling, ELB).
- Nắm vững kỹ năng giám sát và sao lưu với CloudWatch và AWS Backup.
- Tìm hiểu dịch vụ lưu trữ: S3, Storage Gateway, FSx.
- Thực hành triển khai, mở rộng và host website tĩnh.

### Công việc thực hiện trong tuần này:

| Day | Task                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | Start Date | Completion Date | Reference Material                                                                                                                                                       |
| :-- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | **AWS Compute & EC2 Administration** <br> - **Compute Theory:** Nghiên cứu kiến trúc Amazon EC2, hệ thống ảo hóa Nitro Hypervisor, các loại hình Instance và chiến lược tối ưu chi phí (Spot, Reserved, Savings Plans). <br> - **Storage for Compute:** Phân biệt EBS (Block storage) và Instance Store (Ephemeral storage); quản lý AMI và Snapshots. <br> - **Hands-on Lab 04:** <br> &nbsp;&nbsp; + Khởi tạo hạ tầng EC2 (Linux & Windows) trong môi trường VPC. <br> &nbsp;&nbsp; + Thực hành kết nối an toàn qua SSH (Linux) và RDP (Windows). <br> &nbsp;&nbsp; + Triển khai ứng dụng Node.js (CRUD User Management) trực tiếp trên EC2. | 14/09/2025 | 15/09/2025      | [Module 03](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-03)                                                                                       |
| 2   | **High Availability & Monitoring Operations** <br> - **Scaling & Load Balancing (Lab 06):** <br> &nbsp;&nbsp; + Cấu hình **Auto Scaling Group** để đảm bảo khả năng mở rộng tự động. <br> &nbsp;&nbsp; + Triển khai **Elastic Load Balancer (ELB)** phân phối tải ứng dụng. <br> - **Observability (Lab 08):** Thiết lập **Amazon CloudWatch** để thu thập Metrics, Logs và tạo Alarms cảnh báo bất thường hệ thống. <br> - **Data Protection (Lab 13):** Xây dựng chiến lược sao lưu tự động với **AWS Backup** cho EC2, RDS và EFS dựa trên RPO/RTO.                                                                                         | 16/09/2025 | 16/09/2025      | [Module 03](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-03)<br>[Module 06](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-06) |
| 3   | **AWS Storage Fundamentals (Amazon S3)** <br> - **Object Storage Architecture:** Nghiên cứu kiến trúc S3, tính chất bất biến của Object và độ bền dữ liệu (11 số 9). <br> - **Storage Classes:** Phân tích các lớp lưu trữ (Standard, Intelligent-Tiering, Glacier) để tối ưu chi phí theo tần suất truy cập. <br> - **Security & Management:** Cấu hình **Bucket Policy**, ACLs, tính năng Versioning (chống ghi đè) và Lifecycle Policy (vòng đời dữ liệu). <br> - **Archive Strategy:** Tìm hiểu quy trình lưu trữ dài hạn giá rẻ với Amazon S3 Glacier và Deep Archive.                                                                    | 17/09/2025 | 17/09/2025      | [Module 04](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-04)                                                                                       |
| 4   | **Hybrid Cloud Storage (Storage Gateway)** <br> - **Hybrid Architecture:** Tìm hiểu giải pháp mở rộng lưu trữ on-premises lên Cloud thông qua AWS Storage Gateway. <br> - **Hands-on Lab 24 (File Gateway):** <br> &nbsp;&nbsp; + Triển khai EC2 mô phỏng Appliance Gateway. <br> &nbsp;&nbsp; + Cấu hình NFS File Share ánh xạ tới S3 Bucket backend. <br> &nbsp;&nbsp; + Thực hành mount ổ đĩa mạng từ Cloud về máy trạm local (mô phỏng).                                                                                                                                                                                                   | 18/09/2025 | 18/09/2025      | [Module 04](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-04)                                                                                       |
| 5   | **Managed File Systems & Static Hosting** <br> - **Amazon FSx (Lab 25):** Triển khai hệ thống file share Windows native (SMB) sử dụng **Amazon FSx for Windows File Server** tích hợp Active Directory. <br> - **Static Website Hosting (Lab 57):** <br> &nbsp;&nbsp; + Host website tĩnh trực tiếp trên S3 Bucket (HTML/CSS/JS). <br> &nbsp;&nbsp; + Tối ưu hiệu năng và bảo mật nội dung thông qua **Amazon CloudFront** (CDN) và OAI (Origin Access Identity). <br> &nbsp;&nbsp; + Cấu hình DNS và quyền truy cập công khai (Public Access/CORS).                                                                                           | 19/09/2025 | 19/09/2025      | [Module 04](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-04)                                                                                       |

### Thành tựu Tuần 2:

1. **Tính toán & Triển khai**

   - Hiểu rõ kiến thức về **Amazon EC2**, kiến trúc và các thành phần liên quan (AMI, Snapshot, Key Pair, EBS).
   - Triển khai và quản lý thành công EC2 cho cả Linux và Windows.
   - Thực hành triển khai ứng dụng thực tế **Node.js CRUD** trên EC2.
   - Nắm được các kỹ thuật tự động hóa với **User Data, Meta Data, AWS Systems Manager**.

2. **Khả năng mở rộng & Tính sẵn sàng cao**

   - Triển khai **EC2 Auto Scaling Group** để tự động điều chỉnh năng lực theo nhu cầu.
   - Cấu hình **Elastic Load Balancer (ELB)** để phân phối lưu lượng.
   - Tích hợp Auto Scaling với Load Balancer nhằm đảm bảo **high availability** và tối ưu chi phí.

3. **Giám sát & Quan sát hệ thống**

   - Sử dụng **Amazon CloudWatch** để giám sát hạ tầng và ứng dụng.
   - Tạo **metrics, dashboards, alarms** để theo dõi tình trạng hệ thống theo thời gian thực.
   - Quản lý log tập trung với **CloudWatch Logs**, thiết lập chính sách lưu trữ và phát hiện bất thường.
   - Thực hành thiết lập giám sát tự động qua **CloudFormation**.

4. **Bảo vệ & Sao lưu dữ liệu**

   - Thiết kế **AWS Backup Plans** cho nhiều dịch vụ (EBS, RDS, DynamoDB, EFS).
   - Áp dụng các mục tiêu **RTO/RPO** trong chiến lược khôi phục dữ liệu.
   - Cấu hình **SNS notifications** để nhận thông báo trạng thái sao lưu và phục hồi.

5. **Lưu trữ & Quản lý dữ liệu**
   - Hiểu rõ **Amazon S3** là dịch vụ lưu trữ đối tượng với lifecycle policies và storage classes.
   - Thực hành các tính năng: **versioning, ACL, Bucket Policy, CORS**.
   - Cấu hình **S3 Static Website Hosting** và kiểm tra truy cập công khai.
   - Tích hợp với **CloudFront** để tăng tốc độ phân phối nội dung và bảo mật bằng OAI.
   - Tìm hiểu **Amazon FSx for Windows File Server**: kiến trúc, tích hợp Windows, và dịch vụ lưu trữ file được quản lý hoàn toàn.
