---
copyright:
  years: 2024, 2024
lastupdated: "2024-06-18"
subcollection: pattern-code-engine-ai-summary-app
keywords:
authors:
  - name: "Tushar Vaghode"
    email: "Tushar.Vaghode@ibm.com"
  - name: "Sharon Wheless"
    email: "sharon.wheless@us.ibm.com"
---

{{site.data.keyword.attribute-definition-list}}

# Storage design
{: #storage-design}

IBM Cloud® Code Engine uses ephemeral storage where storage size is bounded by memory size.

* The ephemeral storage in IBM Cloud® Code Engine cannot exceed the default value of 0.4 GB (400 MB) or the configured value for memory.
* If you need more than the default for ephemeral storage, you must increase your memory according to the valid combinations of vCPU and memory.
* The total combination for all the app instances, running job instances, and running build instances cannot exceed 512 GB of ephemeral storage within a project.
* See [Project Quotas](/docs/codeengine?topic=codeengine-limits#project_quotas) for other limits.
