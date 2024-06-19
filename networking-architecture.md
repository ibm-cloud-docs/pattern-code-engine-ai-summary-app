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

# Architecture decisions for network
{: #network-decisions}

The following are network architecture decisions for the inclusion of watsonx.ai summarization in the "AI summarization using highly resilient serverless architecture pattern in {{site.data.keyword.cloud}}" pattern.

## Architecture decisions for Network Visibility (connectivity, segmentation, and isolation)
{: #network-decision-connectivity-segmentation-isolation }

| Architecture decision         | Requirement         | Options      | Decision   | Rationale              |
|------------------------------------|---------------------------|--------------------|-----------------|-----------------------------|
| Network segmentation and isolation | * Allow connectivity to web application from Internet. \n * Ability to control visibility of deployed application. | An application can be exposed to the internet, to the {{site.data.keyword.cloud}} private network or scoped only to other resources in the same {{site.data.keyword.codeenginefull}} project by setting up application visibility level: \n * Internal (Project): An app with this setting can receive requests from components in the same {{site.data.keyword.codeengineshort}} project. \n * Private Endpoint: An app with this setting is exposed to the other {{site.data.keyword.cloud_notm}} services in {{site.data.keyword.cloud_notm}} private network by using {{site.data.keyword.vpe_full}}, along with other components within the same {{site.data.keyword.codeengineshort}} project. \n * Public Endpoint: An app with this setting is exposed to the internet and your {{site.data.keyword.codeengineshort}} project. | Public Endpoint | Public Endpoint: Requirement is to allow connectivity to web application from public internet. |
{: caption="Table 3. Architecture decisions for network" caption-side="bottom"}
