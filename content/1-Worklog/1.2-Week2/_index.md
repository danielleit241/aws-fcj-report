---
title: "Week 2 Worklog"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives:

- Learn and practice AWS Compute services (EC2, AMI, EBS, Auto Scaling, ELB).
- Gain skills in monitoring and backup using CloudWatch and AWS Backup.
- Explore AWS Storage services: S3, Storage Gateway, FSx.
- Hands-on with deployment, scaling, and static website hosting.

### Tasks to be carried out this week:

| Day | Task                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Start Date | Completion Date | Reference Material                                                                                                                                                       |
| :-- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | **AWS Compute & EC2 Administration** <br> - **Compute Theory:** Researched Amazon EC2 architecture, Nitro Hypervisor, Instance families, and pricing strategies (Spot, Reserved, Savings Plans). <br> - **Storage for Compute:** Differentiated between EBS (Block) and Instance Store (Ephemeral); managed AMIs and Snapshots. <br> - **Hands-on Lab 04:** <br> &nbsp;&nbsp; + Provisioned EC2 infrastructure (Linux & Windows) within a VPC. <br> &nbsp;&nbsp; + Established secure connections via SSH (Linux) and RDP (Windows). <br> &nbsp;&nbsp; + Deployed a Node.js CRUD User Management application on EC2. | 14/09/2025 | 15/09/2025      | [Module 03](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-03)                                                                                       |
| 2   | **High Availability & Monitoring Operations** <br> - **Scaling & Load Balancing (Lab 06):** <br> &nbsp;&nbsp; + Configured **Auto Scaling Groups** for dynamic scalability. <br> &nbsp;&nbsp; + Deployed **Elastic Load Balancer (ELB)** for traffic distribution. <br> - **Observability (Lab 08):** Configured **Amazon CloudWatch** to collect Metrics, Logs, and set up system anomaly Alarms. <br> - **Data Protection (Lab 13):** Implemented automated backup strategies using **AWS Backup** for EC2, RDS, and EFS based on RPO/RTO targets.                                                                 | 16/09/2025 | 16/09/2025      | [Module 03](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-03)<br>[Module 06](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-06) |
| 3   | **AWS Storage Fundamentals (Amazon S3)** <br> - **Object Storage Architecture:** Studied S3 architecture, object immutability, and data durability standards. <br> - **Storage Classes:** Analyzed storage tiers (Standard, Intelligent-Tiering, Glacier) to optimize costs based on access patterns. <br> - **Security & Management:** Configured **Bucket Policies**, ACLs, Versioning, and Lifecycle Policies. <br> - **Archive Strategy:** Explored long-term archival solutions with S3 Glacier and Deep Archive.                                                                                               | 17/09/2025 | 17/09/2025      | [Module 04](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-04)                                                                                       |
| 4   | **Hybrid Cloud Storage (Storage Gateway)** <br> - **Hybrid Architecture:** Explored on-premises storage extension to Cloud via AWS Storage Gateway. <br> - **Hands-on Lab 24 (File Gateway):** <br> &nbsp;&nbsp; + Deployed an EC2 instance acting as a Gateway Appliance. <br> &nbsp;&nbsp; + Configured NFS File Shares mapping to backend S3 Buckets. <br> &nbsp;&nbsp; + Practiced mounting network drives from Cloud to local workstations.                                                                                                                                                                     | 18/09/2025 | 18/09/2025      | [Module 04](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-04)                                                                                       |
| 5   | **Managed File Systems & Static Hosting** <br> - **Amazon FSx (Lab 25):** Deployed fully managed Windows native file shares (SMB) using **Amazon FSx for Windows File Server**. <br> - **Static Website Hosting (Lab 57):** <br> &nbsp;&nbsp; + Hosted a static website directly on an S3 Bucket. <br> &nbsp;&nbsp; + Optimized performance and security via **Amazon CloudFront** (CDN) and OAI (Origin Access Identity). <br> &nbsp;&nbsp; + Configured DNS and Public Access settings.                                                                                                                            | 19/09/2025 | 19/09/2025      | [Module 04](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-04)                                                                                       |

### Week 2 Achievements:

1. **Compute & Deployment**

   - Gained strong understanding of Amazon EC2 concepts, architecture, and related components (AMI, Snapshot, Key Pair, EBS).
   - Successfully launched and managed both Linux and Windows EC2 instances.
   - Practiced deployment of a real-world Node.js CRUD application on EC2 instances.
   - Learned automation techniques using User Data, Meta Data, and AWS Systems Manager.

2. **Scalability & High Availability**

   - Implemented **EC2 Auto Scaling Group** to automatically adjust capacity based on demand.
   - Configured **Elastic Load Balancer (ELB)** to distribute traffic across multiple EC2 instances.
   - Integrated Auto Scaling with Load Balancing for high availability and cost optimization.

3. **Monitoring & Observability**

   - Explored **Amazon CloudWatch** for infrastructure and application monitoring.
   - Created custom metrics, dashboards, and alarms for real-time system health tracking.
   - Centralized log management using CloudWatch Logs with retention and anomaly detection.
   - Practiced automated monitoring using CloudFormation stacks.

4. **Data Protection & Backup**

   - Learned to design **AWS Backup Plans** for multiple services (EBS, RDS, DynamoDB, EFS).
   - Implemented recovery objectives (RTO/RPO) for disaster recovery strategies.
   - Configured **SNS notifications** for backup success, failure, and recovery events.

5. **Storage & Data Management**
   - Understood **Amazon S3** as an object storage service, with lifecycle policies and storage classes.
   - Practiced S3 features: versioning, access control (ACL, Bucket Policy), and CORS.
   - Configured **S3 Static Website Hosting** and tested public accessibility.
   - Implemented **CloudFront distribution** for faster content delivery and secured access via OAI.
   - Learned **Amazon FSx for Windows File Server**: architecture, integration with Windows, and managed file storage service.
