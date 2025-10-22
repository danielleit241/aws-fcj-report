---
title: "Blog 1"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# **Accelerate Generative AI development with fully managed MLflow 3.0 on Amazon SageMaker AI**

_By Ram Vittal, Amit Modi, Rahul Easwar, and Sandeep Raveesh-Babu on 10 JUL 2025 in [Amazon SageMaker AI](https://aws.amazon.com/blogs/machine-learning/category/artificial-intelligence/sagemaker/amazon-sagemaker-ai/), [Announcements](https://aws.amazon.com/blogs/machine-learning/category/post-types/announcements/), [Technical How-to](https://aws.amazon.com/vi/blogs/machine-learning/category/post-types/technical-how-to/)_

[Amazon SageMaker](https://aws.amazon.com/sagemaker/) now offers fully managed support for **MLflow 3.0**, simplifying AI experimentation and accelerating your [**Generative AI**](https://aws.amazon.com/generative-ai/) journey from idea to production. This release turns **managed MLflow** from an experiment-tracking tool into an **end-to-end observability** solution, reducing time to market for Generative AI.

As customers across industries accelerate Generative AI development, they need experiment tracking, behavior observability, and performance evaluation for **models** and **AI applications**. **Data scientists** and **developers** often struggle to analyze model and application performance from experimentation to production, making root-cause analysis and remediation difficult. Teams spend significant time integrating tools instead of improving the quality of their **models** or **generative AI applications**.

With the launch of **fully managed MLflow 3.0 on [Amazon SageMaker AI](https://aws.amazon.com/sagemaker-ai/)**, you can speed up Generative AI development by tracking experiments and observing model and application behavior with a single tool. MLflow 3.0’s **tracing capabilities** let customers record **inputs, outputs, and metadata** at every step of a Generative AI application, helping developers quickly identify the origin of errors or unexpected behavior. By keeping a history of each model and application version, MLflow 3.0 provides **traceability**, connecting AI feedback back to the underlying components. This lets developers trace issues back to the exact **code, data, or parameters** that caused them.

Customers using [**Amazon SageMaker HyperPod**](https://aws.amazon.com/sagemaker/hyperpod/) to train and deploy [**foundation models**](https://aws.amazon.com/what-is/foundation-models/) (FMs) can now use managed MLflow to track experiments, monitor training, gain deeper insights into model and application behavior, and manage the [**ML lifecycle**](https://aws.amazon.com/ai/machine-learning/) at scale. This reduces troubleshooting time and allows teams to focus more on innovation.

This post introduces core concepts of **fully managed MLflow 3.0 on SageMaker** and provides technical guidance so you can leverage the new features to accelerate your next Generative AI application.

## **Get started**

You can get started with **fully managed MLflow 3.0 on Amazon SageMaker** to track experiments, manage models, and optimize the **Generative AI/ML** lifecycle via the [**AWS Management Console**](https://aws.amazon.com/console/), the [AWS CLI](https://aws.amazon.com/cli/), or the **API**.

## **Prerequisites**

To get started you need:

- An **AWS account** with billing enabled

- An [**Amazon SageMaker Studio**](https://aws.amazon.com/sagemaker-ai/studio/) **AI domain** (see the guide: [Guide to getting set up with Amazon SageMaker AI](https://docs.aws.amazon.com/sagemaker/latest/dg/gs.html))

## **Configure your environment to use the SageMaker-managed MLflow tracking server**

### **Configuration steps:**

1. In the **SageMaker Studio UI**, open the **Applications** panel, choose **MLflow**, then select **Create**.

## ![](/images/3-BlogsTranslated/3.1-Blog1/image1.png)

2. Enter a unique name for the **tracking server** and specify the [**Amazon S3 URI**](https://aws.amazon.com/s3/) where experiment artifacts will be stored. Choose **Create**. (SageMaker defaults to **MLflow v3.0**.)

3. Optional: choose **Update** to adjust settings such as **server size, tags, and [IAM](https://aws.amazon.com/iam/) role**.

The server is provisioned and started automatically and typically takes about 25 minutes. After setup completes, you can launch the MLflow UI from SageMaker Studio to begin tracking ML and Generative AI experiments. For more details on tracking server configuration, see Machine learning experiments using Amazon SageMaker AI with MLflow in the SageMaker Developer Guide: https://docs.aws.amazon.com/sagemaker/latest/dg/mlflow.html

To start logging experiments to the SageMaker managed MLflow tracking server you created, install both MLflow and the SageMaker MLflow Python package in your environment. You can use [SageMaker Studio managed Jupyter Lab](https://docs.aws.amazon.com/sagemaker/latest/dg/studio-updated-jl-user-guide-create-space.html), [SageMaker Studio Code Editor](https://docs.aws.amazon.com/sagemaker/latest/dg/code-editor-use-studio.html), a local IDE, or any environment that supports AI workloads to connect to the SageMaker managed MLflow tracking server.

To install both Python packages with pip:
`pip install mlflow==3.0 sagemaker-mlflow==0.1.0`

To connect and start logging your AI experiments, parameters, and models directly to the managed MLflow on SageMaker, replace the Amazon Resource Name (ARN) of your SageMaker MLflow tracking server:

```
import mlflow

# SageMaker MLflow ARN
tracking_server_arn = "arn:aws:sagemaker:<Region>:<Account_id>:mlflow-tracking-server/<Name>"

# Enter ARN
mlflow.set_tracking_uri(tracking_server_arn)
mlflow.set_experiment("customer_support_genai_app")
```

Your environment is now configured and ready to track experiments with the SageMaker managed MLflow tracking server.

## **Implement tracing and version tracking for Generative AI applications**

Generative AI applications have many components — code, configuration, and data — which can become hard to manage without systematic versioning. A **LoggedModel** entity in managed MLflow 3.0 represents your AI model, agent, or Generative AI application within an experiment. It provides unified tracking of model artifacts, execution traces, evaluation metrics, and metadata across the development lifecycle. A trace is a recorded log of inputs, outputs, and intermediate steps from a single application execution. Traces offer deep visibility into application performance, execution flow, and response quality, aiding debugging and evaluation. With LoggedModel, you can track and compare different versions of an application, making it easy to identify issues, deploy the best version, and maintain a clear record of what was deployed and when.

To implement version tracking and tracing with managed MLflow 3.0 on SageMaker, you can establish a model identity with a version using the **Git commit hash**, set it as the **active model context** so subsequent traces automatically link to that specific version, enable automatic logging for interactions with [**Amazon Bedrock**](https://aws.amazon.com/bedrock/), and then make an API call to Anthropic’s **Claude 3.5 Sonnet** — that call will be fully traced, with inputs, outputs, and metadata automatically recorded in the established model context. Managed MLflow 3.0 tracing integrates with a number of Generative AI libraries and provides one-line automatic tracing for all supported libraries. For details on supported libraries, see [**Supported Integrations**](https://mlflow.org/docs/latest/genai/tracing/app-instrumentation/automatic/#supported-integrations) in the MLflow documentation.

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

After recording this information you can view Generative AI experiments and the **LoggedModel** for the agent in the **Managed MLflow 3.0 tracking server UI**, as shown in the screenshot below.

## ![](/images/3-BlogsTranslated/3.1-Blog1/image2.png)

In addition to one-line auto tracing, **MLflow** provides a **Python SDK** so you can [manually instrument](https://mlflow.org/docs/latest/genai/tracing/app-instrumentation/manual-tracing/) your code and work with traces. See the sample notebook sagemaker_mlflow_strands.ipynb in the [**aws-samples GitHub repository**](https://github.com/aws-samples/genai-ml-platform-examples/tree/main/operations/sagemaker-mlflow-trace-evaluate-langgraph-agent), where we use **MLflow manual instrumentation** to trace [**Strands Agents**](https://strandsagents.com/). With tracing in fully managed MLflow 3.0 you can capture **inputs, outputs, and metadata** for each intermediate step of a request to help identify the root cause of errors and unexpected behavior.

These capabilities provide **observability** for your AI workloads by collecting detailed information about the execution of **workload services, nodes, and tools**, and you can inspect them under the **Traces** tab.

## ![](/images/3-BlogsTranslated/3.1-Blog1/image3.png)

You can inspect an individual **trace**, as illustrated below, by selecting the **request ID** for the trace you want to view in the Traces tab.

## ![](/images/3-BlogsTranslated/3.1-Blog1/image4.png)

**Fully managed MLflow 3.0 on Amazon SageMaker** also introduces tagging for traces. Tags are mutable key–value pairs you can attach to traces to add metadata and contextual information. Trace tags make it easy to organize, search, and filter traces by criteria such as user session, environment, model version, or performance characteristics. You can add, update, or remove tags at any time — while a trace is executing using mlflow.update_current_trace() or after a trace has been logged using the MLflow APIs or UI.

Managed MLflow 3.0 makes searching and analyzing traces seamless, helping teams quickly identify issues, compare agent behavior, and optimize performance. Both the tracing UI and the Python API support powerful filtering, so you can dive into traces based on attributes such as status, tags, user, environment, or execution time, as shown in the screenshot below.

For example, you can immediately find all traces with errors, filter by production environment, or find traces for a specific request. This capability is important for debugging, cost analysis, and continuous improvement of Generative AI applications.

The screenshot below shows the traces returned when searching for the tag 'Production'.

## ![](/images/3-BlogsTranslated/3.1-Blog1/image5.png)

The following code shows how you can search for all traces in the production environment with a successful status:

\# Search for traces in production environment with successful status  
traces = mlflow.search_traces(filter_string="attributes.status = 'OK' AND tags.environment = 'production'")

## **Using MLflow tracing for Generative AI**

Building and deploying generative AI agents — such as chat-based assistants, code generators, or customer support assistants — requires deep observability into how those agents interact with [large language models](https://aws.amazon.com/what-is/large-language-model/) (LLMs) and external tools. In a typical agentic workflow, the agent iterates through reasoning steps, calls LLMs, and uses tools or subsystems like search APIs or [Model Context Protocol (MCP)](https://modelcontextprotocol.io/introduction) servers until the user task is completed. These complex, multi-step interactions make **debugging, optimization, and cost tracking** particularly challenging.

Traditional observability tools fall short for generative AI because agent decisions, tool calls, and LLM responses are dynamic and context-dependent. **Managed MLflow 3.0 tracing** provides comprehensive observability by recording every LLM call, tool invocation, and decision point in the agent workflow. You can use this end-to-end trace data to:

- **Debug agent behavior** — pinpoint where an agent’s reasoning went off track or why it produced an unexpected output.

- **Monitor tool usage** — discover when and how external tools are invoked and analyze their impact on quality and cost.

- **Track performance and cost** — measure latency, token usage, and API cost at each step of the agentic loop.

- **Audit and govern** — maintain detailed logs for compliance and analysis.

Imagine a practical scenario using the **managed MLflow 3.0 tracing UI** for a sample finance customer support agent equipped with a tool for retrieving financial data from a datastore. While developing a generative AI customer support agent or analyzing agent behavior in production, you can observe whether the agent’s response and execution invoke the product database tool to provide more accurate recommendations.

Example: the first trace (shown below) captures the agent handling a user query without calling any tools. The trace records the prompt, agent response, and decision points. The agent’s response lacks product-specific detail. The trace clearly shows that no external tool was invoked, which helps you quickly identify this behavior in the agent’s reasoning chain.

## ![](/images/3-BlogsTranslated/3.1-Blog1/image6.png)

The second trace (shown below) records the same agent but this time the agent decides to call the **product database tool**. This trace logs the **tool invocation**, the returned product data, and how the agent integrates that information into the final response. Here, you can observe improved answer quality, slightly increased **latency**, and additional API cost due to higher **token** usage.

## ![](/images/3-BlogsTranslated/3.1-Blog1/image7.png)

By comparing these traces side-by-side you can **debug** why the agent sometimes skips using the tool, optimize when and how tools are called, and balance quality with **latency** and cost. MLflow’s Tracing UI makes agentic loops transparent, actionable, and straightforward to analyze at scale. The sample agent used in this post and the full source code are available in the [**aws-samples GitHub repository**](https://github.com/aws-samples/genai-ml-platform-examples/tree/main/operations/sagemaker-mlflow-trace-evaluate-langgraph-agent) so you can reproduce and adapt it for your own applications.

## **Clean up resources**

After creation, a **SageMaker managed MLflow tracking server** incurs charges until you stop or delete it. Tracking server charges are based on server uptime, selected size, and the amount of data logged to the tracking server. You can stop the tracking server when not in use to save costs, or delete it via the **API** or the **SageMaker Studio UI**. For pricing details, see [**Amazon SageMaker pricing**](https://aws.amazon.com/sagemaker/pricing?p=pm&c=sm&z=4).

## **Conclusion**

**Fully managed MLflow 3.0 on Amazon SageMaker AI** is now available. Get started with the **sample code** in the [**aws-samples GitHub repository**](https://github.com/aws-samples/genai-ml-platform-examples/tree/main/operations/sagemaker-mlflow-trace-evaluate-langgraph-agent). We invite you to explore the new features and experience the increased productivity and control they provide for your ML projects. To learn more, visit [**Machine Learning Experiments using Amazon SageMaker with MLflow**](https://aws.amazon.com/sagemaker-ai/experiments/).

For more information, see the [**SageMaker Developer Guide**](https://docs.aws.amazon.com/sagemaker/latest/dg/mlflow.html) and send feedback to [**AWS re:Post for SageMaker**](https://repost.aws/tags/TAT80swPyVRPKPcA0rsJYPuA) or through your usual AWS Support channels.

## **About the authors**

<div style="display:flex; flex-direction:column; gap:1rem;">

  <div style="display:flex; align-items:flex-start; gap:1rem;">
    <img src="/images/3-BlogsTranslated/3.1-Blog1/image8.png" alt="Ram Vittal" style="width:120px; height:120px; object-fit:cover; border-radius:8px;" />
    <div>
      <strong>Ram Vittal</strong><br/>
      Ram Vittal is a <strong>Principal ML Solutions Architect</strong> at AWS. He has over three decades of experience in architecting and building distributed, hybrid, and cloud-native applications. He is passionate about creating secure, scalable, and reliable <strong>AI/ML</strong> and <strong>big data</strong> solutions that help enterprise customers accelerate their cloud adoption and optimization journey to improve business outcomes. In his spare time, he enjoys motorcycle riding and walking his three-year-old sheep-a-doodle dog.
    </div>
  </div>

  <div style="display:flex; align-items:flex-start; gap:1rem;">
    <img src="/images/3-BlogsTranslated/3.1-Blog1/image9.png" alt="Sandeep Raveesh" style="width:120px; height:120px; object-fit:cover; border-radius:8px;" />
    <div>
      <strong>Sandeep Raveesh</strong><br/>
      Sandeep Raveesh is a <strong>GenAI Specialist Solutions Architect</strong> at AWS. He works with customers throughout their <strong>AIOps</strong> journey, including model training, <strong>Retrieval-Augmented Generation (RAG)</strong>, <strong>GenAI Agents</strong>, and scaling <strong>Generative AI</strong> use cases. He also focuses on <strong>Go-To-Market</strong> strategies to help AWS design and tailor offerings that address industry challenges in the <strong>Generative AI</strong> domain. You can find Sandeep on <a href="https://www.linkedin.com/in/sandeep-raveesh-750aa630" target="_blank">LinkedIn</a>.
    </div>
  </div>

  <div style="display:flex; align-items:flex-start; gap:1rem;">
    <img src="/images/3-BlogsTranslated/3.1-Blog1/image10.png" alt="Amit Modi" style="width:120px; height:120px; object-fit:cover; border-radius:8px;" />
    <div>
      <strong>Amit Modi</strong><br/>
      Amit Modi is the <strong>Head of Product</strong> for <strong>SageMaker AIOps and Governance</strong>, as well as <strong>Responsible AI</strong> at AWS. With over a decade of B2B experience, he has built scalable products and teams that drive innovation and deliver customer value globally.
    </div>
  </div>

  <div style="display:flex; align-items:flex-start; gap:1rem;">
    <img src="/images/3-BlogsTranslated/3.1-Blog1/image11.png" alt="Rahul Easwar" style="width:120px; height:120px; object-fit:cover; border-radius:8px;" />
    <div>
      <strong>Rahul Easwar</strong><br/>
      Rahul Easwar is a <strong>Senior Product Manager</strong> at AWS, leading <strong>Managed MLflow</strong> and <strong>Partner AI Apps</strong> within the <strong>SageMaker AIOps</strong> group. With over 15 years of experience spanning startups to enterprise technology, he leverages his entrepreneurial background and an <strong>MBA</strong> from <strong>Chicago Booth</strong> to build scalable <strong>ML</strong> platforms that simplify <strong>AI</strong> adoption for organizations worldwide. Connect with Rahul on <a href="https://www.linkedin.com/in/rahul-easwar/" target="_blank">LinkedIn</a> to learn more about his work in <strong>ML</strong> platforms and enterprise <strong>AI</strong> solutions.
    </div>
  </div>

</div>
