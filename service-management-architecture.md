---
copyright:
  years: 2023
lastupdated: "2024-06-11"
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

The following are service management architecture decisions for the AI Summarization Using Highly Resilient Serverless Architecture in IBM Cloud pattern.

## Architecture decisions for monitoring
{: #monitoring}

| **Architecture decision**        | **Requirement**        | **Options**       | **Decision**          | **Rationale**     |
|----------------------------------|------------------------|-------------------|-----------------------|-------------------|
| Operational Monitoring of IBM Cloud® Code Engine workload | Monitor app health to detect issues that might impact the availability of the app. | * IBM Cloud Monitoring \n * BYO Monitoring Tool | IBM Cloud Monitoring  | IBM Cloud Monitoring is integrated with IBM Cloud® Code Engine.  IBM Cloud® Code Engine forwards selected [metrics](https://cloud.ibm.com/docs/codeengine?topic=codeengine-monitor#metrics-by-plan) about the workloads to IBM Cloud Monitoring. |
{: caption="Table 1. Architecture decisions for monitoring" caption-side="bottom"}

## Architecture decisions for logging
{: #logging}

| **Architecture decision**        | **Requirement**        | **Options**       | **Decision**          | **Rationale**     |
|----------------------------------|------------------------|-------------------|-----------------------|-------------------|
| Log Monitoring of Web App | Monitor application operational logs to detect issues that might impact the availability of the app. | * IBM Log Analysis  \n * Application Logging Tool  \n * BYO Logging Tool | IBM Log Analysis | * IBM Log Analysis is integrated with IBM Cloud® Code Engine. \n * When IBM Cloud® Code Engine apps, jobs, functions, or builds in the console are enabled for logging, logs are forwarded to an IBM Log Analysis service where they are indexed, enabling full-text search through all generated messages and convenient querying based on specific fields. |
{: caption="Table 2. Architecture decisions for logging" caption-side="bottom"}

## Architecture decisions for auditing
{: #auditing}
| **Architecture decision**        | **Requirement**        | **Options**       | **Decision**          | **Rationale**     |
|----------------------------------|------------------------|-------------------|-----------------------|-------------------|
| Audit Logging             | Monitor audit logs to track changes to cloud resources and detect potential security problems. | * IBM Cloud Activity Tracker  \n * Hosted Event Search | IBM Cloud Activity Tracker | * IBM Cloud Activity Tracker is integrated with IBM Cloud® Code Engine.  \n * View, manage, and audit user-initiated activities made in IBM Cloud® Code Engine service instance by using the IBM Cloud Activity Tracker service. |
{: caption="Table 3. Architecture decisions for auditing" caption-side="bottom"}

## Architecture decisions for alerting
{: #alerting}

| **Architecture decision**        | **Requirement**        | **Options**       | **Decision**          | **Rationale**     |
|----------------------------------|------------------------|-------------------|-----------------------|-------------------|
| Operational alerts        | Provide a mechanism to identify and send notifications about operational issues that are found across application and infrastructure. | IBM Cloud Monitoring + IBM Cloud Logging + Event Notifications    | IBM Cloud Monitoring + IBM Cloud Logging + Event Notifications    | * IBM Cloud Monitoring and IBM Cloud Logging support the configuration of alerts to detect operational issues and send notifications to targeted channels. \n * Event Notifications are used to route the alert events to service destinations to automate response actions. |
| Audit alerts              | Provide a mechanism to identify and send notifications about issues that are found in audit logs.                                     | IBM Cloud Activity Tracker + IBM Monitoring + Event Notifications | IBM Cloud Activity Tracker + IBM Monitoring + Event Notifications | * IBM Activity Tracker supports the configuration of alerts to detect audit issues and send notifications to targeted channels. \n * Event Notifications are used to route the alert events to service destinations to automate response actions.                            |
{: caption="Table 4. Architecture decisions for alerting" caption-side="bottom"}
