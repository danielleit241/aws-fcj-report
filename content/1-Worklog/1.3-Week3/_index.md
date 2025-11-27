---
title: "Week 3 Worklog"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives:

- Understand AWS security philosophy (“Security is Job Zero”) and the **Shared Responsibility Model**.
- Gain proficiency with **Identity & Access Management**: IAM Users, Groups, Roles, Policies, Permission Boundaries, Organizations, Identity Center, Cognito.
- Apply **AWS KMS** for data encryption, integrate with CloudTrail, and analyze logs using Athena.
- Learn AWS **Database Services**: RDS, Aurora, Redshift, ElastiCache and core concepts of SQL, NoSQL, OLTP, OLAP.
- Deploy **Amazon RDS** with Multi-AZ, subnet groups, backup and restore for high availability and resilience.

### Tasks to be carried out this week:

| Day | Task                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Start Date | Completion Date | Reference Material                                                                 |
| :-- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :--------------------------------------------------------------------------------- |
| 1   | **AWS Security & Identity Management** <br> - **Security Fundamentals:** Studied the Shared Responsibility Model and the "Security is Job Zero" philosophy. <br> - **Identity Management:** Deep dived into **IAM** (Users, Groups, Roles, Policies) and centralized access management via **AWS Organizations** & **Identity Center**. <br> - **App Security:** Explored **Amazon Cognito** (User/Identity Pools) for application authentication. <br> - **Compliance:** Researched data encryption using **AWS KMS** and compliance monitoring with **Security Hub**. | 22/09/2025 | 22/09/2025      | [Module 05](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-05) |
| 2   | **Hands-on Lab: IAM Policy & Role Configuration** <br> - **IAM Basics (Lab 02):** Practiced creating IAM Users/Groups and applying the **Least Privilege** principle. <br> - **Advanced Roles (Lab 44):** Configured **IAM Roles** with advanced conditions (IP, Date/Time) for granular access control. <br> - **Instance Profile (Lab 48):** Attached IAM Roles to EC2 Instances to enable secure S3 access without hardcoding credentials in the application.                                                                                                        | 23/09/2025 | 23/09/2025      | [Module 05](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-05) |
| 3   | **Hands-on Lab: Advanced Security Implementation** <br> - **Federated Identity (Lab 18):** Configured **Amazon Cognito** for identity federation and user authentication. <br> - **Permission Boundaries (Lab 30):** Implemented Permissions Boundaries to limit the maximum permissions available to IAM entities. <br> - **Data Encryption (Lab 33):** Managed Customer Master Keys (CMKs) with **AWS KMS** and integrated **CloudTrail** for auditing key usage.                                                                                                     | 24/09/2025 | 24/09/2025      | [Module 05](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-05) |
| 4   | **AWS Database Services Fundamentals** <br> - **Database Concepts:** Differentiated between Relational (RDBMS) vs Non-Relational (NoSQL) databases, and OLTP vs OLAP workloads. <br> - **Managed RDBMS:** Analyzed **Amazon RDS** (Multi-AZ, Read Replicas) and **Amazon Aurora** (Cloud-native architecture). <br> - **Specialized DBs:** Explored **Amazon Redshift** for Data Warehousing and **Amazon ElastiCache** for in-memory caching strategies.                                                                                                               | 25/09/2025 | 25/09/2025      | [Module 06](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-06) |
| 5   | **Hands-on Lab: Deploying & Managing Amazon RDS** <br> - **Infrastructure Setup:** Configured VPC, DB Subnet Groups, and isolated Security Groups for the database layer (Lab 05). <br> - **Deployment:** Provisioned a Multi-AZ **Amazon RDS** instance and established secure connectivity from an EC2 Web Server. <br> - **Operations:** Practiced Backup & Restore procedures, managed Snapshots, and executed Point-in-Time Recovery (PITR).                                                                                                                       | 26/09/2025 | 26/09/2025      | [Module 06](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-06) |

### Week 3 Achievements:

- **Security Services:**

  - Applied Shared Responsibility Model in practice.
  - Managed IAM with Users, Groups, Roles, Policies, Conditions, and Permission Boundaries.
  - Used IAM Role with EC2 to remove security risks of hardcoded Access Keys.
  - Implemented **Identity Federation** with Cognito (Google, Facebook, SAML).
  - Centralized multi-account management with AWS Organizations and Identity Center.

- **Encryption & Monitoring:**

  - Created and managed **KMS CMKs** for encryption.
  - Encrypted S3 data with KMS.
  - Logged and monitored key activities with CloudTrail, analyzed with Athena.

- **Database Services:**

  - Learned differences between **RDBMS vs NoSQL**, OLTP vs OLAP.
  - Deployed **Amazon RDS** with Multi-AZ, subnet groups, automated backups, snapshots, and point-in-time recovery.
  - Studied **Aurora** (Backtrack, Global DB, Cloning), **Redshift** (MPP, Spectrum), and **ElastiCache** (Redis, Memcached).

- **Hands-on Practice:**
  - Completed labs: IAM Basics, IAM Roles & Conditions, IAM Roles for Applications, Cognito Federation, IAM Permission Boundaries, KMS Encryption, RDS Deployment.
  - Built a secure RDS environment with backup and recovery strategies.
