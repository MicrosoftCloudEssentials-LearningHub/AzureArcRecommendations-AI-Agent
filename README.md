# Demo: Automating Recommendations from Azure Arc with an AI Agent (full-code approach)

Costa Rica

[![GitHub](https://badgen.net/badge/icon/github?icon=github&label)](https://github.com)
[![GitHub](https://img.shields.io/badge/--181717?logo=github&logoColor=ffffff)](https://github.com/)
[brown9804](https://github.com/brown9804)

Last updated: 2025-07-30

-----------------------------

`Arc API → Function App → AI Foundry → Logic Apps → Monitoring`

> - Function App is the central orchestrator for ingestion and enrichment.
> - AI Foundry provides decision intelligence.
> - Logic Apps executes or escalates actions.
> - Monitoring ensures observability and compliance.

> [!IMPORTANT]
> Disclaimer: This repository contains example of how to automate the recommendations from Azure Arc by introducing an AI-driven agent that not only ingests and processes recommendations but also:
>   - Classify & priority-rank each recommendation
>   - Summarize actionable next steps in natural language
>   - Decide `auto-execute` vs `human-review` paths
>  This is `just a guide`. It is not an official solution. For official guidance, support, or more detailed information. Please refer [RAG with Zero-Trust – Architecture Reference to Microsoft's official documentation](https://github.com/Azure/GPT-RAG) or contact Microsoft directly: [Microsoft Sales and Support](https://support.microsoft.com/contactus?ContactUsExperienceEntryPointAssetId=S.HP.SMC-HOME)

| **Category**                   | **Components**| **Purpose**                                                                                                      |
|--------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|
| **Core Components**            | - **Azure Arc API**<br>- **Resource Group**<br>- **Subscription**| - Source of recommendations (DR, security, performance, compliance) for on-prem and hybrid assets.<br>- Groups all resources under a single RG and subscription scope. |
| **Data Engineering Pipeline**  | - **Function App**<br>  *Every Function App requires a General-Purpose v2 Storage Account for triggers, state, and logging.*<br>- **App Service Plan** (Consumption/Premium SKU)<br>  *The App Service Plan can be serverless (Consumption) or a dedicated tier (Premium/Dedicated).*<br>- **Storage Account** (General Purpose v2 for Functions runtime) | Hosts and scales your ingestion/enrichment logic; fetches recommendations and sends them to AI for processing.   |
| **AI Layer**                   | **AI Foundry**| Classifies severity, summarizes actions, prioritizes recommendations, and suggests auto-execute vs manual review. |
| **Automation & Orchestration** | **Logic Apps**| Executes safe actions (DR failover, patching, SQL fixes) or sends Teams/Email approvals for high-risk items.      |
| **Monitoring & Governance**    | - **Azure Monitor + Log Analytics Workspace**<br>- **Power BI**| Tracks pipeline health, AI decisions, execution outcomes; visualizes trends, compliance, and automation SLAs.    |

## Overview 


<div align="center">
  <img src="https://github.com/user-attachments/assets/48774cdd-ba27-404c-b7fc-a124fd176e2a" alt="Centered Image" style="border: 2px solid #4CAF50; border-radius: 5px; padding: 5px;"/>
</div>

<details>
<summary><b> Workflow details </b> (Click to expand)</summary>
      
1. Azure Arc API (Source)
      - Acts as the entry point for all recommendations (DR, security, performance, compliance).
      - Provides raw JSON data about advisories from on-prem and hybrid resources.
2. Function App (with App Service Plan + Storage Account): Ingest and process recommendations.
      - Periodically calls Azure Arc API to fetch recommendations.
      - Stores raw data temporarily in the Storage Account.
      - Sends the data to the AI layer for enrichment.
3. AI Foundry: Adds intelligence to the pipeline.
      - Receives raw recommendations from the Function App.
      - Uses LLM models to:
          - Classify severity (High/Medium/Low).
          - Summarize recommendations in plain language.
          - Suggest whether to auto-execute or require manual review.
      - Returns enriched recommendations back to the Function App for storage and orchestration.
4. Logic Apps: Orchestrates actions based on AI decisions.
      - Reads enriched recommendations.
      - If `autoExecute = true`, triggers automation tasks (e.g., DR failover, patching, SQL index creation).
      - If `manualReview = true`, sends Teams or email notifications for approval.
5. Monitoring & Governance:
      - **Azure Monitor + Log Analytics Workspace**:
          - Collects telemetry from Function App, Logic Apps, and AI calls.
          - Tracks pipeline health, execution outcomes, and AI decision logs.
      - **Power BI**: Connects to Log Analytics or SQL data to visualize.
          - Number of recommendations processed.
          - Auto-executed vs manual approvals.
          - SLA compliance and risk reduction trends.
</details>


<!-- START BADGE -->
<div align="center">
  <img src="https://img.shields.io/badge/Total%20views-1289-limegreen" alt="Total views">
  <p>Refresh Date: 2025-09-09</p>
</div>
<!-- END BADGE -->
