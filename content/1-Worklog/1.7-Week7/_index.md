---
title: "Week 7 Worklog"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives:

- Review and reinforce theoretical knowledge of core AWS services and architectural best practices.
- Practice AWS Cloud Practitioner exam questions daily to improve service recognition and scenario analysis.
- Strengthen understanding of AWS security, network design, storage strategies, compute options, and database availability models.
- Build the ability to confidently select correct AWS services based on business requirements, cost considerations, and operational expectations.

### Tasks to be carried out this week:

| Day | Task                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | Start Date | Completion Date | Reference Material                                                                  |
| :-- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :---------------------------------------------------------------------------------- |
| 1   | **Cloud Concepts & Well-Architected Framework** <br> - **Cloud Value:** Studied cloud benefits: CapEx to OpEx shift, Elasticity, and rapid innovation. <br> - **Performance Services:** Differentiated use cases: **CloudFront** (Content caching), **Global Accelerator** (Routing via AWS backbone), and **Route 53** (DNS Management). <br> - **Well-Architected Framework:** Reviewed 6 pillars (Operational Excellence, Security, Reliability, Performance, Cost, Sustainability) and related keywords. <br> - **Infrastructure as Code:** Understood **CloudFormation** (Automated deployment) and **AWS Service Catalog** (Service governance).                      | 20/10/2025 | 20/10/2025      | [Module Review](https://github.com/danielleit241/aws-fcj-learning/tree/main/Review) |
| 2   | **Networking, VPC Components & Hybrid Connectivity** <br> - **VPC Structure:** Reviewed CIDR, Subnet isolation, and Public/Private network planning. <br> - **Hybrid Connectivity:** Compared **AWS Site-to-Site VPN** (Internet, encrypted) vs. **AWS Direct Connect** (Dedicated, low latency). <br> - **Gateways:** Differentiated **Internet Gateway** (Inbound/Outbound for Public subnet) and **NAT Gateway** (Outbound only for Private subnet). <br> - **Security Layers:** Compared **Security Groups** (Stateful, Instance-level) and **Network ACLs** (Stateless, Subnet-level). <br> - **Routing:** Studied Route 53 policies: Failover, Weighted, Geolocation. | 21/10/2025 | 21/10/2025      | [Module Review](https://github.com/danielleit241/aws-fcj-learning/tree/main/Review) |
| 3   | **Databases, High Availability & Migration** <br> - **Amazon RDS:** Differentiated **Multi-AZ** (High Availability/Disaster Recovery) vs. **Read Replicas** (Scaling read workloads). <br> - **Security:** Learned Database encryption (KMS) and IAM Auth for MySQL/PostgreSQL. <br> - **Migration Tools:** Used **DMS** for continuous data replication and **SCT** for schema conversion between different engines. <br> - **Use Cases:** Differentiated **DynamoDB** (NoSQL, micro-second latency) and **Redshift** (Analytics, Petabyte-scale).                                                                                                                         | 22/10/2025 | 22/10/2025      | [Module Review](https://github.com/danielleit241/aws-fcj-learning/tree/main/Review) |
| 4   | **S3 Storage Architecture & Security Controls** <br> - **Storage Classes:** Selected optimal storage classes: Standard, Intelligent-Tiering (auto cost-opt), Glacier/Deep Archive (long-term). <br> - **Storage Comparison:** Differentiated S3 (Object), EFS/FSx (Shared File), and EBS (Block storage for EC2). <br> - **Access Control:** Differentiated **IAM Policies** (User-based) and **S3 Bucket Policies** (Resource-based). Configured Block Public Access. <br> - **Disaster Recovery:** Explored Cross-Region Replication (CRR) for regional data resilience.                                                                                                  | 23/10/2025 | 23/10/2025      | [Module Review](https://github.com/danielleit241/aws-fcj-learning/tree/main/Review) |
| 5   | **Compute, Pricing & Operational Efficiency** <br> - **EC2 Pricing Models:** Selected pricing models: **On-Demand** (short-term, unpredictable), **Reserved/Savings Plans** (long-term, steady), **Spot** (flexible, cheap). <br> - **Architecture:** Designed HA architecture with **Elastic Load Balancer** combined with **Auto Scaling Group**. <br> - **Serverless:** Reviewed **AWS Lambda** for event-driven tasks and operational cost optimization. <br> - **Operational Tools:** Used **EC2 Image Builder** for standardized AMIs and **Compute Optimizer** for resource recommendations.                                                                         | 24/10/2025 | 24/10/2025      | [Module Review](https://github.com/danielleit241/aws-fcj-learning/tree/main/Review) |

### Week 7 Achievements:

- Completed 2–3 AWS Cloud Practitioner practice exam sets every day with consistent improvement in performance.
- Successfully reviewed theory and real-business scenarios involving key AWS domains including Compute, Storage, Networking, Security, and Databases.
- Improved ability to differentiate AWS services with similar purposes such as:
  Elastic Load Balancing vs Route 53 vs Global Accelerator,
  S3 storage classes vs EBS vs EFS,
  Multi-AZ vs Read Replicas in RDS.
- Fully understood the theoretical foundation behind cost optimization options (On-Demand, Reserved Instances, Savings Plans, Spot Instances).
- Strengthened the theoretical knowledge of identity and access control: IAM users, roles, policies, MFA, least privilege principle.
- Enhanced comprehension of the AWS Well-Architected Framework theory and its six pillars for exam requirement questions.
