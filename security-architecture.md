---
copyright:
  years: 2024, 2024
lastupdated: "2024-06-24"
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

The following are security architecture decisions for the AI summarization using highly resilient serverless architecture pattern.

## Architecture decisions for data encryption
{: #security-encryption}

| Architecture decision      | Requirement           | Options         | Decision          | Rationale            |
|----------------------------|-----------------------|-----------------|-------------------|----------------------|
| Data Secrurity: Encryption | Encrypt all application data in transit to protect it from unauthorized disclosure. | Application-level encryption with TLS | Application-level encryption with TLS | Deployed apps are exposed through HTTPS and {{site.data.keyword.codeenginefull}} creates and manages the underlying TLS certifications automatically for you. |
{: caption="Table 1. Architecture decisions for data security" caption-side="bottom"}

## Architecture decisions for {{site.data.keyword.iamshort}}
{: #security-iam}

| Architecture decision      | Requirement           | Options         | Decision          | Rationale            |
|----------------------------|-----------------------|-----------------|-------------------|----------------------|
| {{site.data.keyword.iamlong}} (IAM) | Securely authenticate users for platform services and control access to resources consistently across {{site.data.keyword.cloud_notm}} | {{site.data.keyword.iamshort}} | {{site.data.keyword.iamshort}} | Use IAM access policies to assign users, service IDs, and trusted profiles access to resources within the {{site.data.keyword.cloud_notm}} account. |
{: caption="Table 2. Architecture decisions for IAM" caption-side="bottom"}

## Architecture decisions for application security
{: #security-application}

| Application Security - DDoS  | Requirement           | Options         | Decision          | Rationale            |
|------------------------------|-----------------------|-----------------|-------------------|----------------------|
| * Enforce information flow policies and protect the boundaries of the application. \n * Protect against or limit the effects of denial-of-service attacks. | {{site.data.keyword.cis_full}} | {{site.data.keyword.cis_full}} | {{site.data.keyword.codeengineshort}} provides immediate DDoS protection for your application. {{site.data.keyword.codeengineshort}}'s [DDoS protection](/docs/codeengine?topic=codeengine-secure#secure-ddos) is provided by {{site.data.keyword.cis_short}} at no additional cost. |
{: caption="Table 3. Architecture decisions for application security" caption-side="bottom"}
