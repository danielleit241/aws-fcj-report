---
title: "Kiểm thử Chatbot (RAG)"
date: "2025-09-09"
weight: 4
chapter: false
pre: " <b> 5.4. </b> "
---

#### Mục tiêu

Sau khi đã nạp dữ liệu thành công vào Vector Store, đây là lúc chúng ta kiểm chứng thành quả. Trong phần này, bạn sẽ đóng vai người dùng cuối, đặt câu hỏi cho Chatbot ngay trên giao diện AWS Console để xem hệ thống RAG hoạt động như thế nào.

Chúng ta sẽ tập trung vào 2 yếu tố:

1.  **Độ chính xác:** AI có trả lời đúng dựa trên tài liệu không?
2.  **Tính minh bạch:** AI có trích dẫn được nguồn gốc (Citation) của thông tin không?

#### 2. Các bước thực hiện

**Bước 1: Cấu hình cửa sổ kiểm thử**

Để bắt đầu chat, chúng ta cần chọn Mô hình nền tảng (Foundation Model) sẽ đóng vai trò là "người trả lời".

1.  Tại giao diện chi tiết Knowledge Base của bạn, nhìn sang khung bên phải màn hình có tiêu đề **Test knowledge base**.
2.  Click nút **Select model**.

> ![Ảnh minh họa nút Select Model trên khung Test bên phải](link_anh_test_select_model_btn)

3.  Trong bảng chọn hiện ra:
    - **Category:** Chọn `Anthropic`.
    - **Model:** Chọn `Claude 3 Sonnet` (hoặc _Claude 3.5 Sonnet_ / _Haiku_ tùy vào model bạn đã kích hoạt).
    - **Throughput:** Giữ nguyên `On-demand`.
4.  Click **Apply**.

> ![Ảnh minh họa bảng cấu hình chọn Model Claude 3](link_anh_test_config_model)

**Bước 2: Thực hiện hội thoại (Chat)**

Bây giờ, hãy thử đặt một câu hỏi liên quan đến nội dung tài liệu bạn đã tải lên.

1.  Tại ô nhập liệu (Message input), gõ câu hỏi của bạn.
    - _Ví dụ:_ Nếu bạn upload tài liệu "Quy trình nghỉ phép", hãy hỏi: _"Tôi cần làm gì để xin nghỉ phép 3 ngày?"_.
2.  Click **Run**.
3.  **Quan sát kết quả:**
    - AI sẽ suy nghĩ trong vài giây (đang tra cứu Vector Store).
    - Sau đó, nó sẽ trả lời bằng ngôn ngữ tự nhiên, tóm tắt thông tin tìm được.

> ![Ảnh minh họa câu hỏi và câu trả lời của AI trong khung chat](link_anh_test_chat_response)

**Bước 3: Kiểm chứng nguồn dữ liệu**

Đây là tính năng quan trọng nhất của RAG giúp phân biệt với ChatGPT thông thường: khả năng chứng minh nguồn gốc thông tin.

1.  Trong câu trả lời của AI, hãy chú ý đến các số nhỏ (footnote) hoặc dòng chữ **Show source details**.
2.  Click vào các số đó hoặc nút chi tiết.
3.  Một cửa sổ **Source details** sẽ hiện ra, hiển thị:
    - **Source chunk:** Đoạn văn bản gốc chính xác mà AI đã tìm thấy trong tài liệu.
    - **Score:** Điểm số tương đồng (độ liên quan).
    - **S3 Location:** Đường dẫn đến file gốc.

> ![Ảnh minh họa cửa sổ Source Details hiển thị đoạn văn bản gốc](link_anh_test_citations)

_Việc nhìn thấy đoạn văn bản gốc này chứng minh rằng AI không "bịa đặt" (hallucinate) mà thực sự đang đọc tài liệu của bạn._

**Bước 4: Thử nghiệm với câu hỏi không liên quan (Optional)**

Để xem hệ thống phản ứng thế nào khi không tìm thấy thông tin.

1.  Hỏi một câu hoàn toàn không liên quan đến tài liệu.
    - _Ví dụ:_ _"Ai là người đầu tiên đặt chân lên mặt trăng?"_ (Trong khi tài liệu của bạn là về Tài chính).
2.  **Kết quả mong đợi:**
    - AI có thể trả lời dựa trên kiến thức chung của nó (nếu không bị giới hạn).
    - HOẶC AI sẽ trả lời _"Sorry, I am unable to answer your question based on the retrieved data"_ (Xin lỗi, tôi không tìm thấy thông tin trong dữ liệu được cung cấp) - Đây là hành vi lý tưởng của ứng dụng RAG doanh nghiệp.

> ![Ảnh minh họa phản hồi khi hỏi câu hỏi ngoài lề](link_anh_test_negative_case)
