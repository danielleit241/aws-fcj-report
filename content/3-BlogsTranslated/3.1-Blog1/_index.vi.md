---
title: "Blog 1"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# **Tăng tốc phát triển Generative AI với MLflow 3.0 được quản lý hoàn toàn trên Amazon SageMaker AI**

_Bởi Ram Vittal, Amit Modi, Rahul Easwar, and Sandeep Raveesh-Babu on 10 JUL 2025 in [Amazon SageMaker AI](https://aws.amazon.com/blogs/machine-learning/category/artificial-intelligence/sagemaker/amazon-sagemaker-ai/), [Announcements](https://aws.amazon.com/blogs/machine-learning/category/post-types/announcements/), [Technical How-to](https://aws.amazon.com/vi/blogs/machine-learning/category/post-types/technical-how-to/)_

[Amazon SageMaker](https://aws.amazon.com/sagemaker/) hiện cung cấp hỗ trợ **MLflow 3.0** được quản lý hoàn toàn, giúp đơn giản hóa quá trình thử nghiệm AI và tăng tốc hành trình [**Generative AI**](https://aws.amazon.com/generative-ai/) của bạn từ ý tưởng đến triển khai sản xuất. Bản phát hành này biến **managed MLflow** từ công cụ theo dõi thí nghiệm thành giải pháp **end-to-end observability**, rút ngắn thời gian đưa Generative AI ra thị trường.

Khi khách hàng ở nhiều ngành khác nhau tăng tốc phát triển Generative AI, họ cần khả năng theo dõi thí nghiệm, quan sát hành vi và đánh giá hiệu suất của **models** và **AI applications**. Các **data scientists** và **developers** gặp khó khăn trong việc phân tích hiệu quả của **models** và **AI applications** từ giai đoạn thử nghiệm đến sản xuất, gây khó khăn trong việc tìm nguyên nhân và khắc phục sự cố. Các nhóm dành nhiều thời gian tích hợp công cụ thay vì nâng cao chất lượng của **models** hoặc **generative AI applications**.

Với việc ra mắt **fully managed MLflow 3.0 trên [Amazon SageMaker AI](https://aws.amazon.com/sagemaker-ai/)**, bạn có thể tăng tốc phát triển Generative AI bằng cách dễ dàng theo dõi thí nghiệm và quan sát hành vi của models và AI applications chỉ bằng một công cụ duy nhất. **Tracing capabilities** trong MLflow 3.0 cho phép khách hàng ghi lại **inputs, outputs, metadata** ở mọi bước trong ứng dụng Generative AI, giúp developers nhanh chóng xác định nguồn gốc của lỗi hoặc hành vi bất thường. Bằng cách duy trì lịch sử của từng phiên bản model và ứng dụng, MLflow 3.0 cung cấp khả năng **traceability**, giúp kết nối phản hồi AI với các thành phần gốc. Điều này cho phép developers nhanh chóng truy vết sự cố trực tiếp đến **code, data, hoặc parameters** đã tạo ra nó.

Với các khả năng này, khách hàng sử dụng [**Amazon SageMaker HyperPod**](https://aws.amazon.com/sagemaker/hyperpod/) để train và deploy [**foundation models**](https://aws.amazon.com/what-is/foundation-models/) **(FMs)** giờ đây có thể dùng managed MLflow để theo dõi thí nghiệm, giám sát quá trình training, có insight sâu hơn về hành vi models và AI applications, và quản lý [**ML lifecycle**](https://aws.amazon.com/ai/machine-learning/) ở quy mô lớn. Điều này giảm thời gian khắc phục sự cố và giúp các nhóm tập trung nhiều hơn vào đổi mới.

Bài viết này sẽ giới thiệu các khái niệm cốt lõi của **fully managed MLflow 3.0 trên SageMaker** và cung cấp hướng dẫn kỹ thuật để bạn khai thác các tính năng mới, giúp tăng tốc phát triển ứng dụng Generative AI tiếp theo.

## **Bắt đầu**

Bạn có thể bắt đầu với **MLflow 3.0 được quản lý hoàn toàn trên Amazon SageMaker** để theo dõi thí nghiệm, quản lý models, và tối ưu hóa vòng đời **Generative AI/ML** thông qua [**AWS Management Console**](https://aws.amazon.com/console/)**, [AWS CLI](https://aws.amazon.com/cli/)**, hoặc **API**.

## **Điều kiện cần thiết**

Để bắt đầu, bạn cần:

- Một **AWS account** đã bật billing

- Một [**Amazon SageMaker Studio**](https://aws.amazon.com/sagemaker-ai/studio/) **AI domain** (xem hướng dẫn: [Guide to getting set up with Amazon SageMaker AI](https://docs.aws.amazon.com/sagemaker/latest/dg/gs.html))

## **Cấu hình môi trường của bạn để sử dụng Máy chủ theo dõi MLflow do SageMaker quản lý**

### **Các bước cấu hình:**

1\. Trong **SageMaker Studio UI**, ở bảng **Applications**, chọn **MLflow** → **Create**.

## ![](/images/3-BlogsTranslated/3.1-Blog1/image1.png)

2\. Nhập tên duy nhất cho **tracking server** và chỉ định [**Amazon S3 URI**](https://aws.amazon.com/s3/) nơi lưu trữ **experiment artifacts**. Chọn **Create**. (Mặc định SageMaker sẽ chọn **MLflow v3.0**).

3\. Tuỳ chọn: chọn **Update** để điều chỉnh cài đặt như **server size, tags, [IAM](https://aws.amazon.com/iam/) role**.

Máy chủ sẽ được cấp phát và khởi động tự động, thường mất khoảng 25 phút. Sau khi thiết lập xong, bạn có thể khởi chạy MLflow UI từ SageMaker Studio để bắt đầu tracking các thí nghiệm ML và Generative AI. Để biết thêm chi tiết về cấu hình tracking server, tham khảo [Machine learning experiments using Amazon SageMaker AI with MLflow](https://docs.aws.amazon.com/sagemaker/latest/dg/mlflow.html) trong SageMaker Developer Guide.

Để bắt đầu tracking các thí nghiệm của bạn với SageMaker managed MLflow tracking server vừa tạo, bạn cần cài đặt cả MLflow và gói AWS SageMaker MLflow Python trong môi trường của bạn. Bạn có thể sử dụng [SageMaker Studio managed Jupyter Lab](https://docs.aws.amazon.com/sagemaker/latest/dg/studio-updated-jl-user-guide-create-space.html), [SageMaker Studio Code Editor](https://docs.aws.amazon.com/sagemaker/latest/dg/code-editor-use-studio.html), một môi trường phát triển tích hợp (IDE) cục bộ, hoặc môi trường khác có hỗ trợ AI workloads để tracking với SageMaker managed MLflow tracking server.

Để cài đặt cả hai gói Python bằng lệnh pip:  
`pip install mlflow==3.0 sagemaker-mlflow==0.1.0`

Để kết nối và bắt đầu ghi log các thí nghiệm AI, tham số, và mô hình của bạn trực tiếp lên managed MLflow trên SageMaker, hãy thay thế [Amazon Resource Name](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference-arns.html) (ARN) của SageMaker MLflow tracking server của bạn:

```
import mlflow

# SageMaker MLflow ARN
tracking_server_arn = "arn:aws:sagemaker:<Region>:<Account_id>:mlflow-tracking-server/<Name>"

# Enter ARN
mlflow.set_tracking_uri(tracking_server_arn)
mlflow.set_experiment("customer_support_genai_app")
```

Bây giờ môi trường của bạn đã được cấu hình và sẵn sàng để tracking các thí nghiệm với SageMaker Managed MLflow tracking server.

## **Triển khai tracing và version tracking cho ứng dụng Generative AI**

Các ứng dụng Generative AI có nhiều thành phần, bao gồm code, cấu hình và dữ liệu, điều này có thể trở nên khó quản lý nếu không có versioning một cách hệ thống. Một thực thể **LoggedModel** trong managed MLflow 3.0 đại diện cho mô hình AI, agent, hoặc ứng dụng Generative AI của bạn trong một experiment. Nó cung cấp khả năng tracking thống nhất các model artifacts, execution traces, evaluation metrics và metadata trong suốt vòng đời phát triển. Một trace là bản ghi log của input, output và các bước trung gian từ một lần thực thi ứng dụng. Traces mang lại cái nhìn sâu về hiệu suất ứng dụng, luồng thực thi, và chất lượng phản hồi, giúp debugging và đánh giá. Với LoggedModel, bạn có thể tracking và so sánh các phiên bản khác nhau của ứng dụng, giúp dễ dàng xác định vấn đề, triển khai phiên bản tốt nhất, và duy trì hồ sơ rõ ràng về những gì đã được triển khai và khi nào.

Để triển khai version tracking và tracing với managed MLflow 3.0 trên SageMaker, bạn có thể thiết lập một danh tính model có version bằng cách sử dụng **Git commit hash**, đặt nó làm **active model context** để tất cả các trace sau đó sẽ tự động liên kết với phiên bản cụ thể này, bật tính năng automatic logging cho các tương tác với [**Amazon Bedrock**](https://aws.amazon.com/bedrock/), và sau đó thực hiện một API call tới **Claude 3.5 Sonnet** của Anthropic, lệnh gọi này sẽ được tracing đầy đủ với input, output và metadata được tự động ghi lại trong model context đã thiết lập. Managed MLflow 3.0 tracing đã được tích hợp sẵn với nhiều thư viện Generative AI khác nhau và cung cấp trải nghiệm tracing tự động chỉ với một dòng lệnh cho tất cả các thư viện được hỗ trợ. Để biết thêm thông tin về các thư viện được hỗ trợ, hãy tham khảo [**Supported Integrations**](https://mlflow.org/docs/latest/genai/tracing/app-instrumentation/automatic/#supported-integrations) trong MLflow documentation.

```
# 1. Define your application version using the git commit
logged_model= "customer_support_agent"
logged_model_name = f"{logged_model}-{git_commit}"

# 2.Set the active model context - traces will be linked to this
mlflow.set_active_model(name=logged_model_name)

# 3.Set auto logging for your model provider
mlflow.bedrock.autolog()

# 4. Chat with your LLM provider
# Ensure that your boto3 client has the necessary auth information
bedrock = boto3.client(
 service_name="bedrock-runtime",
 region_name="<REPLACE_WITH_YOUR_AWS_REGION>",
)
model = "anthropic.claude-3-5-sonnet-20241022-v2:0"
messages = [{ "role": "user", "content": [{"text": "Hello!"}]}]
# All intermediate executions within the chat session will be logged
bedrock.converse(modelId=model, messages=messages)
```

Sau khi ghi lại thông tin này, bạn có thể theo dõi các thí nghiệm Generative AI và **LoggedModel** cho agent trong **Managed MLflow 3.0 tracking server UI**, như minh họa trong ảnh chụp màn hình sau.

## ![](/images/3-BlogsTranslated/3.1-Blog1/image2.png)

Bên cạnh chức năng **one-line auto tracing**, **MLflow** cung cấp **Python SDK** để bạn có thể [thủ công instrument](https://mlflow.org/docs/latest/genai/tracing/app-instrumentation/manual-tracing/) code và thao tác với các trace. Tham khảo notebook mẫu sagemaker_mlflow_strands.ipynb trong kho [**aws-samples GitHub repository**](https://github.com/aws-samples/genai-ml-platform-examples/tree/main/operations/sagemaker-mlflow-trace-evaluate-langgraph-agent), nơi chúng tôi sử dụng **MLflow manual instrumentation** để trace [**Strands Agents**](https://strandsagents.com/). Với khả năng tracing trong **fully managed MLflow 3.0**, bạn có thể ghi lại **inputs, outputs, và metadata** liên quan đến từng bước trung gian của một request, từ đó dễ dàng xác định nguồn gốc của lỗi và các hành vi bất ngờ.

Những khả năng này mang lại **observability** cho workload AI của bạn bằng cách thu thập thông tin chi tiết về quá trình thực thi của các **workload services, nodes, và tools**, và bạn có thể quan sát dưới tab **Traces**.

## ![](/images/3-BlogsTranslated/3.1-Blog1/image3.png)

Bạn có thể kiểm tra từng **trace**, như minh họa trong hình dưới đây, bằng cách chọn **request ID** trong tab **traces** cho trace mà bạn muốn xem.

## ![](/images/3-BlogsTranslated/3.1-Blog1/image4.png)

**MLflow 3.0 được quản lý toàn diện trên Amazon SageMaker** cũng giới thiệu khả năng gắn thẻ cho traces. Tags là các cặp khóa-giá trị có thể thay đổi mà bạn có thể gắn vào traces để bổ sung metadata và ngữ cảnh giá trị. Trace tags giúp việc tổ chức, tìm kiếm, và lọc traces trở nên đơn giản dựa trên các tiêu chí như phiên người dùng, môi trường, phiên bản mô hình, hoặc đặc tính hiệu năng. Bạn có thể thêm, cập nhật, hoặc xóa tags ở bất kỳ giai đoạn nào—trong khi thực thi trace bằng cách sử dụng mlflow.update_current_trace() hoặc sau khi một trace đã được ghi log thông qua MLflow APIs hoặc UI.

Managed MLflow 3.0 làm cho việc tìm kiếm và phân tích traces trở nên liền mạch, giúp các nhóm nhanh chóng xác định vấn đề, so sánh hành vi của agent, và tối ưu hóa hiệu năng. Giao diện người dùng tracing và Python API đều hỗ trợ tính năng lọc mạnh mẽ, vì vậy bạn có thể đi sâu vào traces dựa trên các thuộc tính như trạng thái, tags, người dùng, môi trường, hoặc thời gian thực thi như được minh họa trong ảnh chụp màn hình bên dưới.

Ví dụ, bạn có thể ngay lập tức tìm tất cả traces có lỗi, lọc theo môi trường production, hoặc tìm traces từ một request cụ thể. Khả năng này rất quan trọng cho việc gỡ lỗi, phân tích chi phí, và cải tiến liên tục của các ứng dụng Generative AI.

Ảnh chụp màn hình sau đây hiển thị các dấu vết được trả về khi tìm kiếm thẻ ‘Production’.

## ![](/images/3-BlogsTranslated/3.1-Blog1/image5.png)

Đoạn mã sau đây cho thấy cách bạn có thể sử dụng chức năng tìm kiếm tất cả traces trong môi trường production với trạng thái thành công:

\# Search for traces in production environment with successful status  
traces \= mlflow.search_traces( filter_string="attributes.status \= 'OK' AND tags.environment \= 'production'")

## **Hướng dẫn sử dụng AI tạo sinh với tính năng theo dõi MLflow**

Việc xây dựng và triển khai các generative AI agents như chat-based assistants, code generators hoặc customer support assistants đòi hỏi khả năng quan sát sâu về cách các agent này tương tác với [large language models](https://aws.amazon.com/what-is/large-language-model/) (LLMs) và các công cụ bên ngoài. Trong một quy trình agentic workflow điển hình, agent sẽ lặp qua các bước reasoning, gọi LLMs và sử dụng các công cụ hoặc hệ thống con như search APIs hoặc [Model Context Protocol (MCP)](https://modelcontextprotocol.io/introduction) servers cho đến khi hoàn thành tác vụ của người dùng. Những tương tác phức tạp, nhiều bước này khiến việc **debugging, tối ưu hóa và theo dõi chi phí** trở nên đặc biệt thách thức.

Các công cụ observability truyền thống trở nên thiếu hiệu quả trong generative AI vì các quyết định của agent, các lệnh gọi tool, và phản hồi từ LLM đều mang tính động và phụ thuộc vào ngữ cảnh. **Managed MLflow 3.0 tracing** cung cấp khả năng quan sát toàn diện bằng cách ghi lại mọi lần gọi LLM, tool invocation, và decision point trong workflow của agent. Bạn có thể sử dụng dữ liệu trace end-to-end này để:

- **Debug agent behavior** – Xác định chính xác nơi reasoning của agent bị lệch hướng hoặc lý do tại sao nó tạo ra output bất ngờ.

- **Monitor tool usage** – Khám phá cách và thời điểm các external tools được gọi, đồng thời phân tích tác động của chúng đến chất lượng và chi phí.

- **Track performance and cost** – Đo lường latency, token usage và chi phí API ở mỗi bước của agentic loop.

- **Audit and govern** – Duy trì logs chi tiết để phục vụ compliance và phân tích.

Hãy tưởng tượng một kịch bản thực tế sử dụng **managed MLflow 3.0 tracing UI** cho một finance customer support agent mẫu, được trang bị một công cụ để truy xuất dữ liệu tài chính từ datastore. Trong khi bạn đang phát triển một generative AI customer support agent hoặc phân tích hành vi của agent trong production, bạn có thể quan sát cách phản hồi của agent và việc thực thi có thể (hoặc không) gọi đến product database tool để đưa ra khuyến nghị chính xác hơn.

Ví dụ minh họa: trace đầu tiên (hiển thị trong screenshot bên dưới) cho thấy agent xử lý một user query mà không gọi bất kỳ tool nào. Trace ghi lại prompt, agent response và các decision points của agent. Phản hồi của agent thiếu chi tiết cụ thể về sản phẩm. Trace cho thấy rõ ràng rằng không có external tool nào được gọi, và bạn nhanh chóng nhận ra hành vi này trong reasoning chain của agent.

## ![](/images/3-BlogsTranslated/3.1-Blog1/image6.png)

Trace thứ hai (hiển thị trong screenshot bên dưới) ghi lại cùng một agent, nhưng lần này agent quyết định gọi **product database tool**. Trace này log lại **tool invocation**, dữ liệu sản phẩm được trả về, và cách agent tích hợp thông tin này vào phản hồi cuối cùng. Tại đây, bạn có thể quan sát thấy chất lượng câu trả lời được cải thiện, độ trễ (**latency**) tăng nhẹ, và chi phí API bổ sung do mức sử dụng **token** cao hơn.

## ![](/images/3-BlogsTranslated/3.1-Blog1/image7.png)

Bằng cách so sánh các trace này song song, bạn có thể **debug** lý do vì sao agent đôi khi bỏ qua việc sử dụng tool, tối ưu hóa thời điểm và cách thức gọi tool, đồng thời cân bằng giữa chất lượng với **latency** và chi phí. **Tracing UI** của MLflow giúp các **agentic loops** trở nên minh bạch, dễ hành động, và liền mạch để phân tích ở quy mô lớn. Agent mẫu trong bài viết này cùng với toàn bộ mã nguồn cần thiết đều có sẵn trên [**aws-samples GitHub repository**](https://github.com/aws-samples/genai-ml-platform-examples/tree/main/operations/sagemaker-mlflow-trace-evaluate-langgraph-agent), nơi bạn có thể tái tạo và điều chỉnh cho các ứng dụng của riêng mình.

## **Dọn dẹp tài nguyên**

Sau khi được tạo, một **SageMaker managed MLflow tracking server** sẽ phát sinh chi phí cho đến khi bạn xóa hoặc dừng nó. Việc tính phí cho tracking server dựa trên thời gian máy chủ chạy, kích thước được chọn, và lượng dữ liệu được log vào tracking server. Bạn có thể dừng tracking server khi không sử dụng để tiết kiệm chi phí, hoặc có thể xóa chúng bằng **API** hoặc **SageMaker Studio UI**. Để biết thêm chi tiết về giá, hãy tham khảo [**Amazon SageMaker pricing**](https://aws.amazon.com/sagemaker/pricing?p=pm&c=sm&z=4).

## **Kết luận**

**Fully managed MLflow 3.0 on Amazon SageMaker AI** hiện đã khả dụng. Hãy bắt đầu với **sample code** trong [**aws-samples GitHub repository**](https://github.com/aws-samples/genai-ml-platform-examples/tree/main/operations/sagemaker-mlflow-trace-evaluate-langgraph-agent). Chúng tôi mời bạn khám phá tính năng mới này và trải nghiệm sự hiệu quả cũng như khả năng kiểm soát nâng cao mà nó mang lại cho các dự án ML của bạn. Để tìm hiểu thêm, hãy truy cập [**Machine Learning Experiments using Amazon SageMaker with MLflow**](https://aws.amazon.com/sagemaker-ai/experiments/).

Để biết thêm thông tin, hãy tham khảo [**SageMaker Developer Guide**](https://docs.aws.amazon.com/sagemaker/latest/dg/mlflow.html) và gửi phản hồi đến [**AWS re:Post for SageMaker**](https://repost.aws/tags/TAT80swPyVRPKPcA0rsJYPuA) hoặc thông qua kênh **AWS Support** thông thường của bạn.

## **Thông tin về các tác giả**

<div style="display:flex; flex-direction:column; gap:1rem;">

  <div style="display:flex; align-items:flex-start; gap:1rem;">
    <img src="/images/3-BlogsTranslated/3.1-Blog1/image8.png" alt="Ram Vittal" style="width:120px; height:120px; object-fit:cover; border-radius:8px;" />
    <div>
      <strong>Ram Vittal</strong><br/>
      Ram Vittal là <strong>Kiến trúc sư Giải pháp ML Chính (Principal ML Solutions Architect)</strong> tại AWS. Ông có hơn 3 thập kỷ kinh nghiệm trong việc kiến trúc và xây dựng các ứng dụng phân tán, lai (hybrid) và đám mây. Ông đam mê xây dựng các giải pháp <strong>AI/ML</strong> và <strong>dữ liệu lớn</strong> an toàn, có khả năng mở rộng và đáng tin cậy để giúp các khách hàng doanh nghiệp trong hành trình áp dụng và tối ưu hóa đám mây nhằm cải thiện kết quả kinh doanh. Trong thời gian rảnh, ông lái xe mô tô và đi dạo cùng chú chó sheep-a-doodle ba tuổi của mình!
    </div>
  </div>

  <div style="display:flex; align-items:flex-start; gap:1rem;">
    <img src="/images/3-BlogsTranslated/3.1-Blog1/image9.png" alt="Sandeep Raveesh" style="width:120px; height:120px; object-fit:cover; border-radius:8px;" />
    <div>
      <strong>Sandeep Raveesh</strong><br/>
      Sandeep Raveesh là <strong>Kiến trúc sư Giải pháp Chuyên gia GenAI (GenAI Specialist Solutions Architect)</strong> tại AWS. Anh làm việc với khách hàng trong suốt hành trình <strong>AIOps</strong> của họ, bao gồm đào tạo mô hình, <strong>Tạo sinh Tăng cường Truy xuất (RAG)</strong>, <strong>Tác tử GenAI (GenAI Agents)</strong> và mở rộng quy mô các trường hợp sử dụng <strong>GenAI</strong>. Anh cũng tập trung vào các chiến lược <strong>Go-To-Market</strong> giúp AWS xây dựng và điều chỉnh các sản phẩm để giải quyết các thách thức của ngành trong lĩnh vực <strong>Trí tuệ Nhân tạo Tạo sinh (Generative AI)</strong>. Bạn có thể tìm thấy Sandeep trên <a href="https://www.linkedin.com/in/sandeep-raveesh-750aa630" target="_blank">LinkedIn</a>.
    </div>
  </div>

  <div style="display:flex; align-items:flex-start; gap:1rem;">
    <img src="/images/3-BlogsTranslated/3.1-Blog1/image10.png" alt="Amit Modi" style="width:120px; height:120px; object-fit:cover; border-radius:8px;" />
    <div>
      <strong>Amit Modi</strong><br/>
      Amit Modi là <strong>Trưởng bộ phận Sản phẩm</strong> cho <strong>SageMaker AIOps và Quản trị (Governance)</strong>, cùng với <strong>AI có trách nhiệm (Responsible AI)</strong> tại AWS. Với hơn một thập kỷ kinh nghiệm trong lĩnh vực B2B, ông đã xây dựng các sản phẩm và đội ngũ có khả năng mở rộng, thúc đẩy đổi mới và mang lại giá trị cho khách hàng trên toàn cầu.
    </div>
  </div>

  <div style="display:flex; align-items:flex-start; gap:1rem;">
    <img src="/images/3-BlogsTranslated/3.1-Blog1/image11.png" alt="Rahul Easwar" style="width:120px; height:120px; object-fit:cover; border-radius:8px;" />
    <div>
      <strong>Rahul Easwar</strong><br/>
      Rahul Easwar là <strong>Giám đốc Sản phẩm Cấp cao (Senior Product Manager)</strong> tại AWS, dẫn dắt mảng <strong>MLflow được quản lý</strong> và <strong>Ứng dụng AI Đối tác (Partner AI Apps)</strong> trong nhóm <strong>SageMaker AIOps</strong>. Với hơn 15 năm kinh nghiệm từ các công ty khởi nghiệp đến công nghệ doanh nghiệp, anh tận dụng nền tảng khởi nghiệp và bằng <strong>MBA</strong> từ <strong>Chicago Booth</strong> để xây dựng các nền tảng <strong>ML</strong> có khả năng mở rộng, giúp đơn giản hóa việc áp dụng <strong>AI</strong> cho các tổ chức trên toàn thế giới. Kết nối với Rahul trên <a href="https://www.linkedin.com/in/rahul-easwar/" target="_blank">LinkedIn</a> để tìm hiểu thêm về công việc của anh trong lĩnh vực nền tảng <strong>ML</strong> và các giải pháp <strong>AI</strong> cho doanh nghiệp.
    </div>
  </div>
</div>
