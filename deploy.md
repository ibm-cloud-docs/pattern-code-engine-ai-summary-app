---
copyright:
  years: 2024, 2026
lastupdated: "2026-08-05"

subcollection: pattern-code-engine-ai-summary-app

keywords:
---
{{site.data.keyword.attribute-definition-list}}


# Deploying an AI summarization in Code Engine architecture
{: #ai-code-engine-app-da}

This guide outlines deploying an AI summarization application in {{site.data.keyword.codeenginefull}}, using a highly resilient enterprise architecture. The deployment is based on an existing deployable architecture template, as well as a series of customizations to tailor the setup to the specific requirements for your environment.

This is designed for customers who need a scalable, multi-region infrastructure with the flexibility of customizations post the initial deployment of the base Deployable Architecture. It allows for adapting various components, such as networking and security, to better suit individual business needs after the foundational architecture has been established.


## Before you begin
{: #ai-code-engine-app-prereqs}

You need the following items to deploy and configure this reference architecture:

* An [IBM Cloud account](https://cloud.ibm.com/registration){: external}. Ensure you have an active IBM Cloud account with the necessary permissions to create resources.
* [Required IAM access policies](https://github.com/terraform-ibm-modules/terraform-ibm-code-engine/blob/main/README.md#required-iam-access-policies){: external}.
* A [watsonx subscription](https://dataplatform.cloud.ibm.com/settings/account?context=wx){: external}. Verify that you have a valid watsonx subscription and the necessary entitlements to deploy watsonx on IBM Cloud.
* A custom domain name to run the web application.


## Provision Architecture
{: #ai-code-engine-app-provision}

1. Provision [the architecture stack](https://cloud.ibm.com/catalog/7a4d68b4-cf8b-40cd-a3d1-f49aff526eb3/architecture/Retrieval_Augmented_Generation_Pattern-5fdd0045-30fc-4013-a8bc-6db9d5447a52-global){: external} to deploy the following:
   * Account Infrastructure base for creating and configuring additional needed components of an IBM Cloud account.
   * The watsonx.ai service to deploy Watson Studio, Watson Machine Learning and Cloud Object Storage (COS).
   * {{site.data.keyword.codeengineshort}} to create the highly resilient serverless architecture for housing an internet-facing web application. By provisioning an application in two regions, user requests are served in an active-active manner and if an outage in one region occurs, the second region continues to serve user requests.
   * {{site.data.keyword.monitoringfull_notm}} to integrate with {{site.data.keyword.codeengineshort}} and forward selected metrics about workloads.
   * {{site.data.keyword.logs_full_notm}} for quick issue detection, performance optimization and strong security compliance.
   * {{site.data.keyword.logs_full_notm}} to support the configuration of alerts to detect audit issues and send notifications to targeted channels.
2. Repeat step 1 to provision the additional region.
3. Provision [{{site.data.keyword.cis_full}}](https://github.com/terraform-ibm-modules/terraform-ibm-cis){: external} to configure Domain Name Services (DNS), Global Load Balancer and Web Application Firewall (WAF).
