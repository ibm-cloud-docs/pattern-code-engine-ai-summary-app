---
copyright:
  years: 2024, 2024
lastupdated: "2024-06-21"
subcollection: pattern-code-engine-ai-summary-app
keywords:
authors:
  - name: "Tushar Vaghode"
    email: "Tushar.Vaghode@ibm.com"
  - name: "Sharon Wheless"
    email: "sharon.wheless@us.ibm.com"
---

{{site.data.keyword.attribute-definition-list}}

# Architecture decisions for resiliency
{: #resiliency-decisions}

## Architecture decisions for high availability
{: #high-availability}

| Architecture decision | Requirement            | Options           | Decision      | Rationale  |
|---------------------------|----------------------------|------------------------|-----------------------|-------------------|
| High availability of application     | * Ensure application availability if outages occur. \n * Support SLA targets for availability. | * Single zone, single region  \n * Single zone, multi region  | Single zone, multi Region | * By default, {{site.data.keyword.codeenginefull}} workload is deployed within a zone of a MZR region. If a failure of the hosting zone occurs, the workload is automatically re-created in one of the remaining zones. \n * To protect against regional failure, workloads to be deployed across multiple MZR regions with automatic failover mechanism by using an Edge proxy service such as [{{site.data.keyword.cis_full}}](/docs/cis?topic=cis-getting-started).   |
| High availability of code repository | Ensure the code repository is available in case of a zone outage.    | Multiple zones       | Multiple zones   | * In each supported region, traffic is load balanced across registry infrastructure in multiple availability zones, with no single point of failure. \n * Data that is stored in {{site.data.keyword.registrylong}} is replicated over the availability zones and it is also backed up in another region regularly.     |
{: caption="Table 1. Architecture decisions for high availability" caption-side="bottom"}

## Architecture decisions for backup and restore
{: #backup-and-restore}

| Architecture decision | Requirement           | Options           | Decision         | Rationale   |
|---------------------------|----------------------------|------------------------|-----------------------|-------------------|
| Code repository backup    | Backup application images to enable recovery. | Default backup option of {{site.data.keyword.registryshort}}  | Default backup option of {{site.data.keyword.registryshort}}  | By default, data that is stored in {{site.data.keyword.registryshort}} is replicated over the availability zones and it is also backed up in another region regularly. |
{: caption="Table 2. Architecture decisions for backup and restore" caption-side="bottom"}

## Architecture decisions for disaster recovery
{: #disaster-recovery}

| Architecture decision | Requirement            | Options            | Decision          | Rationale     |
|---------------------------|----------------------------|------------------------|-----------------------|-------------------|
| Disaster recovery: Application     | Highly resilient application disaster recovery capability in secondary region to meet near zero RTO/RPO requirements. | * Active-Active \n * Active-Standby/Hot DR site \n * Active-Standby/warm DR site \n * Backup and Restore (Cold DR site) | Active-Active   | The recommended approach for a highly resilient application by deploying resources in multiple regions of {{site.data.keyword.cloud_notm}} and then using the Global load balancer feature of [{{site.data.keyword.cis_short}}](/docs/cis?topic=cis-getting-started) to load balance between them. |
| Disaster recovery: Code repository | Near zero RPO/RTO code repository availability for disaster recovery         | Use the default DR capability of code repository DevOps pipeline to push images to multiple regions    | Use the DevOps pipeline to push images to multiple regions | * Use the development pipeline to push images in multiple regions for near zero RPO/RTO capability. \n * The default RPO/RTO of {{site.data.keyword.registryshort}} is 48/24 hours which does not meet the requirement of a highly resilient application with a near zero RPO/RTO.       |
{: caption="Table 3. Architecture decisions for disaster recovery" caption-side="bottom"}
