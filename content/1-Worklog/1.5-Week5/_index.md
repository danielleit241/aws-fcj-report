---
title: "Week 5 Worklog"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 Objectives:

- **Project Initiation:** Define project scope, analyze requirements, and develop a development plan for the Personal Finance Management App v2 focusing on Microservices.
- **.NET & AWS Integration:** Research and implement AWS SDK integration within a .NET Microservices architecture.
- **Networking Mastery:** Gain deep understanding of VPC architecture, network security, and hybrid connectivity (VPN, DNS).
- **Compute Fundamentals:** Master core Amazon EC2 concepts for optimal compute resource selection and management.

### Tasks to be carried out this week:

| Day | Task                                                                                                                                                                                                                                                                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                                                                           |
| :-- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :------------------------------------------------------------------------------------------- |
| 1   | **Proposal Research & AWS SDK with .NET** <br> - **Project Proposal:** Conducted group discussions to evaluate feasibility and select a Microservices-focused project topic. <br> - **Tech Stack Integration:** Researched AWS SDK integration for .NET applications. <br> - **Coding Practice:** Wrote C# code snippets for basic AWS operations: uploading data to S3, querying DynamoDB, and invoking Lambda functions.                             | 06/10/2025 | 06/10/2025      |                                                                                              |
| 2   | **Project Planning & Cost Estimation** <br> - **Requirements Analysis:** Analyzed requirements for the Personal Finance Management App v2. <br> - **Agile Planning:** Defined 20 User Stories across 8 Epics (Wallet, Transaction, AI Voice, OCR, etc.) and planned 2 Sprints. <br> - **Cost Estimation:** Selected necessary AWS services (Cognito, Transcribe, SQS...) and estimated operational costs (Free Tier vs. Paid) for budget optimization. | 07/10/2025 | 07/10/2025      | [Project Documentation](https://gitlab.com/vicobi/vicobi-ai)                                 |
| 3   | **AWS Networking: VPC & Site-to-Site VPN (Lab 03)** <br> - **VPC Architecture:** Configured Custom VPC, Subnets, Route Tables, Internet Gateway (IGW), and NAT Gateway. <br> - **Network Security:** Differentiated and configured Security Groups (Stateful) vs. Network ACLs (Stateless). <br> - **Hybrid Connectivity:** Set up AWS Site-to-Site VPN (VGW, CGW) and monitored connectivity using VPC Flow Logs and Reachability Analyzer.           | 08/10/2025 | 08/10/2025      | [Module Re-hand-on](https://github.com/danielleit241/aws-fcj-learning/tree/main/Re-hand-ons) |
| 4   | **Amazon EC2 & Compute Infrastructure Management** <br> - **EC2 Fundamentals:** Researched Instance types (T, M, R series) and selected appropriate hardware configurations (Intel/AMD/Graviton). <br> - **Image Management:** Learned about AMI (Amazon Machine Images) for standardized server environments. <br> - **Backup Strategy:** Designed data backup strategies using EBS Snapshots.                                                        | 09/10/2025 | 09/10/2025      | [Module Review](https://github.com/danielleit241/aws-fcj-learning/tree/main/Review)          |
| 5   | **Hybrid DNS with Route 53 Resolver** <br> - **Hybrid DNS Concepts:** Studied unified domain resolution models between On-premise and AWS environments. <br> - **Route 53 Resolver:** Configured Outbound Endpoints (forwarding queries from AWS) and Inbound Endpoints (receiving queries from on-premise). <br> - **Resolver Rules:** Defined DNS forwarding rules for specific domains.                                                             | 10/10/2025 | 10/10/2025      | [Module Review](https://github.com/danielleit241/aws-fcj-learning/tree/main/Review)          |

### Week 5 Achievements:

- **Project Plan Finalized:** Completed User Stories (20 stories/8 Epics), Sprint planning, and AWS infrastructure cost estimation for the FinTech project.
- **Technical PoC:** Successfully wrote C# sample code integrating AWS SDK (S3 data upload, DynamoDB retrieval).
- **Advanced Networking Config:** Successfully configured Custom VPC with Public/Private subnets and Site-to-Site VPN connectivity.
- **Hybrid DNS Architecture:** Designed and understood the hybrid DNS resolution flow between On-premise and AWS using Route 53 Resolver.
