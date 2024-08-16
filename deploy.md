---
copyright:
  years: 2024
lastupdated: "2024-08-15"

subcollection: pattern-code-engine-ai-summary

keywords:
---
{{site.data.keyword.attribute-definition-list}}


# Deploying a AI Summarization in Code Engine architecture

{: #ai-code-engine-app-da}

This guide outlines deploying an AI summarization application in IBM Cloud Code Engine, using a highly resilient enterprise architecture. The deployment is based on an existing deployable architecture template, as well as a series of customizations to tailor the setup to the specific requirements for your environment.

This is designed for customers who need a scalable, multi-region infrastructure with the flexibility of customizations post the initial deployment of the base Deployable Architecture. It allows for adapting various components, such as networking and security, to better suit individual business needs after the foundational architecture has been established.


## Before you begin
{: #ai-code-engine-app-prereqs}

You need the following items to deploy and configure this reference architecture:

* An [IBM Cloud account](https://cloud.ibm.com/registration). Ensure you have an active IBM Cloud account with the necessary permissions to create resources. Refer to 
[Account Infrastructure base](https://cloud.ibm.com/catalog/7a4d68b4-cf8b-40cd-a3d1-f49aff526eb3/architecture/deploy-arch-ibm-account-infra-base-63641cec-6093-4b4f-b7b0-98d2f4185cd6-global) for creating and configuring additional needed components of an IBM Cloud account.
* [Required IAM access policies](https://github.com/terraform-ibm-modules/terraform-ibm-code-engine/blob/main/README.md#required-iam-access-policies).
* A [watsonx subscription](https://dataplatform.cloud.ibm.com/settings/account?context=wx). Verify that you have a valid Watsonx subscription and the necessary entitlements to deploy watsonx on IBM Cloud.
* A custom domain name to run the web application.


## Provision Architecture
{: #ai-code-engine-app-provision}

1. Provision [the architecture stack](https://cloud.ibm.com/catalog/7a4d68b4-cf8b-40cd-a3d1-f49aff526eb3/architecture/Retrieval_Augmented_Generation_Pattern-5fdd0045-30fc-4013-a8bc-6db9d5447a52-global) to deploy the following:
  * The watsonx.ai service to deploy Watson Studio, Watson Machine Learning and Cloud Object Storage (COS).
  * Code Engine to create the highly resilient serverless architecture for housing an internet-facing web application. By provisioning an application in two regions, user requests are served in an active-active manner and if an outage in one region occurs, the second region continues to serve user requests.
  * IBM Cloud Monitoring to integrate with Code Engine and forward selected metrics about workloads.
  * IBM Cloud Logs for quick issue detection, performance optimization and strong security compliance.
  * IBM Cloud Activity Tracker to support the configuration of alerts to detect audit issues and send notifications to targeted channels.
2. Provision [IBM Cloud Internet Services](https://github.com/terraform-ibm-modules/terraform-ibm-cis) to configure Domain Name Services(DNS), Global Load Balancer and Web Application Firewall (WAF). 


## Additonal Services
{: #ai-code-engine-app-additional}

You can add additional services to the resilient enterprise architecture. The additional services include:

1. [Security and Compliance Center](https://cloud.ibm.com/catalog/7a4d68b4-cf8b-40cd-a3d1-f49aff526eb3/architecture/deploy-arch-ibm-scc-9423f9bc-1290-4c71-a9ac-01898bfa7ccc-global) for compliance posture of your deployed resources.
