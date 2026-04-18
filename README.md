# Azure Business Workflow Observability Platform

![Azure](https://img.shields.io/badge/Microsoft_Azure-0078D4?style=for-the-badge&logo=microsoft-azure&logoColor=white)
![Azure Logic Apps](https://img.shields.io/badge/Azure_Logic_Apps-0078D4?style=for-the-badge&logo=microsoft-azure&logoColor=white)
![Kibana](https://img.shields.io/badge/Kibana-005571?style=for-the-badge&logo=kibana&logoColor=white)
![Application Insights](https://img.shields.io/badge/Application_Insights-0078D4?style=for-the-badge&logo=microsoft-azure&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)

> Centralized observability and monitoring platform for enterprise business workflows running across Azure environments.  
> Achieved **~60% reduction in Mean Time to Resolution (MTTR)** for critical workflow failures.

---

## 📌 Project Overview

Enterprise workflows running across Azure environments had no single place to observe health, failures, or performance. Issues were discovered late — often by end users — and root cause analysis was slow and manual.

This platform provides **end-to-end visibility** across all workflows: real-time health dashboards, automated failure alerting via Teams/Outlook/ServiceNow, and structured logging that makes debugging fast and precise.

---

## 🏗️ Architecture

```
┌──────────────────────────────────────────────────────────────┐
│               ENTERPRISE WORKFLOWS (Azure)                   │
│    ADF Pipelines · Logic Apps · Function Apps · REST APIs    │
└─────────────────────────┬────────────────────────────────────┘
                          │  Emit logs & metrics
                          ▼
┌──────────────────────────────────────────────────────────────┐
│                  LOGGING & METRICS LAYER                     │
│         Azure Log Analytics Workspace  ·  KQL Queries        │
│         Application Insights  ·  Custom Log Tables           │
└──────────┬───────────────────────────────────┬───────────────┘
           │                                   │
           ▼                                   ▼
┌─────────────────────┐             ┌──────────────────────────┐
│   ALERTING ENGINE   │             │   DASHBOARD & ANALYTICS  │
│   Logic Apps        │             │   Kibana Real-time Views  │
│   REST APIs         │             │   Application Insights    │
│   Liquid Templates  │             │   KQL-powered Reports     │
└──────────┬──────────┘             └──────────────────────────┘
           │
           ▼
┌──────────────────────────────────────────────────────────────┐
│                  NOTIFICATION CHANNELS                       │
│     📧 Outlook Email · 💬 Microsoft Teams · 🎫 ServiceNow    │
└──────────────────────────────────────────────────────────────┘
```

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Workflow Sources | Azure Data Factory, Logic Apps, Function Apps |
| Logging | Azure Log Analytics, Custom Log Tables |
| Query Language | KQL (Kusto Query Language) |
| Monitoring | Application Insights, Kibana |
| Alerting Engine | Azure Logic Apps, REST APIs, Liquid Templates |
| Notifications | Outlook, Microsoft Teams, ServiceNow |
| CI/CD | Azure DevOps |

---

## ✅ Key Achievements

- ✅ **~60% reduction in MTTR** for critical workflow failures
- ✅ Real-time dashboards covering **all enterprise workflows** in one place
- ✅ Automated alerts fired to **Teams, Outlook and ServiceNow** on failure detection
- ✅ Structured logging with **custom log tables** for fast root cause analysis
- ✅ Proactive monitoring — issues caught **before end users notice them**
- ✅ KQL-powered analytics for trend analysis and capacity planning

---

## 📁 Project Structure

```
azure-observability-platform/
│
├── log_analytics/              # KQL queries for log analysis
│   ├── workflow_health.kql     # Overall workflow health queries
│   ├── failure_patterns.kql    # Failure trend analysis
│   └── performance_metrics.kql # Processing time & throughput
│
├── alerting/                   # Logic App alert definitions
│   ├── failure_alert/          # Workflow failure triggers
│   ├── threshold_alert/        # Performance threshold breaches
│   └── templates/              # Liquid Templates for notifications
│
├── dashboards/                 # Kibana dashboard configs
│   ├── workflow_overview/      # High-level health summary
│   ├── failure_analysis/       # Failure drill-down views
│   └── performance/            # Throughput & latency views
│
├── notifications/              # Notification channel configs
│   ├── teams_connector/
│   ├── outlook_connector/
│   └── servicenow_connector/
│
├── docs/                       # Architecture diagrams, runbooks
│
└── README.md
```

---

## 📋 Alert Types

| Alert | Trigger | Channel |
|---|---|---|
| Workflow Failure | Any pipeline/function failure | Teams + ServiceNow |
| SLA Breach | Processing time exceeds threshold | Outlook + Teams |
| Retry Exhausted | Max retries hit with no success | ServiceNow ticket |
| Data Quality Issue | Validation failure in pipeline | Outlook |
| Connectivity Failure | Private endpoint / IR unreachable | Teams + ServiceNow |

---

## 📊 Impact

| Metric | Before | After |
|---|---|---|
| Mean Time to Resolution (MTTR) | Baseline | **~60% faster** |
| Issue detection | Reactive (user reported) | Proactive (auto-detected) |
| Alert routing | Manual | Fully automated |
| Dashboard visibility | None | Real-time across all workflows |
| Root cause analysis | Hours | Minutes (structured logs + KQL) |

---

## 🔍 Sample KQL Query

```kql
// Workflow failure summary — last 24 hours
CustomLogs_CL
| where TimeGenerated > ago(24h)
| where Status_s == "Failed"
| summarize FailureCount = count() by WorkflowName_s, bin(TimeGenerated, 1h)
| order by FailureCount desc
| render timechart
```

---

## ⚠️ Note

This repository contains **architecture documentation, KQL query patterns, alert design, and sanitized sample configs** only.  
No proprietary client data or production credentials are included.

---

## 👤 Author

**Prakash Thakur** — Data Engineer, InfoOrigin Pvt. Ltd.  
📧 prakash7thakur@gmail.com  
🌐 [Portfolio](https://personal-portfolio-d-z8t2.bolt.host/)
