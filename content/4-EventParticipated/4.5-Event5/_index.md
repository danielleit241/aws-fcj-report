---
title: "Event 5"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 4.5. </b> "
---

# Report: “AWS Cloud Mastery Series #2: From DevOps, IaC to Containers & Observability”

### Event Objectives

- **Standardize Mindset:** Deeply understand the Value Cycle and the role of DevOps in continuous and reliable software delivery.
- **Modernize Infrastructure (IaC):** Shift from manual operations (ClickOps) to managing infrastructure as code using CloudFormation, Terraform, and CDK.
- **Optimize Applications (Containerization):** Master the strategy for selecting the appropriate container platform: App Runner, ECS, or EKS.
- **Comprehensive Monitoring (Observability):** Build proactive monitoring systems to detect errors and optimize performance using CloudWatch and X-Ray.

### Speakers

- **AWS Experts & Cloud Engineers:** Shared insights on system architecture, Platform Engineering strategies, and deep-dive technical demos.

### Key Highlights

#### **1. DevOps Mindset & CI/CD Pipeline (The Foundation)**

DevOps is not just about tools; it is a culture of optimizing the flow of value from ideation to the end user.

- **The Value Cycle:** A closed-loop process from _Insights -\> Backlog -\> CI -\> Testing -\> CD_, aiming to increase delivery speed (Speed) while maintaining stability (Stability).
- **Pipeline Strategy:**
  - **Centralized CI:** A centralized system that ensures Self-service capabilities for Developers.
  - **Build Once, Deploy Anywhere:** Source code is built only once into an Artifact and used to deploy across all environments (Staging, Prod) to ensure consistency.
  - **Fail Fast:** The pipeline must immediately fail the build if it violates Code Style, Security, or Performance standards.

#### **2. Infrastructure as Code (IaC) - From ClickOps to Code**

Eliminating manual operation habits (ClickOps) that cause errors and drift, moving towards complete automation.

- **AWS CloudFormation (Native):** Uses YAML/JSON, managed via Stacks, and handles regional differences using Mappings.
- **Terraform (Multi-Cloud):** Open-source, uses HCL.

[Image of Terraform workflow diagram]
Notable for its **Plan** feature (Preview changes) and state management via State Files.

- **AWS CDK (Programming):** Write infrastructure using programming languages (Python, TS...). Uses **Constructs** (L2, L3) to quickly build complex architectures following Best Practices.
- **Drift Detection:** A critical feature to detect discrepancies between Code and Reality, helping maintain operational discipline.

#### **3. Containerization - Application Strategy**

Analyzing and selecting the right platform based on project needs:

- **Amazon ECS:** Simple, deeply integrated with AWS. Suitable for teams wanting to reduce operational overhead.
- **Amazon EKS:** Based on Kubernetes. Powerful, flexible, open standard. Designed for large systems or Hybrid-cloud.
- **AWS Fargate (Serverless Compute):** No server management (EC2) required; just focus on the application. Secure and convenient.
- **AWS App Runner:** A "ready-to-use" solution for Web Apps, automating everything from Code to URL (HTTPS).

#### **4. Observability - Monitoring & Optimization**

Closing the development lifecycle loop with deep observability:

- **Amazon CloudWatch:** Centralized collection of Metrics & Logs. Uses **Alarms** to automatically trigger corrective actions (Auto Scaling, Restart Server).
- **AWS X-Ray:** Solves the "needle in a haystack" problem in Microservices using **Distributed Tracing**, helping identify performance bottlenecks.
- **AWS Observability Best Practices:** Leveraging standard design patterns and recipes provided by AWS.

### Event Experience & Reflection

Participating in this series helped me systematize my knowledge of modern DevOps and infrastructure management strategies.

#### 1\. The Shift to "Platform Engineering"

I realized the role of DevOps is not just "deployment execution." DevOps is about architecting a **"Highway" (Pipeline & Platform)** that empowers Developers to operate independently (Self-service) quickly while adhering to safety rules.

#### 2\. Operational Discipline

Lessons on **Artifact Management** and **Drift Detection** are golden rules. In an Enterprise environment, consistency is vital. Manual changes to code-managed systems must be strictly prohibited.

#### 3\. Tool Selection Strategy

There is no "best" tool, only the "most suitable" one:

- Need stability, AWS-native: Choose **CloudFormation**.
- Need Multi-cloud: Choose **Terraform**.
- Strong programming team, need fast builds: Choose **CDK**.
- Running simple Web Apps: Use **App Runner** instead of struggling with Kubernetes.

### Conclusion

The **"AWS Cloud Modernization"** series provided a complete roadmap for the Cloud journey:

- **Mindset:** Transitioning from manual work to automation and data-driven measurement.
- **Infrastructure:** Mastering IaC for scalable and reproducible systems.
- **Operations:** Combining Containerization and Observability to ensure system stability and high performance.

#### Some photos from the event

## ![](/images/4-EventParticipated/event4-3-1.png)
