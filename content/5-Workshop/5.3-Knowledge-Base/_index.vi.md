---
title: "Tạo và cấu hình Knowledge Base"
date: "2025-09-09"
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---

#### 1. Mục tiêu

Sau khi đã hoàn tất việc chuẩn bị môi trường và dữ liệu, bước tiếp theo là thiết lập thành phần cốt lõi của kiến trúc RAG. Trong phần này, chúng ta sẽ khởi tạo **Knowledge Base**, đóng vai trò là cơ chế trung gian thông minh giúp kết nối nguồn dữ liệu phi cấu trúc với khả năng suy luận của các mô hình nền tảng.

Chúng ta sẽ hoàn thành 3 mục tiêu kỹ thuật quan trọng:

1.  **Thiết lập quy trình tự động hóa (Automated Pipeline):** Cấu hình Knowledge Base để tự động hóa toàn bộ quy trình xử lý dữ liệu RAG (bao gồm trích xuất, phân đoạn văn bản và tạo vector) nhằm loại bỏ các thao tác xử lý thủ công.
2.  **Khởi tạo Vector Store:** Triển khai một bộ sưu tập (collection) trên **Amazon OpenSearch Serverless** để lưu trữ các vector ngữ nghĩa, phục vụ cho việc truy xuất thông tin chính xác và hiệu quả.
3.  **Đồng bộ hóa dữ liệu (Data Ingestion):** Thực hiện quy trình nạp dữ liệu lần đầu, chuyển đổi các tài liệu tĩnh từ S3 thành các chỉ mục có thể tìm kiếm (searchable vectors) trong hệ thống.

#### 2. Các thành phần chính

Trong quá trình cấu hình này, chúng ta sẽ tương tác và kết nối các dịch vụ sau:

- **Knowledge Bases for Amazon Bedrock:** Dịch vụ quản lý đóng vai trò điều phối luồng dữ liệu, kết nối nguồn tin và thực hiện truy vấn ngữ nghĩa.
- **Amazon Titan Embeddings G1 - Text v2:** Mô hình chuyên dụng để chuyển đổi dữ liệu văn bản (Text) thành các vector số học (Embeddings) với độ chính xác cao và hỗ trợ đa ngôn ngữ.
- **Amazon OpenSearch Serverless:** Cơ sở dữ liệu vector được quản lý toàn diện (fully managed), đảm nhận vai trò lưu trữ và thực hiện thuật toán tìm kiếm tương đồng (k-NN).

#### 3. Các bước triển khai

1. [Khởi tạo Knowledge Base](5.3.1-Create-KB/)
2. [Kiểm tra Vector Store và Đồng bộ dữ liệu](5.3.2-Sync-Data/)
