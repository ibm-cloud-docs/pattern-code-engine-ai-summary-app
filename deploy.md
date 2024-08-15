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


## Provision Architecture
{: #ai-code-engine-app-provision}

1. Add the [watsonx.ai]( https://github.com/terraform-ibm-modules/terraform-ibm-watsonx-saas-da) service to deploy Watson Studio, Watson Machine Learning and COS. 
2. Provision [Code Engine](https://github.com/terraform-ibm-modules/terraform-ibm-code-engine/tree/main) to create the highly resilient serverless architecture to housing an internet-facing web application. By provisioning an application in two regions, user requests are served in an active-active manner and if an outage in one region occurs, the second region continues to serve user requests.
3. Provision [IBM Cloud Internet Services](https://github.com/terraform-ibm-modules/terraform-ibm-cis) to configure Domain Name Services(DNS), Global Load Balancer and Web Application Firewall (WAF). 
4. Provision [IBM Cloud Monitoring](https://github.com/terraform-ibm-modules/terraform-ibm-observability-instances/tree/main/modules/cloud_monitoring) to integrate with Code Engine and forward selected metrics about workloads.
5. Provision [IBM Cloud Logs](https://github.com/terraform-ibm-modules/terraform-ibm-observability-instances/tree/main/modules/cloud_logs) for quick issue detection, performance optimization and strong security compliance.
6. Provision [IBM Cloud Activity Tracker](https://github.com/terraform-ibm-modules/terraform-ibm-observability-instances/tree/main/modules/activity_tracker) to support the configuration of alerts to detect audit issues and send notifications to targeted channels.





## Additonal Services
{: #ai-code-engine-app-additional}

You can add additional services to the resilient enterprise architecture. The additional services include:

1. [IBM Cloud Observability](https://cloud.ibm.com/catalog/7a4d68b4-cf8b-40cd-a3d1-f49aff526eb3/architecture/deploy-arch-ibm-observability-a3137d28-79e0-479d-8a24-758ebd5a0eab-global) for provisioning and configuring logging, monitoring, and activity tracking.
2. [IBM Cloud Event Notifications](https://cloud.ibm.com/catalog/7a4d68b4-cf8b-40cd-a3d1-f49aff526eb3/architecture/deploy-arch-ibm-event-notifications-c7ac3ee6-4f48-4236-b974-b0cd8c624a46-global) for a high-throughput message bus that is built with Apache Kafka.
3. [Security and Compliance Center](https://cloud.ibm.com/catalog/7a4d68b4-cf8b-40cd-a3d1-f49aff526eb3/architecture/deploy-arch-ibm-scc-9423f9bc-1290-4c71-a9ac-01898bfa7ccc-global) for compliance posture of your deployed resources.
4. [IBM Storage Protect](https://cloud.ibm.com/catalog/content/SPonIBMCloud-20c54034-d319-48c0-beb6-0b4adc54265c-global?catalog_query=aHR0cHM6Ly9jbG91ZC5pYm0uY29tL2NhdGFsb2c%2Fc2VhcmNoPXN0b3JhZ2UlMjUyMHByb3RlY3Qjc2VhcmNoX3Jlc3VsdHM%3D) for data protection operations.
