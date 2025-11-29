---
title: "Khởi tạo Knowledge Base"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 5.3.1 </b> "
---

#### Mục tiêu

Chúng ta sẽ sử dụng trình hướng dẫn (Wizard) của Amazon Bedrock để thiết lập toàn bộ kiến trúc RAG. Quá trình này sẽ kết nối nguồn dữ liệu S3, mô hình Embedding và tự động khởi tạo kho lưu trữ Vector (OpenSearch Serverless).

#### Các bước thực hiện

1.  Đăng nhập vào **AWS Management Console** và truy cập dịch vụ **Amazon Bedrock**.
2.  Tại menu bên tay trái, chọn mục **Knowledge bases**.
3.  Click nút **Create knowledge base** ở góc phải màn hình.

> ![Ảnh minh họa nút Create Knowledge Base trên giao diện Bedrock](link_anh_create_kb_button)

**Bước 1: Cấu hình Knowledge Base**

Tại màn hình cấu hình đầu tiên:

1.  **Knowledge base name:** Nhập tên cho knowledge base (Ví dụ: `kb-workshop-<tên-bạn>`).
2.  **IAM permissions:** Chọn tùy chọn **Create and use a new service role**.
3.  **Service role name:** Giữ nguyên giá trị mặc định mà AWS gợi ý (bắt đầu bằng `AmazonBedrockExecutionRoleForKnowledgeBase_...`).
4.  Click **Next**.

> ![Ảnh minh họa Step 1: Điền tên KB và chọn IAM Role](link_anh_step1_details)

**Bước 2: Cấu hình nguồn dữ liệu**

Kết nối tới S3 Bucket chứa tài liệu:

1.  **Data source name:** Nhập tên nguồn dữ liệu (Ví dụ: `s3-datasource`).
2.  **S3 URI:**
    - Click nút **Browse S3**.
    - Trong cửa sổ hiện ra, chọn bucket `rag-workshop-<tên-bạn>` mà bạn đã tạo ở phần trước.
    - Click **Choose**.
3.  Click **Next**.

> ![Ảnh minh họa Step 2: Chọn S3 Bucket làm nguồn dữ liệu](link_anh_step2_datasource)

**Bước 3: Lưu trữ & Xử lý**

Đây là bước quan trọng nhất để định nghĩa mô hình AI và nơi lưu trữ vector:

1.  **Embeddings model:**
    - Click **Select model**.
    - Chọn model: **Titan Embeddings G1 - Text v2**.
2.  **Vector database:**
    - Chọn tùy chọn: **Quick create a new vector store - Recommended**.
    - _Lưu ý:_ Tùy chọn này cho phép AWS tự động tạo một cụm **Amazon OpenSearch Serverless** để chứa dữ liệu, giúp bạn không cần quản lý hạ tầng thủ công.
3.  Click **Next**.

> ![Ảnh minh họa Step 3: Chọn Titan Embeddings v2 và Quick Create Vector Store](link_anh_step3_storage)

**Bước 4: Kiểm tra và tạo Knowledge Base**

1.  Kiểm tra lại toàn bộ thông tin cấu hình tại trang Review.
2.  Đảm bảo các mục S3 URI và Model đã chính xác.
3.  Kéo xuống cuối trang và click nút **Create knowledge base**.

> ![Ảnh minh họa Step 4: Màn hình Review và nút Create](link_anh_step4_review)

**Bước 5: Chờ đợi khởi tạo**

Sau khi nhấn Create, hệ thống sẽ bắt đầu quá trình khởi tạo hạ tầng Vector Store ngầm bên dưới.

- **Thời gian chờ:** Khoảng **2 - 5 phút**.
- **Lưu ý:** Vui lòng không tắt trình duyệt trong lúc này.
- **Thành công:** Khi màn hình hiển thị thông báo màu xanh **"Knowledge base created successfully"**, bạn đã hoàn tất bước này và sẵn sàng cho phần tiếp theo.

> ![Ảnh minh họa màn hình thông báo tạo thành công màu xanh](link_anh_step5_success)
