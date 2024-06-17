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

# Architecture decisions for compute
{: #compute-decisions}

The following are compute architecture decisions for the inclusion of watsonx.ai summarization in the AI Summarization Using Highly Resilient Serverless Architecture in IBM Cloud® pattern.

| **Architecture decision**    | **Requirement**     | **Options**      | **Decision**        | **Rationale**      |
|------------------------------|---------------------|------------------|---------------------|--------------------|
| Compute platform for developer to run their code without the operational burden | * A serverless compute platform that allows developer to deploy web application code without the operational burden of building and deploying underlying infrastructure. \n * Pay for resources only when in use. | * IBM Cloud® Code Engine \n * IBM Cloud Functions                                                  | IBM Cloud® Code Engine       | * IBM Cloud® Code Engine is a fully managed, serverless platform that runs your containerized workloads, including web apps, micro-services, event-driven functions, or batch jobs. \n * IBM Cloud Functions has been deprecated. |
| Serverless Compute platform for Web Application                                 | * A serverless compute platform to run application to serve HTTP requests. \n * The application to be invoked on request or run permanently.             | * IBM Cloud® Code Engine – App * \n IBM Cloud® Code Engine – Job \n * IBM Cloud®Code Engine – Function  | IBM Cloud®Code Engine – App  | * IBM Cloud® Code Engine – App is meant for continuously running application that responds to HTTP web requests. \n * Other options of IBM Cloud® Code Engine (Job and Function) run to completion.                               |
{: caption="Table 2. Architecture decisions for compute" caption-side="bottom"}
