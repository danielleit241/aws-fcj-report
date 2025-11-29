---
title: "Workshop"
date: "2025-09-09"
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Xây dựng ứng dụng RAG sử dụng Knowledge Bases for Amazon Bedrock

#### Tổng quan

**Knowledge Bases for Amazon Bedrock** là một tính năng được quản lý toàn diện bởi giúp bạn triển khai kỹ thuật RAG (Retrieval-Augmented Generation) bằng cách kết nối các mô hình nền tảng (Foundation Models) với nguồn dữ liệu nội bộ của bạn để đưa ra các phản hồi chính xác, có dẫn chứng và phù hợp ngữ cảnh.
Phần note nhỏ ở dưới này giải thích về RAG**Knowledge Bases for Amazon Bedrock** là một tính năng được quản lý toàn diện (fully managed) giúp bạn triển khai kỹ thuật RAG (Retrieval-Augmented Generation) bằng cách kết nối các mô hình nền tảng (Foundation Models) với nguồn dữ liệu nội bộ của bạn để đưa ra các phản hồi chính xác, có dẫn chứng và phù hợp ngữ cảnh.

> RAG là kỹ thuật tối ưu hóa đầu ra của mô hình ngôn ngữ lớn (LLM) bằng cách truy xuất thông tin từ cơ sở dữ liệu tin cậy bên ngoài (Retrieval) và bổ sung vào ngữ cảnh (Augmentation) trước khi sinh ra câu trả lời (Generation). Phương pháp này giúp khắc phục giới hạn về dữ liệu huấn luyện lỗi thời và đảm bảo AI trả lời dựa trên thông tin thực tế được cung cấp.

Trong bài lab này, chúng ta sẽ học cách xây dựng một trợ lý AI có khả năng "đọc hiểu" tài liệu riêng của doanh nghiệp. Bạn sẽ thực hiện quy trình từ việc nhập dữ liệu (ingestion), tạo chỉ mục vector, đến việc cấu hình mô hình để trả lời câu hỏi dựa trên tài liệu đó mà không cần quản lý bất kỳ máy chủ nào.

Chúng ta sẽ sử dụng ba thành phần chính để thiết lập luồng xử lý RAG hoàn chỉnh:

- **Data Source (Amazon S3)** - Đóng vai trò là kho chứa "sự thật". Bạn sẽ upload các tài liệu (PDF, Word, Text) vào S3 bucket. Knowledge Base sẽ sử dụng nguồn này để đồng bộ hóa dữ liệu.
- **Vector Store (OpenSearch Serverless)** - Nơi lưu trữ các vector embeddings (dữ liệu đã được mã hóa số học). Khi người dùng đặt câu hỏi, hệ thống sẽ tìm kiếm ngữ nghĩa (semantic search) tại đây để trích xuất các đoạn văn bản liên quan nhất thay vì tìm kiếm từ khóa thông thường.
- **Foundation Model (Claude 3)** - Mô hình ngôn ngữ lớn đóng vai trò là bộ não xử lý. Nó sẽ nhận câu hỏi của người dùng kèm theo thông tin được tìm thấy từ Vector Store, sau đó tổng hợp và sinh ra câu trả lời tự nhiên, chính xác kèm theo trích dẫn nguồn.

#### Kết quả đạt được

Kết thúc workshop, bạn sẽ có một hệ thống Chatbot hoạt động thực tế với các tính năng:

- Chat hỏi đáp về nội dung tài liệu riêng.
- Trả lời chính xác, không bịa đặt.
- Trích dẫn nguồn (biết rõ câu trả lời lấy từ trang nào).
- Triển khai nhanh chóng không cần viết code xử lý dữ liệu phức tạp.

#### Nội dung

1. [Tổng quan về workshop](5.1-Workshop-overview/)
2. [Chuẩn bị môi trường](5.2-Prerequiste/)
3. [Tạo và cấu hình Knowledge Base](5.3-Knowledge-Base/)
4. [Kiểm thử Chatbot (RAG)](5.4-Test-Chatbot/)
5. [Tích hợp ứng dụng Client (Tùy chọn)](5.5-Client-Integration/)
6. [Cập nhật dữ liệu](5.6-Cleanup/)
7. [Dọn dẹp tài nguyên](5.7-Cleanup/)
