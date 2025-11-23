---
title: "Week 10 Worklog"
date: "2025-09-09"
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---

### Week 10 Objectives:

- Complete the setup of the **Microservice architecture** using **.NET Aspire** and build all core **Shared Libraries**.
- Fully implement the **User Service** with **AWS Cognito** authentication integration and **automatic user/profile creation** logic.
- Fully implement the **Wallet Service** with balance management logic, **Money Jar** management, **Goals Tracking**, and **Jar Expiry Processing** mechanisms.
- Set up the **API Gateway**, configure **Polly**, and finalize **Integration Testing** for the End-to-End flow (User-Wallet).

### Tasks to be carried out this week:

| Day       | Task                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Start Date | Completion Date | Reference Material                                                                                                 |
| :-------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :----------------------------------------------------------------------------------------------------------------- |
| **Day 1** | **Microservice Architecture & Shared Libraries Setup** <br> - Initialize the **.NET Aspire** solution and structure **6 Microservices** (User, Wallet, Transaction, Report, Notification, AI Integration Service). <br> - Configure Service Discovery and **Docker Compose** for the local development environment. <br> - Build core **Shared Libraries**: `Common.DTOs` (with `ApiResponse<T>`), `Common.Authentication` (JWT), `Common.Messaging` (**MassTransit/RabbitMQ**), `Common.Repositories` (UoW Pattern), and `Common.Middlewares` (Rate Limiting, Correlation ID).                                         | 12/11/2025 | 12/11/2025      | [Day 1 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-1/day-1.md?ref_type=heads) |
| **Day 2** | **Implement User Service & Authentication Integration** <br> - Set up **PostgreSQL Database** (`user_service_db`) and design the `User` Entity (using `Guid.CreateVersion7()`, Soft Delete Filter). <br> - Integrate **AWS Cognito** authentication (**JWT Bearer Authentication**) and create middleware to extract `CognitoSub`. <br> - Implement **automatic user record creation** logic upon first login. <br> - Implement Core APIs: `GET /api/users/me` (Get/Create profile), `PUT /api/users/me` (Update), and `POST /api/users/complete-profile`.                                                              | 13/11/2025 | 13/11/2025      | [Day 2 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-1/day-2.md?ref_type=heads) |
| **Day 3** | **Wallet Service - Part 1: Wallet Management & Allocation Logic** <br> - Set up **PostgreSQL Database** (`wallet_service_db`) and design `Wallet`, `MoneyJar`, `BudgetPeriod` Entities. <br> - Implement **Message Consumer** to **automatically create Wallet** upon receiving the `UserCreated` event, and simultaneously create the default **"Income" jar**. <br> - Implement core Wallet APIs: **Deposit**, **Withdraw** (from Available Balance only), **Reconcile** (Synchronize total balance), and **Soft Delete/Archive Wallet**. <br> - Implement basic **Money Jar CRUD APIs**.                             | 14/11/2025 | 14/11/2025      | [Day 3 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-1/day-3.md?ref_type=heads) |
| **Day 4** | **Wallet Service - Part 2: Money Jar, Goals & Budget** <br> - Complete **CRUD** for Money Jar, including logic to recalculate `AvailableBalance` upon updating `AllocatedAmount`. <br> - Integrate **Goals Tracking** (calculate `ProgressPercent`) and `GoalAchieved` event publishing logic. <br> - Implement **Jar Operations**: **Deposit**, **Withdraw**, **Transfer** between jars, and **Reconcile Jar Balance**. <br> - Implement **Budget Threshold & Over-Budget Logic** (publish warning events) and **Jar Expiry Processing Service** (handle Income Jar auto-reset, Expense Jar Grace Period/Auto-Return). | 15/11/2025 | 15/11/2025      | [Day 4 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-1/day-4.md?ref_type=heads) |
| **Day 5** | **End-to-End Integration & Testing** <br> - Set up **API Gateway** (Routing, CORS, Rate Limiting). <br> - Configure **Service-to-Service** communication with **HTTP Client Factory** and **Polly** (Retry Policy, Circuit Breaker). <br> - Perform **Integration Testing** for the End-to-End flow: New User Onboarding, Jar Creation, Wallet/Jar Operations (Deposit/Withdraw/Transfer/Reconcile), and **Goal Achievement**. <br> - Test **Security** (JWT Expiration, Authorization) and **Concurrency** (Balance Updates).                                                                                          | 16/11/2025 | 16/11/2025      | [Day 5 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-1/day-5.md?ref_type=heads) |

### Week 10 Achievements:

- **Microservice Platform Architecture Established:**
  - Used **.NET Aspire** to shape the Microservice architecture for 6 services.
  - Completed the core set of **Shared Libraries**, including MassTransit/RabbitMQ configuration.
- **User Service Completed:**
  - Successfully integrated **AWS Cognito** for the JWT authentication mechanism.
  - Implemented **automatic user profile creation** logic and the profile completion API.
- **Wallet Service Completed:**
  - Implemented three-component balance management logic: **TotalBalance, AllocatedBalance, AvailableBalance**.
  - Completed **Money Jar Management** with **Goals Tracking** (Target, Progress) and `GoalAchieved` event publishing.
- **Complex Business Logic Implemented:**
  - Finalized operations such as **Wallet/Jar Reconciliation** (Balance Synchronization) and **Jar Expiry Processing** (allowing Income Jar auto-reset and Expense Jar with a grace period).
- **Stable and Integrated System:**
  - **API Gateway** and the fault tolerance mechanism **Polly** (Retry, Circuit Breaker) have been configured.
  - The entire main business flow has been successfully **Integration Tested** (from Cognito -> User Service -> Wallet Service).
