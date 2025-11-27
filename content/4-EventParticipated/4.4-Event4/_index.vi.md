---
title: "Event 4"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 4.4. </b> "
---

# Bài thu hoạch “AWS Cloud Mastery Series #1: GENERATIVE AI, RAG & AWS AGENTIC AI”

### Mục Đích Của Sự Kiện

- Nắm vững nghệ thuật **Prompt Engineering** để điều khiển mô hình hiệu quả.
- Khám phá hệ sinh thái các dịch vụ AI có sẵn (Pretrained AI Services) trên AWS.
- Hiểu chuyên sâu về quy trình xây dựng ứng dụng AI với **RAG (Retrieval-Augmented Generation)**.
- Cập nhật xu hướng mới nhất về **Agentic AI** và cách đưa AI Agent từ bản thử nghiệm (POC) ra thực tế (Production) với **Amazon Bedrock AgentCore**.
- Tiếp cận Framework **Pipecat** để xây dựng trợ lý ảo giao tiếp bằng giọng nói thời gian thực.

### Danh Sách Diễn Giả

- **Lâm Tuấn Kiệt** - Sr DevOps Engineer (FPT Software)
- **Danh Hoàng Hiếu Nghị** - AI Engineer (Renova Cloud)
- **Đinh Lê Hoàng Anh** - Cloud Engineer Trainee (First Cloud AI Journey)

### Nội Dung Nổi Bật

#### **1. Prompt Engineering & Foundation Models (Nền Tảng Cốt Lõi)**

Trước khi đi vào các dịch vụ phức tạp, sự kiện nhấn mạnh tầm quan trọng của việc hiểu và giao tiếp với các mô hình nền tảng (Foundation Models) thông qua Amazon Bedrock.

- **Zero-shot / Few-shot Prompting:** Kỹ thuật đưa ra yêu cầu trực tiếp hoặc cung cấp ví dụ mẫu để định hướng câu trả lời.
- **Chain of Thought (CoT):** Kỹ thuật yêu cầu mô hình "suy nghĩ từng bước" (Step-by-step), giúp giải quyết các bài toán logic phức tạp chính xác hơn.

#### **2. Các Dịch Vụ AI Được Huấn Luyện Trước (AWS AI Services)**

Giới thiệu nhóm các API "mì ăn liền" giúp tích hợp tính năng thông minh mà không cần training model:

- **Xử lý hình ảnh/video:** Amazon Rekognition.
- **Xử lý ngôn ngữ:** Amazon Translate, Comprehend, Textract (OCR).
- **Âm thanh:** Amazon Polly (Text-to-Speech), Transcribe (Speech-to-Text).

#### **3. RAG - Retrieval Augmented Generation**

Quy trình giúp AI trả lời dựa trên dữ liệu doanh nghiệp, giảm ảo giác:

- **Embeddings:** Sử dụng _Amazon Titan Text Embeddings V2_ để vector hóa văn bản, phục vụ tìm kiếm ngữ nghĩa.
- **Knowledge Bases for Amazon Bedrock:** Quản lý trọn gói quy trình từ Chunking -> Vector Store -> Retrieval -> Generation.

#### **4. Sự Tiến Hóa Lên Agentic AI (Kỷ Nguyên AI Tác Vụ)**

Sự kiện giới thiệu bước tiến hóa tiếp theo của GenAI:

1.  **GenAI Assistants:** Tuân theo quy tắc, tự động hóa các tác vụ lặp lại.
2.  **GenAI Agents:** Hướng tới mục tiêu cụ thể (Goal-oriented), xử lý chuỗi tác vụ rộng hơn.
3.  **Agentic AI Systems:** Hệ thống đa tác vụ (Multi-agent), hoạt động hoàn toàn tự chủ (Fully autonomous) với sự giám sát tối thiểu của con người.

**Thách thức "Hố sâu ngăn cách" (The Prototype to Production Chasm):**
Việc đưa Agent từ bản thử nghiệm (POC) ra thực tế gặp nhiều trở ngại lớn về:

- **Performance & Scalability:** Hiệu năng và khả năng mở rộng.
- **Security & Governance:** Bảo mật và quản trị dữ liệu.
- **Complexity:** Khó khăn trong việc quản lý bộ nhớ (Memory), kiểm soát quyền truy cập và kiểm toán (Audit) các tương tác của Agent.

