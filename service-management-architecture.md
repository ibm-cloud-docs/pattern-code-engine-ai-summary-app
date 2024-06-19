---
copyright:
  years: 2024, 2024
lastupdated: "2024-06-19"
subcollection: pattern-code-engine-ai-summary-app
keywords:
authors:
  - name: "Tushar Vaghode"
    email: "Tushar.Vaghode@ibm.com"
  - name: "Sharon Wheless"
    email: "sharon.wheless@us.ibm.com"
---

# Architecture decisions for service management
{: #service}

The following are service management architecture decisions for the "AI summarization using highly resilient serverless architecture pattern in {{site.data.keyword.cloud}}" pattern.

## Architecture decisions for monitoring
{: #monitoring}

| Architecture decision        | Requirement        | Options       | Decision          | Rationale     |
|------------------------------|--------------------|---------------|-------------------|---------------|
| Operational Monitoring of {{site.data.keyword.codeenginefull}} workload | Monitor app health to detect issues that might impact the availability of the app. | * {{site.data.keyword.monitoringfull}} \n * BYO Monitoring Tool | {{site.data.keyword.monitoringfull_notm}}  | {{site.data.keyword.monitoringfull_notm}} is integrated with {{site.data.keyword.codeengineshort}}.  {{site.data.keyword.codeengineshort}} forwards selected [metrics](/docs/codeengine?topic=codeengine-monitor#metrics-by-plan) about the workloads to {{site.data.keyword.mon_short}}. |
{: caption="Table 1. Architecture decisions for monitoring" caption-side="bottom"}

## Architecture decisions for logging
{: #logging}

| Architecture decision        | Requirement        | Options       | Decision          | Rationale     |
|------------------------------|--------------------|---------------|-------------------|---------------|
| Log Monitoring of Web App | Monitor application operational logs to detect issues that might impact the availability of the app. | * {{site.data.keyword.loganalysislong}}  \n * Application Logging Tool  \n * BYO Logging Tool | {{site.data.keyword.loganalysisshort}} | * {{site.data.keyword.loganalysisshort}} is integrated with {{site.data.keyword.codeengineshort}}. \n * When {{site.data.keyword.codeengineshort}} apps, jobs, functions, or builds in the console are enabled for logging, logs are forwarded to an {{site.data.keyword.loganalysisshort}} service where they are indexed, enabling full-text search through all generated messages and convenient querying based on specific fields. |
{: caption="Table 2. Architecture decisions for logging" caption-side="bottom"}

## Architecture decisions for auditing
{: #auditing}

| Architecture decision        | Requirement        | Options       | Decision          | Rationale     |
|------------------------------|--------------------|---------------|-------------------|---------------|
| Audit Logging             | Monitor audit logs to track changes to cloud resources and detect potential security problems. | * {{site.data.keyword.cloudaccesstraillong}}  \n * Hosted Event Search | {{site.data.keyword.cloudaccesstrailshort}} | * {{site.data.keyword.cloudaccesstrailshort}} is integrated with {{site.data.keyword.codeengineshort}}.  \n * View, manage, and audit user-initiated activities made in {{site.data.keyword.codeengineshort}} service instance by using the {{site.data.keyword.cloudaccesstrailshort}} service. |
{: caption="Table 3. Architecture decisions for auditing" caption-side="bottom"}

## Architecture decisions for alerting
{: #alerting}

| Architecture decision        | Requirement        | Options       | Decision          | Rationale     |
|------------------------------|--------------------|---------------|-------------------|---------------|
| Operational alerts        | Provide a mechanism to identify and send notifications about operational issues that are found across application and infrastructure. | {{site.data.keyword.mon_full_notm}} + {{site.data.keyword.loganalysisshort}} + {{site.data.keyword.en_full}}    | {{site.data.keyword.mon_full_notm}} + {{site.data.keyword.loganalysisshort}} + {{site.data.keyword.en_full}}    | * {{site.data.keyword.mon_full_notm}} and {{site.data.keyword.loganalysisshort}} support the configuration of alerts to detect operational issues and send notifications to targeted channels. \n * {{site.data.keyword.en_short}} are used to route the alert events to service destinations to automate response actions. |
| Audit alerts              | Provide a mechanism to identify and send notifications about issues that are found in audit logs.                      | {{site.data.keyword.cloudaccesstrailshort}} + {{site.data.keyword.mon_full_notm}} + {{site.data.keyword.en_short}} | {{site.data.keyword.cloudaccesstrailshort}} + {{site.data.keyword.mon_full_notm}} + {{site.data.keyword.en_short}} | * {{site.data.keyword.cloudaccesstrailshort}} supports the configuration of alerts to detect audit issues and send notifications to targeted channels. \n * {{site.data.keyword.en_short}} are used to route the alert events to service destinations to automate response actions.    |
{: caption="Table 4. Architecture decisions for alerting" caption-side="bottom"}
