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

# Architecture decisions for devops
{: #devops-decisions}

| **Architecture decision** | **Requirement**            | **Options**            | **Decision**          | **Rationale**     |
|---------------------------|----------------------------|------------------------|-----------------------|-------------------|
| Code Repository           | Meet organization's security requirements such as access management, vulnerability scanning, or app privacy. | * [IBM Cloud Container Registry](https://cloud.ibm.com/docs/Registry?topic=Registry-getting-started#getting-started) \n * Public Docker Hub \n * Any other private registry | [IBM Cloud Container Registry](https://cloud.ibm.com/docs/Registry?topic=Registry-getting-started#getting-started) | * IBM Cloud Container Registry provides a multi-tenant, highly available, scalable, and encrypted private image registry that is hosted and managed by IBM. \n * By using Container Registry, only users with access to your IBM Cloud account can access your images by setting up registry namespace. \n * Built-in Vulnerability Advisor features that scan for potential security issues and vulnerabilities. |
{: caption="Table 1. Architecture decisions for devops" caption-side="bottom"}