#### **5. Amazon Bedrock AgentCore: Giải Pháp Đưa Agent Ra Thị Trường**

Để giải quyết các thách thức trên, AWS giới thiệu **AgentCore** - nền tảng toàn diện để xây dựng và vận hành Agent:

- **Các thành phần chính:**
  - **Runtime & Memory:** Môi trường chạy và khả năng "ghi nhớ" lịch sử tương tác/học tập của Agent.
  - **Identity & Gateway:** Quản lý định danh và cổng kết nối an toàn.
  - **Code Interpreter:** Cho phép Agent tự viết và chạy code để xử lý dữ liệu phức tạp.
  - **Observability:** Khả năng quan sát, theo dõi hoạt động của Agent.
- **Lợi ích:** Giúp lập trình viên tập trung vào logic nghiệp vụ thay vì lo lắng về hạ tầng bảo mật hay cách lưu trữ ngữ cảnh hội thoại.

#### **6. Pipecat: Framework Cho AI Voice Thời Gian Thực**

Một framework mã nguồn mở (Open Source) thú vị được giới thiệu để xây dựng các trợ lý ảo đa phương thức (Multimodal):

- **Đặc điểm:** Tối ưu hóa cho các tác vụ thời gian thực (Real-time) và luồng hội thoại (Streaming).
- **Cơ chế hoạt động (Pipeline):**
  1.  **WebRTC Input:** Nhận tín hiệu âm thanh từ người dùng.
  2.  **STT (Speech-to-Text):** Chuyển giọng nói thành văn bản.
  3.  **LLM Processing:** Xử lý ngôn ngữ tự nhiên để sinh câu trả lời.
  4.  **TTS (Text-to-Speech):** Chuyển văn bản thành giọng nói.
  5.  **Output:** Phát lại âm thanh cho người dùng với độ trễ cực thấp.

### Trải nghiệm chi tiết trong Event

Tham gia buổi workshop giúp tôi mở rộng tầm mắt từ những khái niệm cơ bản đến những công nghệ tiên tiến nhất đang định hình tương lai của AI.

#### 1. Sự chuyển dịch từ "Hỏi - Đáp" sang "Hành động" (Agentic AI)

Điều ấn tượng nhất với tôi là khái niệm **Agentic AI**. Trước đây tôi chỉ nghĩ AI dùng để chat hoặc tóm tắt văn bản. Nhưng qua phần giới thiệu về **AgentCore**, tôi thấy tương lai là các "nhân viên ảo" có thể tự lên kế hoạch, tự dùng công cụ (như trình duyệt web, viết code) để giải quyết công việc phức tạp mà không cần con người cầm tay chỉ việc.

#### 2. Giải quyết bài toán "Production"

Tôi rất tâm đắc với phần chia sẻ về "Hố sâu ngăn cách" giữa POC và Production. Các công cụ như **Amazon Bedrock AgentCore** thực sự là chìa khóa để doanh nghiệp dám tin tưởng giao việc cho AI, nhờ vào các lớp bảo mật (Identity) và kiểm soát (Observability) chặt chẽ mà AWS cung cấp.

#### 3. Tiềm năng của Voice AI với Pipecat

Phần demo về **Pipecat** rất thú vị. Việc kết hợp WebRTC và các mô hình AI để tạo ra một cuộc hội thoại trôi chảy, độ trễ thấp mở ra vô vàn ứng dụng thực tế như: Tổng đài ảo thông minh, Trợ lý phỏng vấn, hay Giáo viên ngoại ngữ AI.

### Kết Luận

Buổi workshop **“Generative AI & Agentic AI on AWS”** là một bức tranh toàn cảnh giá trị:

- **Hiện tại:** Chúng ta có **RAG** và **Prompt Engineering** để làm việc hiệu quả với dữ liệu.
- **Tương lai:** Chúng ta đang bước vào kỷ nguyên **Agentic AI**, nơi các hệ thống tự chủ (Autonomous Agents) sẽ thay đổi cách vận hành doanh nghiệp.
- **Công cụ:** Với hệ sinh thái AWS (Bedrock, AgentCore) và các Framework (Pipecat, LangChain), rào cản kỹ thuật đang dần được xóa bỏ để các kỹ sư có thể hiện thực hóa những ý tưởng đột phá.

#### Một số hình ảnh khi tham gia sự kiện

<!-- ![](/images/4-EventParticipated/event4-3-1.png) -->
