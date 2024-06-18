---
copyright:
  years: 2024, 2024
lastupdated: "2024-06-18"
subcollection: pattern-code-engine-ai-summary-app
keywords:
authors:
  - name: "Tushar Vaghode"
    email: "Tushar.Vaghode@ibm.com"
  - name: "Sharon Wheless"
    email: "sharon.wheless@us.ibm.com"
---

{{site.data.keyword.attribute-definition-list}}

# Service management design
{: #service-management-design}

## **Logging**
{: #logging}

IBM Cloud® Code Engine apps, jobs, functions, or builds in the console with logging enabled, the logs are forwarded to an [IBM Log Analysis](/docs/log-analysis?topic=log-analysis-getting-started) service where they are indexed, enabling full-text search through all generated messages and convenient querying based on specific fields. Logging is enabled for IBM Cloud® Code Engine only one time per region, per account.


## **Auditing**
{: #auditing}

IBM Cloud® Code Engine sends audit logs to the [IBM Cloud Activity Tracker](/docs/activity-tracker?topic=activity-tracker-getting-started) service in the same region as the IBM Cloud® Code Engine project. IBM Cloud Activity Tracker records user-initiated activities that change the state of a service in IBM Cloud®. You can use this service to investigate abnormal activity and critical actions and to follow regulatory audit requirements. You can also be alerted about actions as they happen. The events that are collected follow the Cloud Auditing Data Federation (CADF) standard.


## **Monitoring**
{: #monitoring}

Get insight into the performance of your workloads that are deployed with IBM Cloud® Code Engine. Metrics can help you find bottlenecks or predict possible production problems. You can use the [IBM Cloud® Monitoring](/docs/monitoring?topic=monitoring-getting-started) service to monitor your IBM Cloud® Code Engine workloads. IBM Cloud® Code Engine forwards selected information about your workloads to Monitoring so that you can monitor specific metrics such as requests, revisions, and duration. To set up your IBM Cloud® Code Engine customer metrics dashboards in Monitoring, you must create a Monitoring instance and then enable Platform Metrics in the same region as the IBM Cloud® Code Engine projects that you want to monitor. If you have deployments in more than one region, you must provision Monitoring and enable platform metrics for each region.
