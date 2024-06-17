---
copyright:
  years: 2023
lastupdated: "2024-06-11"
subcollection: "pattern-code-engine-ai-summary-app"
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

| **Architecture decision** | **Requirement**            | **Options**            | **Decision**          | **Rationale**     |
|---------------------------|----------------------------|------------------------|-----------------------|-------------------|
| High Availability of Application     | * Ensure application availability if outages occur. \n * Support SLA targets for availability. | * Single zone, single region  \n * Single zone, Multi region  | Single Zone, Multi Region | * By default, IBM Cloud® Code Engine workload is deployed within a zone of a MZR region. If a failure of the hosting zone occurs, the workload is automatically re-created in one of the remaining zones. \n * To protect against regional failure workloads to be deployed across multiple MZR regions with automatic failover mechanism by leveraging an Edge Proxy service such as [IBM Cloud® Internet Services](https://cloud.ibm.com/docs/cis?topic=cis-getting-started).   |
| High Availability of Code Repository | Ensure code repository is available in case of a zone outage.                           | Multiple zones                                         | Multiple zones            | * In each supported region, traffic is load balanced across registry infrastructure in multiple availability zones, with no single point of failure. \n * Data that is stored in IBM Cloud Container Registry is replicated over the availability zones and it is also backed up in another region regularly.              |
{: caption="Table 1. Architecture decisions for high availability" caption-side="bottom"}

## Architecture decisions for backup and restore
{: #backup-and-restore}

| **Architecture decision** | **Requirement**            | **Options**            | **Decision**          | **Rationale**     |
|---------------------------|----------------------------|------------------------|-----------------------|-------------------|
| Code Repository Backup    | Backup application images to enable recovery. | Default backup option of IBM Code Repository  | Default backup option of IBM Code Repository  | By default, data that is stored in IBM Cloud Container Registry is replicated over the availability zones and it is also backed up in another region regularly. |
{: caption="Table 2. Architecture decisions for backup and restore" caption-side="bottom"}

## Architecture decisions for disaster recovery
{: #disaster-recovery}

| **Architecture decision** | **Requirement**            | **Options**            | **Decision**          | **Rationale**     |
|---------------------------|----------------------------|------------------------|-----------------------|-------------------|
| Disaster Recovery - application     | Highly resilient Application disaster recovery capability in secondary region to meet near zero RTO/RPO requirements. | * Active-Active \n * Active-Standby / Hot DR Site \n * Active-Standby / Warm DR Site \n * Backup & Restore (Cold DR Site) | Active-Active   | Recommended approach for highly resilient application by deploying resources in multiple regions of IBM Cloud and then using Global Load Balancer feature of [IBM Cloud® Internet Services](https://cloud.ibm.com/docs/cis?topic=cis-getting-started) to load balance between them. |
| Disaster Recovery – Code Repository | Near zero RPO/RTO Code Repository availability for disaster recovery         | Leverage Default DR capability of Code Repository  DevOps pipeline to push images to multiple regions    | Leverage DevOps pipeline to push images to multiple regions | Use Development pipeline to push images in multiple regions for near zero RPO/RTO capability. Default RPO/RTO of IBM Code Repository is 48/24 hours which does not meet requirement of a highly resilient application with a near zero RPO/RTO.       |
{: caption="Table 3. Architecture decisions for disaster recovery" caption-side="bottom"}
