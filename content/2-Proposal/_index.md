---
title: "Proposal"
date: "2025-09-09"
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Personal Finance Management App

### 1. Executive Summary

The Personal Finance Management App project aims to provide an intelligent, modern, and highly automated personal financial management platform. The application allows users to record income and expenses, create and manage multiple money jars for different purposes, create spending plans, receive smart alerts, and generate visual analytical reports.

The application is built with a microservices architecture on .NET Aspire and FastAPI platform, deployed on AWS Cloud, ensuring flexibility, scalability, and data security. The development process follows the Agile/Scrum model (2 weeks/sprint), with MVP completion time within 2 months.

### 2. Problem Statement

### What’s the Problem?

Current weather stations require manual data collection, becoming unmanageable with multiple units. There is no centralized system for real-time data or analytics, and third-party platforms are costly and overly complex.

**Solution**  
The solution uses AWS Cloud combined with microservices architecture to build an automated personal financial management platform, integrating AI in voice processing and bill recognition. The system is deployed on AWS ECS Fargate for backend services (.NET Aspire), FastAPI for AI processing, and Next.js for frontend. Compared to popular financial platforms like Money Lover or Misa Money Keeper, this application focuses on complete automation of financial data entry through detailed Vietnamese AI voice-to-text and bill scanning, helping reduce manual operations and errors. The system is suitable for individual users and small groups, and can be expanded when needed for enterprise scale or digital banking applications.

**Benefits and Return on Investment (ROI)**  
The solution brings many practical benefits both technically and in business value:

- Data Entry Automation: Reduces over 70% manual operations through AI voice and bill recognition.
- Increased Accuracy: Limits input errors, ensures financial data integrity (>90% accuracy).
- Improved User Performance: Record and categorize transactions in just seconds, optimizing user experience.
- Cost Savings: Low infrastructure costs thanks to AWS Free Tier utilization until 2026; only estimated ~$60 USD/month for AWS and ~$30 USD for AI compute.
- Fast ROI: Expected payback in 6–12 months, thanks to time savings in data entry and increased operational efficiency.
- Scalability & Integration: Microservices architecture on AWS allows easy addition of features (mobile app, advanced analytics, banking integration).

### 3. Solution Architecture

The system is built on a **microservices architecture** hosted on **AWS Cloud**, combining serverless components, containerized services, and managed databases for scalability and performance.

![IoT Weather Sofware Architecture](/images/2-Proposal/development_architecture.drawio.png)

Users access the **Next.js** web application through **Amazon CloudFront**, with static content stored in **Amazon S3**.  
Authentication is handled by **Amazon Cognito**, which issues access tokens for secure communication between the frontend and the backend through **Amazon API Gateway**.

The **API Gateway** routes requests to the **Application Load Balancer (ALB)**, which forwards traffic to **Amazon ECS (Fargate)** containers running backend services:

- **Aspire Service (.NET Aspire)**: Handles core business logic such as user, transaction, and budget management.
- **FastAPI Service (AI Service)**: Processes invoices, voice inputs, and AI-based recommendations.

When a user uploads an invoice or voice file, it is temporarily stored in **Amazon S3**.  
The **AI Service** fetches this file, processes it, and returns results to the **Aspire Service**, while additional metadata is stored in **MongoDB Cloud (Free Tier)**.  
Structured business data (users, transactions, budgets) is stored in **Amazon Aurora PostgreSQL (RDS)**.

All logs, metrics, and alerts from ECS, API Gateway, and ALB are centralized in **Amazon CloudWatch**.  
Container images are stored in **Amazon ECR**, and deployments are automated via **GitHub Actions**.

![IoT Weather Platform Architecture](/images/2-Proposal/cloud_architecture.drawio.png)

_AWS Services Used_

- _Amazon CloudFront_: Global content delivery and frontend acceleration.
- _Amazon S3_: Storage for static website assets, invoices, and voice files.
- _Amazon Cognito_: Authentication and user management.
- _Amazon API Gateway_: Entry point routing requests from frontend to backend.
- _Application Load Balancer (ALB)_: Distributes traffic among backend containers.
- _Amazon ECS (Fargate)_: Runs containerized microservices for .NET Aspire and FastAPI.
- _Amazon ECR_: Stores container images for ECS deployment.
- _Amazon Aurora PostgreSQL (RDS)_: Stores structured business data.
- _MongoDB Cloud (Free 512MB)_: Stores AI and notification metadata.
- _Amazon CloudWatch_: Centralized logging, metrics, and monitoring.
- _Amazon Route 53_: DNS and domain management.
- _GitHub Actions_: Automates CI/CD pipelines for build and deployment.

---

### 4. Technical Deployment

_Implementation Phases_  
The project is divided into three main phases, focusing on the design, optimization, and deployment of the personal finance management platform on AWS:

1. _Research and Architecture Design_: Study microservices models and design the overall architecture on AWS (including CloudFront, ECS Fargate, RDS, S3, API Gateway, Cognito) — (January).
2. _Cost Estimation and Optimization_: Use AWS Pricing Calculator to estimate cost and optimize service selection for affordability and ease of deployment — (January–February).
3. _Development, Testing, and Deployment_: Build frontend (Next.js), backend (.NET Aspire), and AI service (FastAPI); perform microservice integration testing; deploy the system to AWS via ECS Fargate; and set up monitoring with CloudWatch — (February–March).

_Technical Requirements_

- _Frontend_:  
  The **Next.js** web app is hosted on **Amazon S3** and distributed via **CloudFront**, communicating with backend APIs through **API Gateway**.  
  User authentication and token issuance are handled by **Amazon Cognito**.

