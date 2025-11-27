---
title: "Week 10 Worklog"
date: "2025-09-09"
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---

### Week 10 Objectives:

- Complete the implementation of **Transaction Service** (Create, Read, Update, Delete) with a tightly controlled money flow via **Wallet Service** (balance check and deduction).
- Implement advanced Transaction features: **Advanced Filtering**, **Full-Text Search**, **Tags**, and **AI Metadata** support.
- Fully establish the **Event-Driven Architecture (EDA)** using **RabbitMQ/MassTransit** for data synchronization across services (User, Wallet, Transaction).
- Finalize **Integration Testing** and **performance optimization** for core business flows.

### Tasks to be carried out this week:

| Day | Task                                                                                                                                                                                                                                                                                                                                                                                                                                    | Start Date | Completion Date | Reference Material                                                                                                   |
| :-- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :------------------------------------------------------------------------------------------------------------------- |
| 1   | **Transaction Service Foundation & Database Setup** <br> - Initialize **Transaction Service**, set up PostgreSQL Database with necessary Entities (`Transaction`, `TransactionTag`, etc.). <br> - Configure **HTTP Client Factory** with **Polly** (Retry/Circuit Breaker) for communication with Wallet Service.                                                                                                                       | 10/11/2025 | 10/11/2025      | [Day 6 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-2/day-6.md?ref_type=heads)   |
| 2   | **Transaction CRUD APIs & Wallet Integration** <br> - Implement full **CRUD APIs** (Create, Read, Update, Delete) for transactions. <br> - Ensure **Atomic** operations in the creation flow: **Deduct Balance** via HTTP Client, then save the record to DB. <br> - Implement **Soft Delete** logic with automatic **refund** mechanism to the Jar. <br> - Implement **Basic Statistics APIs** (total expenses, daily spending).       | 11/11/2025 | 11/11/2025      | [Day 7 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-2/day-7.md?ref_type=heads)   |
| 3   | **Advanced Filtering, Tags & Budget Support** <br> - Complete the **GET /api/transactions** API with **Advanced Filtering** (by Date Range, Jar ID, Category ID, Amount Range) and **Full-Text Search** (`search=`). <br> - Implement **Transaction Tags** system (Add/Remove tags) and API to retrieve tag lists. <br> - Add a support API for **Budget Checking** for the Wallet Service.                                             | 12/11/2025 | 12/11/2025      | [Day 8 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-2/day-8.md?ref_type=heads)   |
| 4   | **Event-Driven Architecture & Service Integration** <br> - Set up **RabbitMQ** and **MassTransit** across services. <br> - Implement **Consumers** in Wallet Service to handle the `TransactionCreated` event (update Jar balance). <br> - Implement **Consumers** in Transaction Service to auto-create transactions from Wallet events (e.g., `WalletDeposited`, `WalletWithdrawn`). <br> - Ensure **Idempotency** for all Consumers. | 13/11/2025 | 13/11/2025      | [Day 9 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-2/day-9.md?ref_type=heads)   |
| 5   | **Sprint 2 Testing, Bug Fixes & Polish** <br> - Conduct **End-to-End Integration Testing** for the entire business flow (Registration -> Wallet -> Jar -> Transaction -> Budget Alerts). <br> - **Load Test** with 50 concurrent requests. <br> - **Performance Optimization** (add DB Indexes, Caching). <br> - Update **Documentation** (Swagger, Postman, README).                                                                   | 14/11/2025 | 14/11/2025      | [Day 10 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-2/day-10.md?ref_type=heads) |

### Week 10 Achievements:

- **Transaction Service Completed:**
  - Full CRUD implemented, tight money flow control, and automatic refund mechanism on deletion.
- **Advanced Feature Support:**
  - Effective **multi-dimensional filtering** and **searching** integrated.
  - Support for **Transaction Tags** and storing **AI Metadata** (JSONB).
- **Stable Event-Driven Architecture:**
  - **RabbitMQ/MassTransit** is operational, ensuring Jar balance synchronization between Transaction and Wallet Services.
  - Successfully handled events for automatic transaction creation.
- **Stable and Tested System:**
  - The entire Sprint was covered by Integration Testing and performance optimization was completed.
