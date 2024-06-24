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

# Security design
{: #security-design}

The [{{site.data.keyword.codeenginefull}} architecture](/docs/codeengine?topic=codeengine-architecture) is built with a security-first mindset.

* {{site.data.keyword.codeengineshort}} components are [managed and owned by IBM](/docs/codeengine?topic=codeengine-responsibilities-ce).
* Customers and their workloads are isolated from each other by using projects, which are based on Kubernetes namespaces. For more information about projects, see [IBM Code Engine projects](/docs/codeengine?topic=codeengine-manage-project).
* Role-based access controls are performed on a resource level to allow only authorized users to perform certain operations on project resources.
* User access is controlled by {{site.data.keyword.iamlong}}.
* Deployed apps are exposed through HTTPS and {{site.data.keyword.codeengineshort}} creates and manages the underlying TLS certifications automatically for you.
* {{site.data.keyword.codeengineshort}} provides immediate Layer-4 DDoS protection by {{site.data.keyword.cis_full}} at no additional cost to you.