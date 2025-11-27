---
title: "Week 1 Worklog"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Week 1 Objectives:

- Understand the fundamentals of **cloud computing** and AWS global infrastructure.
- Learn how to manage AWS services using **Management Console, CLI, and SDK**.
- Explore **AWS security, IAM, and cost management** through practical labs.
- Build foundational knowledge of **VPC networking and connectivity** (Subnets, Route Tables, IGW, NAT, Peering, Transit Gateway).
- Gain hands-on experience by performing **AWS labs** to reinforce theoretical knowledge with practical skills.

### Tasks to be carried out this week:

| Day | Task                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Start Date | Completion Date | Reference Material                                                                 |
| :-- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :--------------------------------------------------------------------------------- |
| 1   | **AWS Cloud Foundation & IAM Security** <br> - **Cloud Essentials:** Researched core cloud computing concepts and AWS Global Infrastructure (Regions, AZs, Edge Locations). <br> - **Account Management:** Explored AWS Pricing models and Support Plans. <br> - **Hands-on Lab:** Secured Root User, configured **IAM** (Users, Groups, MFA), and set up cost alerts using **AWS Budgets**.                                                                                                                            | 08/09/2025 | 08/09/2025      | [Module 01](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-01) |
| 2   | **Networking Fundamentals (VPC Architecture)** <br> - **VPC Design:** Analyzed Amazon VPC architecture, IP addressing (CIDR Blocks), and Subnet segmentation (Public/Private). <br> - **Routing Components:** Studied routing mechanisms via Route Tables, Internet Gateway (IGW), and NAT Gateway. <br> - **Network Interfaces:** Researched Elastic IP (EIP), ENI, and VPC Endpoints (Gateway & Interface) for optimized internal connectivity.                                                                       | 09/09/2025 | 09/09/2025      | [Module 02](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-02) |
| 3   | **Network Security & Advanced Connectivity** <br> - **Network Security:** Compared Instance-level security (**Security Groups**) vs. Subnet-level security (**Network ACLs**); monitored traffic with **VPC Flow Logs**. <br> - **Inter-Connectivity:** Explored multi-VPC connection models (**VPC Peering**, **Transit Gateway**) and hybrid connectivity (**VPN**, **Direct Connect**). <br> - **Load Balancing:** Studied application traffic distribution using **Elastic Load Balancing (ELB)** (ALB, NLB, GWLB). | 10/09/2025 | 10/09/2025      | [Module 02](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-02) |
| 4   | **Hands-on Lab: VPC Infrastructure Implementation** <br> - **Infrastructure Setup:** Deployed a standard VPC model: Created Subnets, IGW, Route Tables, and Security Groups. <br> - **Compute & Connectivity:** Launched EC2 Instances and configured **NAT Gateway** for secure Private Subnet internet access. <br> - **Operations:** Practiced resource monitoring via **CloudWatch** and secure session management using **SSM Session Manager**.                                                                   | 11/09/2025 | 11/09/2025      | [Module 02](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-02) |
| 5   | **Hands-on Lab: Advanced Networking Scenarios** <br> - **Secure Access:** Practiced Port Forwarding techniques and centralized log management with Session Manager. <br> - **VPC Peering:** Configured cross-Region/Account VPC peering connections and updated route tables. <br> - **Transit Gateway:** Implemented a centralized Hub-and-Spoke network model to simplify routing. <br> - **Hybrid DNS:** Configured **Route 53 Resolver** (Inbound/Outbound Endpoints) for hybrid domain resolution.                 | 12/09/2025 | 12/09/2025      | [Module 02](https://github.com/danielleit241/aws-fcj-learning/tree/main/Module-02) |

### Week 1 Achievements:

- **Gained solid knowledge of AWS and Cloud Computing**

  - Understood cloud computing concepts, benefits, and the cloud adoption journey.
  - Learned AWS global infrastructure (Regions, AZs, Edge Locations, Data Centers).

- **Hands-on with AWS management tools**

  - Practiced with AWS Management Console, AWS CLI, and AWS SDK.
  - Created and managed IAM Users/Groups, enabled MFA, and configured Access Keys.

- **Cost management & support**

  - Created and configured different AWS Budgets.
  - Learned AWS Support Plans and practiced opening support cases.

- **AWS Networking & Security**

  - Built and configured VPC, Subnet, Route Table, Internet Gateway, NAT Gateway.
  - Implemented Security Groups, Network ACLs, and VPC Flow Logs.
  - Understood VPC Peering vs. Transit Gateway, and hybrid connectivity (VPN, Direct Connect).

- **System management on AWS**

  - Managed EC2 instances with **Session Manager** instead of SSH.
  - Practiced Port Forwarding and Session Logs.
  - Enabled **CloudWatch Monitoring & Alerts** for EC2.

- **Advanced solutions**
  - Set up **VPC Peering** and **Transit Gateway** for multi-VPC connectivity.
  - Configured **Hybrid DNS** with Route 53 Resolver (Inbound/Outbound Endpoints).
  - Practiced **Elastic Load Balancer** (ALB, NLB, CLB, GWLB).

---

👉 **Outcome:** After Week 1, I have built a strong foundation in AWS fundamentals and intermediate networking concepts, while successfully completing multiple **hands-on labs directly on AWS** to strengthen my practical skills.
