---
copyright:
  years: 2023
lastupdated: "2024-06-11"
subcollection: pattern-code-engine-ai-summary-app
keywords:
authors:
  - name: "Tushar Vaghode"
    email: "Tushar.Vaghode@ibm.com"
  - name: "Sharon Wheless"
    email: "sharon.wheless@us.ibm.com"
---

{{site.data.keyword.attribute-definition-list}}

# Architecture decisions for network
{: #network-decisions}

The following are data architecture decisions for the inclusion of watsonx.ai summarization in the AI Summarization Using Highly Resilient Serverless Architecture in IBM Cloud® pattern.

The following are network architecture decisions for the AI Summarization Using Highly Resilient Serverless Architecture in IBM Cloud® pattern.

## Architecture decisions for Network Visibility (connectivity, segmentation, and isolation)
{: #network-decision-connectivity-segmentation-isolation }

| **Architecture decision**          | **Requirement**           | **Options**        | **Decision**    | **Rationale**               |
|------------------------------------|---------------------------|--------------------|-----------------|-----------------------------|
| Network segmentation and isolation | * Allow connectivity to web application from Internet. \n * Ability to control visibility of deployed application. | An application can be exposed to the internet, to the IBM Cloud private network or scoped only to other resources in the same IBM Cloud® Code Engine project by setting up application visibility level: * Internal (Project): An app with this setting can receive requests from components in the same IBM Cloud® Code Engine project. \n * Private Endpoint: An app with this setting is exposed to the other IBM Cloud services in IBM Cloud private network by using VPE, along with other components within the same IBM Cloud® Code Engine project. \n * Public Endpoint: An app with this setting is exposed to the internet and your IBM Cloud® Code Engine project. | Public Endpoint | Public Endpoint: Requirement is to allow connectivity to web application from public internet. |
{: caption="Table 3. Architecture decisions for network" caption-side="bottom"}
