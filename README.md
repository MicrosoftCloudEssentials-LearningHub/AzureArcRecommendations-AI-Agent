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

| **Category**                   | **Components**| **Purpose**                                                                                                      |
|--------------------------------|--------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|
| **Core Components**            | - **Azure Arc API**<br/> - **Resource Group**<br>- **Subscription**            | - Source of recommendations (DR, security, performance, compliance) for on-prem and hybrid assets. <br/>   - Groups all resources under a single RG and subscription scope.> |
| **Data Engineering Pipeline**  | - **Function App** `Every Function App **requires** a General-Purpose v2 **Storage Account** for triggers, state, and logging.` <br>- **App Service Plan** (Consumption/Premium SKU): `The **App Service Plan** can be serverless (Consumption) or a dedicated tier (Premium/Dedicated).`<br>- **Storage Account** (General Purpose v2 for Functions runtime)<br| Hosts and scales your ingestion/enrichment logic.     |
| **AI Layer**                   | - **AI Foundry**| Classifies severity, summarizes actions, prioritizes recommendations, and suggests auto-execute vs manual review. |
| **Automation & Orchestration** | - **Logic Apps**| Executes safe actions (DR failover, patching, SQL fixes) or sends Teams/Email approvals for high-risk items.      |
| **Monitoring & Governance**    | - **Azure Monitor + Log Analytics Workspace**<br>- **Power BI** | Tracks pipeline health, AI decisions, execution outcomes; visualizes trends, compliance, and automation SLAs.    |


<!-- START BADGE -->
<div align="center">
  <img src="https://img.shields.io/badge/Total%20views-1787-limegreen" alt="Total views">
  <p>Refresh Date: 2025-08-04</p>
</div>
<!-- END BADGE -->
