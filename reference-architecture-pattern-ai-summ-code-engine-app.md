---
copyright:
  years: 2024, 2024
lastupdated: "2024-06-19"
subcollection: pattern-code-engine-ai-summary-app
keywords:
version: 1.0
content-type: reference-architecture
authors:
  - name: "Tushar Vaghode"
    email: "Tushar.Vaghode@ibm.com"
  - name: "Sharon Wheless"
    email: "sharon.wheless@us.ibm.com"
---

{{site.data.keyword.attribute-definition-list}}

# AI summarization using highly resilient serverless architecture in {{site.data.keyword.cloud_notm}}
{: #architecture}
{: toc-content-type="reference-architecture"}
{: toc-version="1.0"}

The "AI summarization using highly resilient serverless architecture pattern in {{site.data.keyword.cloud}}" describes an internet-facing web application deployed using {{site.data.keyword.codeenginefull}} serverless platform in two {{site.data.keyword.cloud_notm}} regions. By provisioning application in two regions user requests are served in an active-active manner and in case of an outage in one region the second region continues to serve user requests.


## Architecture diagram
{: #architecture-diagram}

![Network Diagram](images/code-engine-app-pattern-arch-diagram.svg){: caption="Figure 1. AI Summarization Using Highly Resilient Serverless Architecture in {{site.data.keyword.cloud_notm}} solution architecture" caption-side="bottom"}

* {{site.data.keyword.codeengineshort}} abstracts the operational burden of building, deploying, and managing workloads in Kubernetes so that developers can focus on what matters most to them: the source code.

* By default, {{site.data.keyword.codeengineshort}} applications are deployed within a single zone of a region. If a failure of the hosting zone occurs, the workload is automatically re-created in one of the remaining zones of that region, providing high availability at regional level.

* This pattern provides additional protection by provisioning application in two regions of {{site.data.keyword.cloud_notm}}.

* {{site.data.keyword.registrylong}} provides a multi-tenant private image [registry](/docs/Registry?topic=Registry-registry_overview#overview_elements_registry) that is used to store [container images](/docs/Registry?topic=Registry-registry_overview#overview_elements_container_image). {{site.data.keyword.codeengineshort}} application configuration points to this container registry for image reference.

* {{site.data.keyword.monitoringfull}} service is setup to monitor your {{site.data.keyword.codeengineshort}} workloads. {{site.data.keyword.codeengineshort}} forwards selected information about your workloads to the monitoring platform so that you can monitor specific metrics such as requests, revisions and durations, with this monitoring being configurable.

* An {{site.data.keyword.loganalysislong}} service instance is also setup where {{site.data.keyword.codeengineshort}} application logs are forwarded to for help with troubleshoot issues.

* This pattern uses a global content delivery network (CDN) called [{{site.data.keyword.cis_full}}](/docs/cis?topic=cis-getting-started) and its global load balancer capability to provide global endpoint for the web application.

* Origin pools are created for each region application endpoints, to which traffic is intelligently routed to when attached to a global load balancer as above.

* A health check is created to gain insight into the availability of pools so that traffic is always routed to healthy ones making the app highly available.

* By setting Traffic Steering to ‘Geo’ the load balancer directs incoming traffic to origin pools based on the client’s region or point of presence.

* {{site.data.keyword.codeengineshort}} provides immediate DDoS (Distributed Denial of Service) protection for your application. {{site.data.keyword.codeengineshort}}'s DDoS protection is provided by {{site.data.keyword.cis_short}} at no additional cost. DDoS protection covers System Interconnection (OSI) Layer 3 and Layer 4 (TCP/IP) protocol attacks. Layer 7 protection is implemented by configuring WAF (Web Application Firewall) ruleset sensitivity and response behavior, adding rate limiting and adding firewall rules. WAF is also included as part of {{site.data.keyword.cis_short}} at no additional charge.


## Design scope
{: #design-scope}

Following the [Architecture Framework](/docs/architecture-framework?topic=architecture-framework-taxonomy), the "AI summarization using highly resilient serverless architecture pattern in {{site.data.keyword.cloud_notm}}" pattern covers design considerations and architecture decisions for the following aspects and domains:

* **Data:** Artificial Intelligence

* **Compute:** Serverless

* **Networking:** Isolation, Cloud Native Connectivity, Load Balancing, DNS

* **Security:** Data Security, Identity and Access, Application Security, Infrastructure Security

* **DevOps:** Code Repository

* **Resiliency:** High Availability, Disaster Recovery

* **Service management:** Monitoring, Logging, Auditing

![Design Scope](images/heat-map-template-codeengine-app.svg){: caption="Figure 2. AI Summarization Using Highly Resilient Serverless Architecture in {{site.data.keyword.cloud_notm}} design scope" caption-side="bottom"}

The Architecture Framework provides a consistent approach to design cloud solutions by addressing requirements across a set of "aspects" and "domains", which are technology-agnostic architectural areas that need to be considered for any enterprise solution. See [Introduction to the architecture framework](/docs/architecture-framework?topic=architecture-framework-intro) for more details.


## Requirements
{: #requirements}

The following represents a baseline set of requirements that are applicable to most clients and critical to successful "AI summarization using highly resilient serverless architecture pattern in {{site.data.keyword.cloud_notm}}" deployment.

| Aspect             |  Requirement                                                          |
|--------------------|-----------------------------------------------------------------------|
| Data               | Provide a way to perform summarization of input.                      |
| Compute            | Provide different levels of CPU and memory options to match the type of workloads.    |
| Network            | Provide connectivity to web application from public internet or privately in {{site.data.keyword.cloud_notm}} private network by using {{site.data.keyword.vpe_full}}. \n Provide isolation with the ability to deploy application with different level of visibility such as at project level, public or private.     |
| Security           | Grant access to other users for {{site.data.keyword.codeengineshort}} by using {{site.data.keyword.iamlong}}. \n Provide DDoS and Layer-7 attack protection for web application. \n Provide a method to store and access sensitive configuration information, such as secrets, passwords, and keys.   |
| DevOps             | Provide private image repository with vulnerability scanning capability                     |
| Resiliency         | Deploy application across multiple regions to make it resilient to regional failures.       |
| Service management | Provide Health and System Monitoring with ability to monitor and correlate performance metrics, events and provide alerting across applications and infrastructure. \n Ability to diagnose issues and exceptions and identify error source. Get insight into the performance of your workloads   |
{: caption="Table 1. AI Summarization Using Highly Resilient Serverless Architecture in {{site.data.keyword.cloud_notm}} requirements" caption-side="bottom"}


## Components
{: #components}

| Aspect            | Component                           | How the component is used           |
|-------------------|-------------------------------------|-------------------------------------|
| Data                   | [IBM watsonx.ai](https://www.ibm.com/watsonx){: external}       | Summarization will be performed by the IBM Developed GRANITE model, hosted and used by IBM watsonx.ai, bringing together new generative AI capabilities powered by foundation models and traditional machine learning (ML) into a powerful studio spanning the AI lifecycle.       |
| Compute                | [{{site.data.keyword.codeengineshort}}](/docs/codeengine?topic=codeengine-ceapplications) | Abstracts the operational burden of building, deploying, and managing workloads in Kubernetes               |
| Networking             | [Global Load Balancer](/docs/cis?topic=cis-configure-glb)  | Public Load balancing of web server traffic across regions     |
| | [{{site.data.keyword.dns_full}}](/docs/dns-svcs?topic=dns-svcs-about-dns-services)  | The domain Name System (DNS) to associate human-friendly domain names with IP addresses     |
| Security           |  [Secrets](/docs/codeengine?topic=codeengine-secret)      | A secret provides a method to include sensitive configuration information, such as passwords or SSH keys, to your deployment. By referencing values from your secret, you can decouple sensitive information from your deployment to keep your app, function, or job portable.        |
| | [{{site.data.keyword.iamshort}}](/docs/account?topic=account-cloudaccess)         | {{site.data.keyword.iamshort}}         |
| | [{{site.data.keyword.cis_short}}](/docs/cis?topic=cis-getting-started)                   | {{site.data.keyword.codeengineshort}} provides immediate DDoS protection for your application. DDoS protection covers System Interconnection (OSI) Layer 3 and Layer 4 (TCP/IP) protocol attacks, but not Layer 7 attacks. CIS provides capability to further add security against Layer 7 attacks by configuring WAF rulesets and WAF firewall rules. |
| Resiliency    | [{{site.data.keyword.cis_short}}](/docs/cis?topic=cis-getting-started)     | For highly resilient application, {{site.data.keyword.cis_short}} Global Load Balancer provides your application a global endpoint. The Origin Pools serves as a backend target to the Load Balancer. Origin Pools are setup for each of the region where application is deployed.  |
| Service management | [{{site.data.keyword.monitoringfull_notm}}](/docs/monitoring?topic=monitoring-about-monitor)    | {{site.data.keyword.monitoringfull_notm}} service to monitor {{site.data.keyword.codeengineshort}} workloads. {{site.data.keyword.codeengineshort}} forwards selected information about your workloads to Monitoring so that you can monitor specific metrics such as requests, revisions, and duration.   |
| | [{{site.data.keyword.loganalysisshort}}](/docs/log-analysis?topic=log-analysis-getting-started)              | {{site.data.keyword.codeengineshort}} apps, jobs, functions, or builds in the console with logging enabled, logs are forwarded to an {{site.data.keyword.loganalysisshort}} service where they are indexed, enabling full-text search through all generated messages and convenient querying based on specific fields. |
| | [{{site.data.keyword.cloudaccesstraillong}}](/docs/atracker?topic=atracker-about)   | View, manage, and audit user-initiated activities made in your {{site.data.keyword.codeengineshort}} service instance by using the {{site.data.keyword.cloudaccesstrailshort}} service.      |
{: caption="Table 2. AI Summarization Using Highly Resilient Serverless Architecture in {{site.data.keyword.cloud_notm}} components" caption-side="bottom"}
