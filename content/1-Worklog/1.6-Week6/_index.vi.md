---
title: "Worklog Tuần 6"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6:

- **Containerization Mastery:** Làm chủ quy trình đóng gói và vận hành ứng dụng trên nền tảng Container (Docker) và điều phối quy mô lớn với Amazon ECS.
- **Automation & Optimization:** Tự động hóa quy trình phát triển phần mềm (CI/CD) và tối ưu hóa trải nghiệm người dùng toàn cầu thông qua CDN.
- **Decoupled Architecture:** Hiểu và triển khai kiến trúc Event-driven/Decoupled sử dụng các dịch vụ hàng đợi và thông báo của AWS.
- **Modern Backend Development:** Xây dựng các API hiệu năng cao, bảo mật và dễ bảo trì sử dụng Framework hiện đại FastAPI (Python).

### Công việc thực hiện trong tuần này:

| Day | Task                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Start Date | Completion Date | Reference Material                                                                           |
| :-- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :------------------------------------------------------------------------------------------- |
| 1   | **Containerization & Orchestration (Docker & ECS)** <br> - **Docker Deployment:** Đóng gói ứng dụng full-stack (Frontend/Backend/DB) vào container. Quản lý Images với **Docker Hub** và **Amazon ECR**. Cấu hình Nginx làm Reverse Proxy. <br> - **Amazon ECS:** Triển khai quản lý container trên quy mô lớn. Phân biệt **EC2 Launch Type** và **AWS Fargate** (Serverless). <br> - **Deployment Strategies:** Thực hành các chiến lược triển khai trên ECS: **Rolling Update** (giảm thiểu downtime) và **Blue/Green** (chuyển đổi lưu lượng an toàn).               | 13/10/2025 | 13/10/2025      | [Module Re-hand-on](https://github.com/danielleit241/aws-fcj-learning/tree/main/Re-hand-ons) |
| 2   | **Content Delivery & CI/CD Automation** <br> - **CDN Optimization (Lab 9.4):** Tích hợp **Amazon CloudFront** với S3 Static Hosting, giảm độ trễ truy cập toàn cầu (từ ~200ms xuống ~30ms) và thiết lập bảo mật SSL/Custom Domain. <br> - **Serverless CI/CD (Lab 8.4):** Xây dựng quy trình tự động hóa với **AWS CodePipeline**. <br> &nbsp;&nbsp; + **CI:** Tự động build và test code (CodeBuild). <br> &nbsp;&nbsp; + **CD:** Tự động triển khai artifacts lên môi trường Staging/Production (CodeDeploy).                                                         | 14/10/2025 | 14/10/2025      | [Module Re-hand-on](https://github.com/danielleit241/aws-fcj-learning/tree/main/Re-hand-ons) |
| 3   | **Decoupled Architecture (SQS & SNS)** <br> - **Amazon SQS (Message Queue):** Thiết kế hệ thống xử lý đơn hàng phân tán, sử dụng Standard Queue (high throughput) và FIFO Queue (đảm bảo thứ tự) để tách biệt các thành phần hệ thống. <br> - **Amazon SNS (Pub/Sub):** Cấu hình cơ chế thông báo bất đồng bộ (Fan-out pattern) tới nhiều endpoints (Lambda, SQS, Email/SMS). <br> - **Integration:** Kết hợp SNS và SQS để xây dựng kiến trúc Event-driven tin cậy và có khả năng mở rộng cao.                                                                         | 15/10/2025 | 15/10/2025      | [Module Re-hand-on](https://github.com/danielleit241/aws-fcj-learning/tree/main/Re-hand-ons) |
| 4   | **Modern API Development với FastAPI (Part 1)** <br> - **Framework Fundamentals:** Làm quen với **FastAPI** (Python), tận dụng kiến trúc ASGI cho hiệu năng cao và tự động sinh tài liệu (Swagger UI/ReDoc). <br> - **Modular Design:** Cấu trúc dự án sử dụng **APIRouter** để phân chia module (Users, Items, Auth) giúp dễ dàng bảo trì. <br> - **Data Validation:** Sử dụng **Pydantic** schemas để định nghĩa và kiểm tra dữ liệu đầu vào/đầu ra tự động. <br> - **Database Setup:** Tích hợp **SQLAlchemy**, thiết lập kết nối cơ sở dữ liệu và quản lý Sessions. | 16/10/2025 | 16/10/2025      |                                                                                              |
| 5   | **Advanced FastAPI Implementation (Part 2)** <br> - **Security & Auth:** Triển khai cơ chế xác thực bảo mật sử dụng **OAuth2** với Password Flow và **JWT Tokens** (Access/Refresh tokens). <br> - **Database Operations:** Xây dựng đầy đủ các API CRUD, xử lý quan hệ dữ liệu (Relationships) trong SQLAlchemy. <br> - **Testing & CI/CD:** Viết Unit/Integration tests với **pytest**. Thiết lập pipeline (GitHub Actions) để tự động test và deploy ứng dụng (Zero-downtime).                                                                                       | 17/10/2025 | 17/10/2025      |                                                                                              |

### Thành tựu tuần 6:

- **Vận hành ECS thành thạo:** Đã đóng gói và triển khai thành công ứng dụng Full-stack lên Amazon ECS, nắm vững các chiến lược deployment (Rolling/Blue-Green).
- **Tối ưu hóa quy trình DevOps:** Xây dựng thành công pipeline CI/CD không máy chủ và giảm độ trễ truy cập ứng dụng từ 200ms xuống 30ms nhờ CloudFront.
- **Kiến trúc hệ thống tin cậy:** Thiết kế hệ thống xử lý tin nhắn bất đồng bộ, đảm bảo tính tách biệt và khả năng mở rộng giữa các thành phần.
- **Xây dựng Secure API:** Hoàn thiện Backend với FastAPI bao gồm đầy đủ các tính năng: Xác thực JWT, kết nối Database qua ORM và kiểm thử tự động.
