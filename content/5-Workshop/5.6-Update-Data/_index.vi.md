---
title: "Cập nhật dữ liệu"
date: "2025-09-09"
weight: 6
chapter: false
pre: " <b> 5.6. </b> "
---

#### Mục tiêu

Một trong những ưu điểm lớn nhất của RAG so với việc Fine-tuning (huấn luyện lại) mô hình là khả năng cập nhật dữ liệu nhanh chóng. Khi doanh nghiệp có văn bản quy định mới, bạn chỉ cần nạp nó vào Knowledge Base, và AI sẽ "học" được ngay lập tức.

Trong phần này, chúng ta sẽ thực hiện kịch bản giả lập sau:

1.  Hỏi AI một thông tin chưa từng tồn tại (AI sẽ trả lời không biết).
2.  Cung cấp thông tin đó vào hệ thống thông qua việc upload file mới.
3.  Hỏi lại câu cũ để chứng kiến AI trả lời chính xác ngay lập tức.

#### Các bước thực hiện

**Bước 1: Kiểm chứng sự "thiếu hiểu biết" ban đầu**

Chúng ta cần xác nhận rằng AI hiện tại không biết gì về thông tin bí mật mà chúng ta sắp tạo ra.

1.  Quay lại giao diện **Chatbot Streamlit** (bạn đã tạo ở Phần 5) hoặc dùng cửa sổ **Test Knowledge Base** trên Console.
2.  Đặt một câu hỏi về thông tin giả định không có thật.
    - _Ví dụ:_ _"Mật mã kích hoạt của Dự án Omega là gì?"_
3.  **Quan sát kết quả:** AI sẽ trả lời rằng nó không tìm thấy thông tin trong tài liệu được cung cấp hoặc sẽ cố gắng trả lời chung chung (nếu không bị giới hạn).

> ![Ảnh minh họa AI trả lời không biết thông tin về dự án Omega](link_anh_ai_dont_know)

**Bước 2: Tạo dữ liệu mới**

Chúng ta sẽ tạo một file văn bản chứa "bí mật" này để nạp vào hệ thống.

1.  Trên máy tính của bạn, mở **Notepad** (Windows) hoặc **TextEdit** (Mac).
2.  Copy và dán nội dung sau vào file:
    ```text
    THÔNG BÁO MẬT:
    Dự án bí mật Omega chính thức khởi động từ ngày 01/12/2025.
    Mật mã kích hoạt là: "AWS-ROCKS-2025-SINGAPORE".
    Người quản lý dự án là Mr. Robot.
    Vui lòng bảo mật thông tin này tuyệt đối.
    ```
3.  Lưu file với tên: `du-an-bi-mat.txt`.

> ![Ảnh minh họa nội dung file text bí mật trên máy tính](link_anh_secret_file_content)

**Bước 3: Upload và Đồng bộ (Sync)**

Bây giờ, chúng ta sẽ đưa kiến thức mới này vào "bộ não" của AI.

1.  Truy cập **S3 Console**, tìm đến bucket cũ của bạn (`rag-workshop-<tên-bạn>`).
2.  Click **Upload** -> **Add files** -> Chọn file `du-an-bi-mat.txt` -> **Upload**.

> ![Ảnh minh họa file đã upload thành công lên S3](link_anh_upload_secret_s3)

3.  Chuyển sang **Amazon Bedrock Console** -> Chọn **Knowledge bases** ở menu trái.
4.  Click vào tên Knowledge Base của bạn.
5.  Kéo xuống phần **Data source**, đánh dấu chọn vào data source (`s3-datasource`).
6.  Click nút **Sync** (Màu cam).
7.  **Chờ đợi:** Đợi khoảng 30 giây đến 1 phút cho đến khi cột **Status** chuyển từ `Syncing` sang `Available`.

> ![Ảnh minh họa quá trình Sync hoàn tất trên Bedrock Console](link_anh_sync_new_data_success)

**Bước 4: Kiểm tra lại (The "Wow" Moment)**

Hệ thống đã có kiến thức mới. Hãy thử thách AI một lần nữa.

1.  Quay lại giao diện **Chatbot Streamlit** (Không cần tải lại trang hay khởi động lại server).
2.  Hỏi lại đúng câu hỏi lúc nãy: _"Mật mã kích hoạt của Dự án Omega là gì?"_
3.  **Kết quả mong đợi:**
    - AI trả lời chính xác: _"Mật mã là AWS-ROCKS-2025-SINGAPORE"_.
    - AI trích dẫn nguồn là file `du-an-bi-mat.txt`.

> ![Ảnh minh họa AI trả lời chính xác sau khi cập nhật dữ liệu](link_anh_ai_knows_secret)

#### Kết luận

Bạn vừa chứng kiến sức mạnh thực sự của RAG!

- **Không cần sửa code.**
- **Không cần train lại model.**
- **Chỉ cần Sync dữ liệu.**

Chatbot của bạn đã trở nên thông minh hơn và cập nhật thông tin mới nhất chỉ trong vài thao tác đơn giản. Đây chính là lý do các doanh nghiệp lựa chọn giải pháp này để xây dựng trợ lý ảo nội bộ.
