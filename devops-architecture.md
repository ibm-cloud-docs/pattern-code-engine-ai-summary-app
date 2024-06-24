---
copyright:
  years: 2024, 2024
lastupdated: "2024-06-24"
subcollection: pattern-code-engine-ai-summary-app
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
The following are devops architecture decisions for the inclusion of watsonx.ai summarization in the "AI summarization using highly resilient serverless architecture pattern in {{site.data.keyword.cloud}}" pattern.

| Architecture decision     | Requirement                | Options                | Decision              | Rationale         |
|---------------------------|----------------------------|------------------------|-----------------------|-------------------|
| Code repository           | Meet organization's security requirements such as access management, vulnerability scanning, or app privacy. | * [{{site.data.keyword.registrylong}}](/docs/Registry?topic=Registry-getting-started#getting-started) \n * Public Docker Hub \n * Any other private registry | [{{site.data.keyword.registrylong_notm}}](/docs/Registry?topic=Registry-getting-started#getting-started) | * {{site.data.keyword.registrylong_notm}} provides a multi-tenant, highly available, scalable, and encrypted private image registry that is hosted and managed by {{site.data.keyword.cloud_notm}}. \n * By using Container Registry, only users with access to your {{site.data.keyword.cloud_notm}} account can access your images by setting up a registry namespace. \n * Built-in vulnerability advisor features that scan for potential security issues and vulnerabilities. |
{: caption="Table 1. Architecture decisions for devops" caption-side="bottom"}
