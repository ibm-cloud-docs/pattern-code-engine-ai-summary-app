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

{{site.data.keyword.attribute-definition-list}}

# Service management design
{: #service-management-design}

## **Logging**
{: #logging}

{{site.data.keyword.codeenginefull}} apps, jobs, functions, or builds in the console with logging enabled, the logs are forwarded to an [{{site.data.keyword.loganalysislong}}](/docs/log-analysis?topic=log-analysis-getting-started) service where they are indexed, enabling full-text search through all generated messages and convenient querying based on specific fields. Logging is enabled for {{site.data.keyword.codeengineshort}} only one time per region, per account.


## **Auditing**
{: #auditing}

{{site.data.keyword.codeengineshort}} sends audit logs to the [{{site.data.keyword.cloudaccesstraillong}}](/docs/activity-tracker?topic=activity-tracker-getting-started) service in the same region as the {{site.data.keyword.codeengineshort}} project. {{site.data.keyword.cloudaccesstrailshort}} records user-initiated activities that change the state of a service in {{site.data.keyword.cloud}}. You can use this service to investigate abnormal activity and critical actions and to follow regulatory audit requirements. You can also be alerted about actions as they happen. The events that are collected follow the Cloud Auditing Data Federation (CADF) standard.


## **Monitoring**
{: #monitoring}

Get insight into the performance of your workloads that are deployed with {{site.data.keyword.codeengineshort}}. Metrics can help you find bottlenecks or predict possible production problems. You can use the [{{site.data.keyword.monitoringfull_notm}}](/docs/monitoring?topic=monitoring-getting-started) service to monitor your {{site.data.keyword.codeengineshort}} workloads. {{site.data.keyword.codeengineshort}} forwards selected information about your workloads to {{site.data.keyword.mon_short}} so that you can monitor specific metrics such as requests, revisions, and duration. To set up your {{site.data.keyword.codeengineshort}} customer metrics dashboards in {{site.data.keyword.mon_short}}, you must create a {{site.data.keyword.mon_short}} instance and then enable Platform Metrics in the same region as the {{site.data.keyword.codeengineshort}} projects that you want to monitor. If you have deployments in more than one region, you must provision {{site.data.keyword.mon_short}} and enable platform metrics for each region.
