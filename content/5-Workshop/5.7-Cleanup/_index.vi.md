---
title: "Dọn dẹp tài nguyên"
date: "2025-09-09"
weight: 7
chapter: false
pre: " <b> 5.7. </b> "
---

#### Mục tiêu

Để tránh phát sinh chi phí không mong muốn sau khi kết thúc bài thực hành, chúng ta cần xóa bỏ các tài nguyên đã tạo.

> ⚠️ **CẢNH BÁO:**
> Việc xóa **Knowledge Base** KHÔNG tự động xóa **Vector Store (OpenSearch Serverless)**. Bạn bắt buộc phải xóa thủ công OpenSearch Serverless Collection vì đây là dịch vụ tốn chi phí nhất trong bài Lab này.

#### Các bước thực hiện

**Bước 1: Xóa Knowledge Base**

1.  Truy cập **Amazon Bedrock Console** -> **Knowledge bases**.
2.  Chọn vào ô tròn cạnh tên Knowledge Base của bạn.
3.  Click nút **Delete**.
4.  Một hộp thoại hiện ra, nhập tên Knowledge Base để xác nhận (hoặc gõ `delete`).
5.  Click **Delete**.

> ![Ảnh minh họa thao tác xóa Knowledge Base](link_anh_delete_kb)

**Bước 2: Xóa Vector Store**

1.  Truy cập dịch vụ **Amazon OpenSearch Service**.
2.  Tại menu bên trái, mục **Serverless**, chọn **Collections**.
3.  Bạn sẽ thấy một Collection có tên dạng `bedrock-knowledge-base-...`.
4.  Chọn vào ô tròn cạnh tên Collection đó.
5.  Click nút **Delete**.
6.  Gõ `confirm` hoặc tên collection để xác nhận xóa.
7.  Click **Delete**.

> ![Ảnh minh họa thao tác xóa OpenSearch Collection](link_anh_delete_opensearch)

**Bước 3: Xóa dữ liệu trên S3**

1.  Truy cập dịch vụ **Amazon S3**.
2.  Chọn bucket `rag-workshop-<tên-bạn>`.
3.  Click nút **Empty** (Làm rỗng) trước.
    - Gõ `permanently delete` để xác nhận xóa hết các file bên trong.
4.  Sau khi bucket đã rỗng, quay lại danh sách Buckets.
5.  Chọn lại bucket đó và click nút **Delete**.
6.  Nhập tên bucket để xác nhận.

> ![Ảnh minh họa thao tác Empty và Delete S3 Bucket](link_anh_delete_s3)

**Bước 4: Dừng ứng dụng trên CloudShell**

1.  Quay lại tab **CloudShell**.
2.  Tại cửa sổ dòng lệnh (nơi đang chạy Streamlit), nhấn tổ hợp phím `Ctrl + C` để dừng server.
3.  Đóng tab trình duyệt CloudShell.
4.  Phiên làm việc của CloudShell sẽ tự động hủy sau 20 phút không hoạt động, bạn không cần xóa gì thêm ở đây.

> ![Ảnh minh họa terminal CloudShell đã dừng ứng dụng](link_anh_stop_cloudshell)

#### Hoàn tất

Chúc mừng bạn đã hoàn thành trọn vẹn Workshop **"Xây dựng ứng dụng RAG với Amazon Bedrock"**. Hệ thống của bạn đã được dọn dẹp sạch sẽ và an toàn!
