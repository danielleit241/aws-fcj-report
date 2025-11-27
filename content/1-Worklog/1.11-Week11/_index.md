---
title: "Week 11 Worklog"
date: "2025-09-09"
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---

### Week 11 Objectives:

- Completed the deployment of the **Report Service** using **CQRS** architecture to separate read/write flows, ensuring high performance for complex reports.
- Implemented advanced analytics features: **Spending Trends**, **Budget vs. Actual Comparison**, and multi-sheet **Excel Report Export**.
- Built a comprehensive **Notification Service** supporting multi-channel delivery: **Email** (via AWS SES) and **In-App** (via SignalR), allowing users to customize notification preferences.
- Established the **Period End Automation** process to handle surplus funds and prepare the Backend for **AI (OCR/Voice)** integration.

### Tasks to be carried out this week:

| Day | Task                                                                                                                                                                                                                                                                                                                                                                                                                                             | Start Date | Completion Date | Reference Material                                                                                                   |
| :-- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :------------------------------------------------------------------------------------------------------------------- |
| 1   | **Report Service Foundation & CQRS Setup** <br> - Initialized **Report Service**, setup PostgreSQL (`report_service_db`) and Read Model entities (`TransactionSummary`, `JarAnalytics`). <br> - Implemented **CQRS** pattern: Handled events from Transaction Service (`TransactionCreated`, `Updated`, `Deleted`) to update report data in real-time. <br> - Built **Basic Report APIs** to retrieve period summaries and basic jar statistics. | 17/11/2025 | 17/11/2025      | [Day 11 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-3/day-11.md?ref_type=heads) |
| 2   | **Advanced Analytics & Excel Export** <br> - Developed advanced analytics APIs: Spending trends (day/week/month), budget vs. actual comparison, and goal progress. <br> - Integrated Excel library (EPPlus/ClosedXML) to export **Multi-sheet** reports (Transaction History, Jar Analytics, Category Analytics). <br> - Configured **Caching** for reports to optimize query performance.                                                       | 18/11/2025 | 18/11/2025      | [Day 12 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-3/day-12.md?ref_type=heads) |
| 3   | **Notification Service & Email Integration** <br> - Initialized **Notification Service** connected to MongoDB (`UserPreferences`, `EmailHistory`). <br> - Integrated **AWS SES** and created email templates for critical alerts (Budget Exceeded, Low Balance, Goal Achieved). <br> - Built **Preferences** management API allowing users to choose notification frequency (Daily/Weekly) and types.                                            | 19/11/2025 | 19/11/2025      | [Day 13 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-3/day-13.md?ref_type=heads) |
| 4   | **Period End Automation & In-App Alerts** <br> - Setup **Job Scheduler** (Hangfire/Quartz) to automate the period-end process: Calculate surplus, return to main wallet, and generate summary reports. <br> - Implemented real-time **In-App** notification system via **SignalR Hub**. <br> - Built APIs to mark as read (`mark-as-read`) and manage unread badge counts.                                                                       | 20/11/2025 | 20/11/2025      | [Day 14 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-3/day-14.md?ref_type=heads) |
| 5   | **AI Service Integration (Backend Side)** <br> - Updated Transaction Entity to include AI metadata fields (`AiExtracted`, `ConfidenceScore`, `OriginalText`). <br> - Developed **Batch Transaction** API (`POST /batch`) to support processing multi-item OCR bills in a single call. <br> - Updated processing flow so Backend receives user-reviewed data from Client instead of auto-creating from AI events.                                 | 21/11/2025 | 21/11/2025      | [Day 15 Docs](https://gitlab.com/vicobi/vicobi-docs/-/blob/main/dev-plans/backend/sprint-3/day-15.md?ref_type=heads) |

### Week 11 Achievements:

- Successfully operated the reporting system with the **CQRS** pattern, providing real-time analytics data.
- **Excel Export** feature works perfectly with detailed multi-sheets (Transaction History, Jar Analysis, Category Analysis).
- **Multi-Channel Notification System:**
  - **AWS SES** integrated to send alert emails (Budget Exceeded, Low Balance).
  - **SignalR** system stable for real-time in-app notifications.
- **Automation & AI Readiness:**
  - **Period-end processing** job automated: accurately calculates surplus and returns it to the main wallet.
  - Backend completed API support for **Batch Transactions** and storage of **AI Metadata** (Confidence Score, Original Text).
