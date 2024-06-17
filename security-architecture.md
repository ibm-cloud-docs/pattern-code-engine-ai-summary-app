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

# Architecture decisions for security
{: #security-decisions}

The following are security architecture decisions for the AI Summarization Using Highly Resilient Serverless Architecture in IBM Cloud® pattern.

## Architecture decisions for data encryption
{: #security-encryption}

| **Architecture decision**      | **Requirement**           | **Options**          | **Decision**          | **Rationale**            |
|------------------------------|-----------------------------|----------------------|-----------------------|--------------------------|
| Data Secrurity (Encryption) | Encrypt all application data in transit to protect it from unauthorized disclosure. | Application-level encryption with TLS | Application-level encryption with TLS | Deployed apps are exposed through HTTPS and IBM Cloud® Code Engine creates and manages the underlying TLS certifications automatically for you. |
{: caption="Table 1. Architecture decisions for data security" caption-side="bottom"}

## Architecture decisions for identity and access management
{: #security-iam}

| **Architecture decision**      | **Requirement**           | **Options**          | **Decision**          | **Rationale**            |
|------------------------------|-----------------------------|----------------------|-----------------------|--------------------------|
| Identity Access & Role Management (IAM) | Securely authenticate users for platform services and control access to resources consistently across IBM Cloud | IBM Cloud® IAM | IBM Cloud® IAM | Use IAM access policies to assign users, service IDs, and trusted profiles access to resources within the IBM Cloud® account. |
{: caption="Table 2. Architecture decisions for IAM" caption-side="bottom"}

## Architecture decisions for application security
{: #security-application}

| Application Security - DDoS        | * Enforce information flow policies and protect the boundaries of the application. \n * Protect against or limit the effects of denial-of-service attacks. | IBM Cloud Internet Services (CIS) | IBM Cloud Internet Services (CIS) | IBM Cloud® Code Engine provides immediate DDoS protection for your application. Code Engine's [DDoS protection](https://cloud.ibm.com/docs/codeengine?topic=codeengine-limits#secure-ddos) is provided by Cloud Internet Services (CIS) at no additional cost. |
{: caption="Table 3. Architecture decisions for application security" caption-side="bottom"}
