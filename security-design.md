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

# Security design
{: #security-design}

The [IBM Cloud® Code Engine architecture](https://cloud.ibm.com/docs/codeengine?topic=codeengine-architecture) is built with a security-first mindset.
* IBM Cloud® Code Engine components are [managed and owned by IBM](https://cloud.ibm.com/docs/codeengine?topic=codeengine-responsibilities-ce).
* Customers and their workloads are isolated from each other by using projects, which are based on Kubernetes namespaces.
* Role-based access controls are performed on a resource level to allow only authorized users to perform certain operations on project resources.
* User access is controlled by Cloud Identity and Access Management (IAM).
* Deployed apps are exposed through HTTPS and IBM Cloud® Code Engine creates and manages the underlying TLS certifications automatically for you.
* IBM Cloud® Code Engine provides immediate Layer-4 DDoS protection by Cloud Internet Services (CIS) at no additional cost to you.
