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

# Overview
{: #overview}

The objective of the AI summarization that uses highly resilient serverless architecture pattern in {{site.data.keyword.cloud}} is to provide users a high-level overview of solution design and components that are used in hosting a highly resilient serverless web application.

This pattern describes the deployment architecture of a web application on {{site.data.keyword.codeenginefull}} platform that is deployed across multiple regions of {{site.data.keyword.cloud_notm}}, making it resilient to regional failures and to meet disaster recovery requirements for enterprise workloads. Also, this pattern provides a use case for the web application that demonstrates the text summarization capabilities that are easily available using one of the large language models available in {{site.data.keyword.IBM_notm}} watsonx.ai platform that is hosted in {{site.data.keyword.cloud_notm}}.

The web application uses ‘IBM-watsonx-ai’ Python library for inferencing by using the foundation model available in {{site.data.keyword.IBM_notm}} watsonx.ai.

The {{site.data.keyword.codeengineshort}} serverless platform experience is designed so that one can focus on writing code and not on the infrastructure that is needed to host it. In addition, this guidance is intended to:

* Accelerate and simplify solution design by providing a standard {{site.data.keyword.cloud_notm}} deployment architecture reference that follows the [IBM Architecture Framework](/docs/architecture-framework).

* Provide a prescriptive, end-to-end enterprise-class solution design, with diagrams, component architecture decisions along with rationale for cloud component selection to meet enterprise requirements.

* Deliver the defined performance, system availability and security within the scope and capabilities of {{site.data.keyword.cloud_notm}} and its scaling capabilities.
