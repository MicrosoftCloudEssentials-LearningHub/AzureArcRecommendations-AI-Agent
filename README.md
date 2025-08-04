# Demo: Automating Recommendations from Azure Arc with an AI Agent (full-code approach)

Costa Rica

[![GitHub](https://badgen.net/badge/icon/github?icon=github&label)](https://github.com)
[![GitHub](https://img.shields.io/badge/--181717?logo=github&logoColor=ffffff)](https://github.com/)
[brown9804](https://github.com/brown9804)

Last updated: 2025-07-30

-----------------------------

> This demo is intended to demonstrate how to automate the recommendations from Azure Arc by introducing an AI-driven agent that not only ingests and processes recommendations but also:
> - Classify & priority-rank each recommendation
> - Summarize actionable next steps in natural language
> - Decide `auto-execute` vs `human-review` paths

| **Category**                   | **Components**| **Purpose** |
| ------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ |
| **Core Components**            | **Azure Arc Advisory API**| Source of recommendations (DR, security, performance, compliance) for on-prem and hybrid assets. |
| **Data Engineering Pipeline**  | - **Azure Functions**: Fetch raw recommendations and call AI for enrichment.<br>- **Azure Data Factory (ADF)**: Orchestrate data flows and conditional logic.<br>- **Azure SQL / Data Lake**: Store raw and enriched recommendations for audit and reporting. | Handles ingestion, orchestration, and storage of all recommendations.                            |
| **AI Layer**                   | **Azure OpenAI or AI Foundry**: Classifies severity (High/Medium/Low), summarizes actions in natural language, prioritizes recommendations, and suggests auto-execution vs manual review based on risk.| Adds intelligence for decision-making, prioritization, and human-readable summaries.             |
| **Automation & Orchestration** | **Logic Apps / Azure Automation**: Execute actions (e.g., DR failover, patching, security fixes) or send Teams notifications for approval. | Automates execution of safe actions and integrates approval workflows for high-risk changes.  |
| **Monitoring & Governance**    | - **Azure Monitor + Log Analytics**: Track pipeline health, AI decisions, and execution status.<br>- **Power BI Dashboards**: Visualize trends, compliance, and automation success rates. | Provides observability, governance, and reporting for the entire solution.                       |



<!-- START BADGE -->
<div align="center">
  <img src="https://img.shields.io/badge/Total%20views-1787-limegreen" alt="Total views">
  <p>Refresh Date: 2025-08-04</p>
</div>
<!-- END BADGE -->
