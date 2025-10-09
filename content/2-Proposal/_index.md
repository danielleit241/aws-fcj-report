---
title: "Pro### 2. Problem Statement

**Current Problem**  
The market already has many financial management applications, however most still require users to manually input data — a time-consuming task prone to errors that causes users to quickly give up. Existing applications only focus on expense statistics but don't truly help users automate the personal financial management process."
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

The system operates on a microservices model on AWS Cloud. Users interact through a web interface (Next.js) that sends requests to the API Gateway (.NET Aspire). The Gateway routes to appropriate services like User, Transaction, Budget, or AI Service (FastAPI). When users upload bills or record voice, data is temporarily stored on S3, AI processes it and returns results to the Transaction Service to create or suggest transactions. All data is stored in RDS PostgreSQL, events are transmitted via RabbitMQ/SQS, and the system is monitored through CloudWatch.

![IoT Weather Station Architecture](/images/2-Proposal/edge_architecture.jpeg)

![IoT Weather Platform Architecture](/images/2-Proposal/platform_architecture.jpeg)

**AWS Services Used**

- **Amazon ECS (Fargate)**: Runs .NET Aspire microservices and FastAPI without server management.
- **Amazon API Gateway**: Routes requests from frontend to backend, combined with Cognito authentication.
- **Amazon RDS (PostgreSQL)**: Stores user data, transactions, and budgets.
- **Amazon S3**: Stores bill files, voice recordings, and financial reports.
- **Amazon SQS / RabbitMQ**: Transmits events between services (event-driven).
- **Amazon CloudWatch**: Monitors logs, performance, and system alerts.
- **Amazon Cognito**: Manages users and security authentication.
- **Amazon Route 53**: Manages domain names and DNS.
- **GitHub Actions**: Automates CI/CD deployment.

### 4. Technical Implementation

**Implementation Phases**
The project is divided into 3 main phases, focusing on building, optimizing, and deploying the personal financial management platform on AWS:

1. **Research and Architecture Design**: Research microservices models and design overall architecture on AWS (including ECS Fargate, RDS, S3, API Gateway, Cognito) — (Month 1).
2. **Cost Calculation and Solution Adjustment**: Use AWS Pricing Calculator to estimate costs, optimize service selection to ensure low cost and easy deployment for beginners — (Month 1–2).
3. **Development, Testing, Deployment**: Build frontend (Next.js), backend (.NET Aspire), and AI service (FastAPI); test microservices integration, then deploy entire system to AWS using ECS Fargate and set up monitoring via CloudWatch — (Month 2–3).

**Technical Requirements**

- **Frontend**: **Next.js** web application hosted on **AWS Amplify** or ECS Fargate, communicating with backend through **API Gateway**.
- **Backend**: Built with **.NET Aspire**, deployed on **ECS Fargate**, communicating with **RDS PostgreSQL** and **S3**.
- **AI Service**: Built with **FastAPI**, processes bills and voice, connects to S3 and returns results via message queue (RabbitMQ or SQS).
- **Database**: **Amazon RDS (PostgreSQL)** stores transactions, users, and budgets.
- **Cloud Infrastructure**: Uses **AWS VPC** (multi-AZ), **Load Balancer**, **CloudWatch** for monitoring, and **CodePipeline / GitHub Actions** for CI/CD.
- **Security**: Access control management with **Amazon Cognito** and **IAM Roles** for services.

### 5. Timeline & Milestones

- **Pre-internship (Month 0)**: 1 month for planning.
- **Internship (Month 1–3)**:
  - Month 1: Learn AWS and upgrade programming skills.
  - Month 2: Design and adjust architecture.
  - Month 3: Implement, test, and deploy.
- **Post-deployment**: Research mobile development and deploy after month 4.

### 6. Budget Estimation

You can view costs on [AWS Pricing Calculator](https://calculator.aws/#/estimate?id=621f38b12a1ef026842ba2ddfe46ff936ed4ab01)  
Or download the [budget estimation file](../attachments/budget_estimation.pdf).

### **Infrastructure Costs**

**Within Free Tier (First 12 months)**

- **Amazon ECS (Fargate)**: $0.00/month (≤ 50 GB-hr CPU, 200 GB-hr RAM).
- **Amazon API Gateway**: $0.00/month (≤ 1 million requests).
- **Amazon RDS (PostgreSQL)**: $0.00/month (db.t3.micro 750 hours, 20 GB storage).
- **Amazon S3**: $0.00/month (≤ 5 GB storage for bills and voice files).
- **Amazon SQS**: $0.00/month (≤ 1 million messages).
- **Amazon CloudWatch**: $0.00/month (≤ 10 custom metrics + 5 GB logs).
- **Amazon Cognito**: $0.00/month (≤ 50,000 active users).
- **Amazon Route 53**: $1.00/month (1 domain).
- **GitHub Actions**: $0.00/month (≤ 2,000 free build minutes).

**Total**: **≈ $1.00/month**, equivalent to **$12.00/year** during Free Tier period.

**After Free Tier expires (with 50–100 users)**

- **Amazon ECS (Fargate)**: $18.00/month (3 small containers, running 24/7).
- **Amazon API Gateway**: $3.50/month (≈ 2–3 million requests).
- **Amazon RDS (PostgreSQL)**: $12.00/month (db.t3.micro, 20 GB).
- **Amazon S3**: $2.50/month (50 GB, 10,000 requests).
- **Amazon SQS / RabbitMQ**: $1.00/month (several million messages).
- **Amazon CloudWatch**: $3.50/month (basic logs + metrics).
- **Amazon Cognito**: $0.50/month (50–100 active users).
- **Amazon Route 53**: $1.00/month (1 domain).
- **GitHub Actions**: $2.00/month (exceeding free limits).

**Total**: **≈ $44.00/month**, equivalent to **$528.00/year** after Free Tier expires.

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
