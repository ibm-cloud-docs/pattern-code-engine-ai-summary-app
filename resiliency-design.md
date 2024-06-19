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

# Resiliency design
{: #resiliency-design}

{{site.data.keyword.codeenginefull}} has a Service Level Agreement of 99.99% and is offered in several locations. Each MZR (Multi-zone Region of {{site.data.keyword.cloud}}) region has three different data centers for redundancy. By default, your workload is deployed within a zone of an MZR region. If a failure of the hosting zone occurs, the workload is automatically re-created in one of the remaining zones.

In a major regional disaster, such as an earthquake, flood, or tornado, an entire region might be impacted. To ensure that workloads are resilient to such events, workloads can be deployed across multiple MZR regions with an automatic failover mechanism, which uses an Edge Proxy service such as [{{site.data.keyword.cis_full}}](/docs/cis?topic=cis-getting-started).

This pattern describes deploying web application on {{site.data.keyword.codeengineshort}} Application platform in two regions of {{site.data.keyword.cloud_notm}} in an active-active manner. This architecture provides combined availability of 99.999999% for web app hosted in {{site.data.keyword.codeengineshort}} Application.
