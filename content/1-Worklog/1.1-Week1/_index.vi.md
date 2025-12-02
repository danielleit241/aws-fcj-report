---
title: "Worklog Tuần 1"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Mục tiêu tuần 1:

- Hiểu các kiến thức cơ bản về **điện toán đám mây** và hạ tầng toàn cầu của AWS.
- Học cách quản lý dịch vụ AWS thông qua **Management Console, CLI và SDK**.
- Tìm hiểu **bảo mật, IAM và quản lý chi phí AWS** thông qua các bài thực hành.
- Xây dựng nền tảng kiến thức về **mạng VPC và kết nối** (Subnet, Route Table, IGW, NAT, Peering, Transit Gateway).
- Thực hành trực tiếp trên AWS với các **bài Lab** để củng cố lý thuyết bằng kỹ năng thực tế.

### Công việc thực hiện trong tuần này:

| Day | Task                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | Start Date | Completion Date | Reference Material                                                                 |
| :-- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :--------------------------------------------------------------------------------- |
| 1   | **AWS Cloud Foundation & IAM Security** <br> - **Cloud Essentials:** Nghiên cứu các khái niệm điện toán đám mây cốt lõi và kiến trúc hạ tầng toàn cầu của AWS (Regions, AZs, Edge Locations). <br> - **Account Management:** Tìm hiểu các mô hình định giá (Pricing) và các gói hỗ trợ (Support Plans). <br> - **Hands-on Lab:** Thiết lập bảo mật tài khoản gốc (Root User), cấu hình **IAM** (Users, Groups, MFA) và thiết lập cảnh báo chi phí với **AWS Budgets**.                                | 08/09/2025 | 08/09/2025      | [Module 01](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-01) |
| 2   | **Networking Fundamentals (VPC Architecture)** <br> - **VPC Design:** Phân tích kiến trúc mạng ảo Amazon VPC, quy hoạch địa chỉ IP (CIDR Blocks) và phân chia Subnet (Public/Private). <br> - **Routing Components:** Tìm hiểu cơ chế định tuyến qua Route Tables, Internet Gateway (IGW) và NAT Gateway cho kết nối Internet. <br> - **Network Interfaces:** Nghiên cứu về Elastic IP (EIP), ENI và các loại VPC Endpoints (Gateway & Interface) để tối ưu kết nối nội bộ.                           | 09/09/2025 | 09/09/2025      | [Module 02](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-02) |
| 3   | **Network Security & Advanced Connectivity** <br> - **Network Security:** So sánh cơ chế bảo mật tầng Instance (**Security Group**) và tầng Subnet (**Network ACL**); giám sát lưu lượng với **VPC Flow Logs**. <br> - **Inter-Connectivity:** Nghiên cứu các mô hình kết nối đa VPC (**VPC Peering**, **Transit Gateway**) và kết nối lai (**VPN**, **Direct Connect**). <br> - **Load Balancing:** Tìm hiểu cơ chế phân tải ứng dụng sử dụng **Elastic Load Balancing (ELB)** (ALB, NLB, GWLB).     | 10/09/2025 | 10/09/2025      | [Module 02](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-02) |
| 4   | **Hands-on Lab: VPC Infrastructure Implementation** <br> - **Infrastructure Setup:** Triển khai thực tế mô hình VPC tiêu chuẩn: Tạo Subnets, IGW, cấu hình Route Table và Security Groups. <br> - **Compute & Connectivity:** Khởi tạo EC2 Instance, thiết lập **NAT Gateway** cho Private Subnet truy cập Internet an toàn. <br> - **Operations:** Thực hành giám sát tài nguyên EC2 qua **CloudWatch** và quản trị phiên kết nối an toàn không dùng SSH qua **SSM Session Manager**.                | 11/09/2025 | 11/09/2025      | [Module 02](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-02) |
| 5   | **Hands-on Lab: Advanced Networking Scenarios** <br> - **Secure Access:** Thực hành kỹ thuật Port Forwarding và quản lý logs tập trung với Session Manager. <br> - **VPC Peering:** Cấu hình kết nối ngang hàng giữa các VPC khác Region/Account và cập nhật bảng định tuyến. <br> - **Transit Gateway:** Triển khai mô hình mạng tập trung (Hub-and-Spoke) để đơn giản hóa định tuyến. <br> - **Hybrid DNS:** Cấu hình **Route 53 Resolver** (Inbound/Outbound Endpoints) để phân giải tên miền lai. | 12/09/2025 | 12/09/2025      | [Module 02](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-02) |

### Thành tựu Tuần 1:

- **Nắm vững kiến thức nền tảng về AWS và Điện toán đám mây**

  - Hiểu khái niệm, lợi ích của cloud computing và hành trình chuyển đổi lên cloud.
  - Nắm vững hạ tầng AWS: Region, AZ, Edge Location, Data Center.

- **Thực hành công cụ quản lý AWS**

  - Sử dụng thành thạo AWS Management Console, AWS CLI, AWS SDK.
  - Tạo và quản lý IAM Users/Groups, kích hoạt MFA, cấu hình Access Keys.

- **Quản lý chi phí và hỗ trợ AWS**

  - Tạo và quản lý các loại Budget khác nhau.
  - Tìm hiểu các gói Support Plans và thực hành mở case hỗ trợ.

- **Kiến thức Networking & Security trên AWS**

  - Xây dựng và cấu hình VPC, Subnet, Route Table, Internet Gateway, NAT Gateway.
  - Triển khai Security Group, Network ACL, VPC Flow Logs.
  - So sánh VPC Peering và Transit Gateway, tìm hiểu kết nối Hybrid (VPN, Direct Connect).

- **Quản lý hệ thống trên AWS**

  - Quản lý EC2 bằng **Session Manager** thay vì SSH.
  - Thực hành Port Forwarding và quản lý Session Logs.
  - Bật giám sát bằng **CloudWatch Monitoring & Alerts**.

- **Giải pháp nâng cao**
  - Cấu hình **VPC Peering** và **Transit Gateway** để kết nối nhiều VPC.
  - Thiết lập **Hybrid DNS** với Route 53 Resolver (Inbound/Outbound Endpoints).
  - Thực hành với **Elastic Load Balancer** (ALB, NLB, CLB, GWLB).

---

👉 **Kết quả:** Sau Tuần 1, tôi đã xây dựng nền tảng vững chắc về AWS cơ bản và các khái niệm mạng ở mức trung cấp, đồng thời hoàn thành nhiều **bài Lab trực tiếp trên AWS** để rèn luyện kỹ năng thực hành.
