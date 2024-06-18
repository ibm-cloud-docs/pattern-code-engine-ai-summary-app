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

# Overview
{: #overview}

The objective of `AI Summarization Using Highly Resilient Serverless Architecture in IBM Cloud` pattern is to provide users a high-level overview of solution design and components used in hosting highly resilient serverless web application.

This pattern describes deployment architecture of a web application on {{site.data.keyword.codeenginefull}} platform deployed across multiple regions of IBM Cloud, making it resilient to regional failures and to meet disaster recovery requirements for enterprise workloads. Additionally, this pattern provides a use case for the web application demonstrating the text summarization capabilities that are easily available leveraging one of the large language models available in IBM watsonx.ai platform hosted in IBM Cloud.

The web application uses ‘IBM-watsonx-ai’ Python library for inferencing using the foundation model available in IBM watsonx.ai.

While IBM Cloud® Code Engine serverless platform experience is designed so that one can focus on writing code and not on the infrastructure that is needed to host it, this guidance is intended to:

* Accelerate and simplify solution design by providing a standard IBM Cloud deployment architecture reference following the [IBM Architecture Framework](/docs/architecture-framework).

* Provide a prescriptive, end-2-end enterprise-class solution design, with diagrams, component architecture decisions along with rationale for cloud component selection to meet enterprise requirements.

* Deliver the defined performance, system availability and security within the scope and capabilities of IBM Cloud® and its scaling capabilities.
