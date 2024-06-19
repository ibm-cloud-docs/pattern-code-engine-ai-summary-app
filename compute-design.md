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

# Compute design
{: #compute-design}

{{site.data.keyword.codeenginefull}} provides various combinations of compute and memory size for running applications, jobs, and functions on serverless workload.
* A combination is picked based on workload requirements i.e. if workload is compute-intensive, memory-intensive, or balanced. See [Supported memory and CPU combinations](/docs/codeengine?topic=codeengine-mem-cpu-combo) and the defaults for apps, jobs, and functions.
* The total combination for all the app instances, running job instances, and running build instances cannot exceed 128 vCPU and 512GB of memory within a project.
* See [Project Quotas](/docs/codeengine?topic=codeengine-limits#project_quotas) for other limits.
