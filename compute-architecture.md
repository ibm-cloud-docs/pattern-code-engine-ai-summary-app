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

# Architecture decisions for compute
{: #compute-decisions}

The following are compute architecture decisions for the inclusion of watsonx.ai summarization in the "AI summarization using highly resilient serverless architecture pattern in {{site.data.keyword.cloud}}" pattern.

| Architecture decision    | Requirement     | Options     | Decision       | Rationale     |
|------------------------------|---------------------|------------------|---------------------|--------------------|
| Compute platform for developer to run their code without the operational burden | * A serverless compute platform that allows developer to deploy web application code without the operational burden of building and deploying underlying infrastructure. \n * Pay for resources only when in use. | * {{site.data.keyword.codeenginefull}} \n * {{site.data.keyword.openwhisk}}    | {{site.data.keyword.codeenginefull_notm}}       | * {{site.data.keyword.codeenginefull_notm}} is a fully managed, serverless platform that runs your containerized workloads, including web apps, micro-services, event-driven functions, or batch jobs. \n * {{site.data.keyword.openwhisk}} has been deprecated. |
| Serverless Compute platform for Web Application    | * A serverless compute platform to run application to serve HTTP requests. \n * The application to be invoked on request or run permanently.    | * {{site.data.keyword.codeenginefull_notm}} – Application \n * {{site.data.keyword.codeenginefull_notm}} – Job \n * {{site.data.keyword.codeenginefull_notm}} – Function  | {{site.data.keyword.codeenginefull_notm}} – App  | * {{site.data.keyword.codeenginefull_notm}} – Application is meant for continuously running application that responds to HTTP web requests. \n * Other options of {{site.data.keyword.codeenginefull_notm}} (Job and Function) run to completion.                               |
{: caption="Table 2. Architecture decisions for compute" caption-side="bottom"}
