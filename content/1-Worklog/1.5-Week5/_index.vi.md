---
title: "Worklog Tuần 5"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu tuần 5:

- **Khởi tạo Dự án:** Xác định đề tài, phân tích yêu cầu và lên kế hoạch phát triển cho dự án Personal Finance Management App v2.
- **Tích hợp .NET & AWS:** Nghiên cứu và thực hành tích hợp AWS SDK vào kiến trúc Microservices sử dụng .NET.
- **Làm chủ Networking:** Hiểu sâu về kiến trúc mạng VPC, bảo mật mạng và kết nối lai (Hybrid Connectivity) qua VPN và DNS.
- **Compute Fundamentals:** Nắm vững các khái niệm cốt lõi của Amazon EC2 để lựa chọn tài nguyên tính toán phù hợp.

### Công việc thực hiện trong tuần này:

| Day       | Task                                                                                                                                                                                                                                                                                                                                                                                                                        | Start Date | Completion Date | Reference Material                                                                           |
| :-------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :------------------------------------------------------------------------------------------- |
| 1 | **Nghiên cứu Đề tài & Tích hợp AWS SDK với .NET** <br> - **Project Proposal:** Thảo luận nhóm, đánh giá tính khả thi và lựa chọn đề tài dự án tập trung vào kiến trúc Microservices. <br> - **Tech Stack Integration:** Nghiên cứu cách tích hợp AWS SDK vào .NET. <br> - **Coding Practice:** Viết code mẫu C# thực hiện các tác vụ cơ bản: upload dữ liệu lên S3, truy xuất DynamoDB và gọi Lambda function.              | 06/10/2025 | 06/10/2025      |                                                                                              |
| 2 | **Lập Kế hoạch Dự án & Ước tính Chi phí** <br> - **Requirements Analysis:** Phân tích yêu cầu ứng dụng Quản lý Tài chính Cá nhân v2. <br> - **Agile Planning:** Viết 20 User Stories, chia thành 8 Epics (Wallet, Transaction, AI Voice, OCR...). Lên kế hoạch 2 Sprints. <br> - **Cost Estimation:** Lựa chọn dịch vụ (Cognito, Transcribe, SQS...) và tính toán chi phí vận hành (Free Tier vs Paid) để tối ưu ngân sách. | 07/10/2025 | 07/10/2025      | [Project Documentation](https://gitlab.com/vicobi/vicobi-ai)                                 |
| 3 | **AWS Networking: VPC & Site-to-Site VPN (Lab 03)** <br> - **VPC Architecture:** Cấu hình Custom VPC, chia Subnets, Route Tables, IGW và NAT Gateway. <br> - **Network Security:** Phân biệt và cấu hình Security Groups (Stateful) vs Network ACLs (Stateless). <br> - **Hybrid Connectivity:** Thiết lập AWS Site-to-Site VPN (VGW, CGW) và giám sát kết nối bằng VPC Flow Logs và Reachability Analyzer.                 | 08/10/2025 | 08/10/2025      | [Module Re-hand-on](https://github.com/danielleit241/aws-fcj-learning/tree/main/Re-hand-ons) |
| 4 | **Amazon EC2 & Quản lý Hạ tầng Tính toán** <br> - **EC2 Fundamentals:** Nghiên cứu các loại Instance (T, M, R series) và lựa chọn cấu hình phù hợp (Intel/AMD/Graviton). <br> - **Image Management:** Tìm hiểu về AMI (Amazon Machine Images) để chuẩn hóa môi trường server. <br> - **Backup Strategy:** Xây dựng chiến lược sao lưu dữ liệu sử dụng EBS Snapshots.                                                        | 09/10/2025 | 09/10/2025      | [Module Review](https://github.com/danielleit241/aws-fcj-learning/tree/main/Review)          |
| 5 | **Hybrid DNS với Route 53 Resolver** <br> - **Hybrid DNS Concepts:** Tìm hiểu mô hình phân giải tên miền thống nhất giữa On-premise và AWS. <br> - **Route 53 Resolver:** Cấu hình Outbound Endpoints (forward query từ AWS ra ngoài) và Inbound Endpoints (nhận query từ on-premise vào AWS). <br> - **Resolver Rules:** Thiết lập các quy tắc chuyển tiếp DNS (Forwarding rules) cho các domain cụ thể.                   | 10/10/2025 | 10/10/2025      | [Module Review](https://github.com/danielleit241/aws-fcj-learning/tree/main/Review)          |

### Thành tựu tuần 5:

- **Hoàn thiện kế hoạch dự án:** Đã xây dựng bộ User Stories (20 stories/8 Epics), chia Sprint và ước tính chi phí hạ tầng AWS cho dự án FinTech.
- **Kiểm chứng kỹ thuật (PoC):** Đã viết code mẫu tích hợp thành công AWS SDK với .NET (kết nối S3, DynamoDB).
- **Cấu hình mạng nâng cao:** Thiết lập thành công VPC với Public/Private subnets và mô hình kết nối Site-to-Site VPN.
- **Kiến trúc Hybrid DNS:** Hiểu và thiết kế được luồng phân giải tên miền lai giữa On-premise và AWS sử dụng Route 53 Resolver.