- _Backend_:  
  Built with **.NET Aspire**, deployed on **ECS Fargate**.  
  Services handle user, transaction, and budget management, connecting to **RDS PostgreSQL** and **S3**.  
  Container images are stored in **ECR** and deployed automatically using **GitHub Actions**.

- _AI Service_:  
  Developed with **FastAPI**, it processes invoice images and voice inputs by reading files from **S3**.  
  Results are stored in **MongoDB Cloud (Free Tier)** and returned to the Aspire Service via API or message queue.

- _Database_:  
  **Amazon Aurora PostgreSQL** stores structured data (users, transactions, budgets).  
  **MongoDB Cloud** stores AI metadata, notifications, and unstructured data.  
  Aurora runs in a private subnet to ensure database security and restricts access to ECS only.

- _Cloud Infrastructure_:  
  Uses **Amazon VPC** (multi-AZ), **Application Load Balancer**, and **CloudWatch** for monitoring.  
  Container images are hosted in **ECR** and deployed to **ECS Fargate**.  
  **GitHub Actions** provides automated CI/CD workflows for build and deployment.

- _Security_:  
  User access is managed by **Amazon Cognito**.  
  **IAM Roles** are used for ECS, S3, and CloudWatch to enforce least-privilege access.  
  **Security Groups** are configured between ECS, ALB, and RDS for network security.

### 5. Timeline & Milestones

- **Pre-internship (Month 0)**: 1 month for planning.
- **Internship (Month 1–3)**:
  - Month 1: Learn AWS and upgrade programming skills.
  - Month 2: Design and adjust architecture.
  - Month 3: Implement, test, and deploy.
- **Post-deployment**: Research mobile development and deploy after month 4.

### 6. Budget Estimation

<!-- You can view costs on [AWS Pricing Calculator](https://calculator.aws/#/estimate?id=621f38b12a1ef026842ba2ddfe46ff936ed4ab01)
Or download the [budget estimation file](../attachments/budget_estimation.pdf). -->

**_Within AWS Free Tier (First 12 Months)_**

- _Amazon ECS (Fargate)_: 0.00 USD/month (≤ 50 GB-hr CPU, 200 GB-hr RAM).
- _Amazon API Gateway_: 0.00 USD/month (≤ 1 million requests).
- _Amazon RDS (PostgreSQL)_: 0.00 USD/month (db.t3.micro 750 hours, 20 GB storage).
- _Amazon S3_: 0.00 USD/month (≤ 5 GB for invoice and voice files).
- _Amazon SQS_: 0.00 USD/month (≤ 1 million messages).
- _Amazon CloudWatch_: 0.00 USD/month (≤ 10 custom metrics + 5 GB logs).
- _Amazon Cognito_: 0.00 USD/month (≤ 50,000 active users).
- _Amazon ECR_: 0.00 USD/month (≤ 500 MB image storage).
- _Amazon Route 53_: 1.00 USD/month (1 domain).
- _MongoDB Atlas (Free Tier)_: 0.00 USD/month (M0 Sandbox – 512 MB RAM, Shared Cluster).
- _GitHub Actions_: 0.00 USD/month (≤ 2,000 free build minutes).

_Total_: **≈ 1.00 USD/month**, equivalent to **≈ 12.00 USD/year** during the Free Tier period.

**_After Free Tier (Estimated for 50–100 Users)_**

- _Amazon ECS (Fargate)_: 18.00 USD/month (3 small containers running 24/7).
- _Amazon API Gateway_: 3.50 USD/month (≈ 2–3 million requests).
- _Amazon RDS (PostgreSQL)_: 12.00 USD/month (db.t3.micro, 20 GB).
- _Amazon S3_: 2.50 USD/month (50 GB storage, 10,000 requests).
- _Amazon SQS / RabbitMQ_: 1.00 USD/month (a few million messages).
- _Amazon CloudWatch_: 3.50 USD/month (basic logs and metrics).
- _Amazon Cognito_: 0.50 USD/month (50–100 active users).
- _Amazon ECR_: 0.50 USD/month (1 GB container image storage).
- _MongoDB Atlas (M2 Shared Cluster)_: 9.00 USD/month (2 GB RAM).
- _Amazon Route 53_: 1.00 USD/month (1 domain).
- _GitHub Actions_: 2.00 USD/month (beyond free limit).

_Total_: **≈ 53.50 USD/month**, equivalent to **≈ 642.00 USD/year** after the Free Tier expires.

### 7. Risk Assessment

**Risk Matrix**

- AI model misrecognition (voice/bill): Medium impact, medium probability.
- AWS connection loss or regional service errors: High impact, low probability.
- Exceeding AWS usage budget: Medium impact, low probability.
- Data synchronization errors between microservices: Medium impact, medium probability.
- User information leakage (Cognito/Database): High impact, low probability.

**Mitigation Strategies**

- **AI**: Improve OCR and voice-to-text models through additional training, regular testing with real data.
- **AWS Region**: Set up multi-AZ deployment and regular RDS database backup.
- **Cost**: Configure **AWS Budget Alert** and optimize ECS, S3 based on actual usage.
- **Microservices**: Use **SQS/RabbitMQ** to ensure asynchronous processing and retry on errors.
- **Security**: Data encryption (AES-256, HTTPS), IAM control following "Least Privilege" principle.

**Contingency Plans**

- If AWS encounters issues: Temporarily switch to local transaction data storage and sync after recovery.
- Restore infrastructure using **AWS CloudFormation** or pre-saved **IaC (Infrastructure as Code)**.
- Keep regular database copies (RDS snapshots) for data loss recovery.

### 8. Expected Outcomes

#### Technical Improvements:

Real-time data and analytics replace manual processes.  
Scalable to 10-15 stations.

#### Long-term Value

1-year data foundation for AI research.  
Reusable for future projects.
