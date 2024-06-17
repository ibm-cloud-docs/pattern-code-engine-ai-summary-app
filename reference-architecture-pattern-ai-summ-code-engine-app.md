---
copyright:
  years: 2023
lastupdated: "2024-06-11"
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

# AI Summarization Using Highly Resilient Serverless Architecture in IBM Cloud
{: #architecture}
{: toc-content-type="reference-architecture"}
{: toc-version="1.0"}

The “AI Summarization Using Highly Resilient Serverless Architecture in IBM Cloud” pattern describes an internet-facing web application deployed using IBM Cloud Code Engine serverless platform in two IBM Cloud regions. By provisioning application in two regions user requests are served in an active-active manner and in case of an outage in one region the second region continues to serve user requests.


## Architecture diagram
{: #architecture-diagram}

![Network Diagram](/images/code-engine-app-pattern-arch-diagram.svg){: caption="Figure 1. AI Summarization Using Highly Resilient Serverless Architecture in IBM Cloud® solution architecture" caption-side="bottom"}

* IBM Cloud® Code Engine abstracts the operational burden of building, deploying, and managing workloads in Kubernetes so that developers can focus on what matters most to them: the source code.

* By default, IBM Cloud® Code Engine applications are deployed within a single zone of a region. If a failure of the hosting zone occurs, the workload is automatically re-created in one of the remaining zones of that region, providing high availability at regional level.

* This pattern provides additional protection by provisioning application in two regions of IBM Cloud®.

* IBM Cloud® Container Registry provides a multi-tenant private image [registry](https://cloud.ibm.com/docs/Registry?topic=Registry-registry_overview#overview_elements_registry) that is used to store [container images](https://cloud.ibm.com/docs/Registry?topic=Registry-registry_overview#overview_elements_container_image). IBM Cloud® Code Engine application configuration points to this container registry for image reference.

* IBM Cloud® Monitoring service is setup to monitor your IBM Cloud® Code Engine workloads. IBM Cloud® Code Engine forwards selected information about your workloads to the monitoring platform so that you can monitor specific metrics such as requests, revisions and durations, with this monitoring being configurable.

* An IBM Log Analysis service instance is also setup where IBM Cloud® Code Engine application logs are forwarded to for help with troubleshoot issues.

* This pattern uses a global content delivery network (CDN) called [IBM Cloud Internet Services](https://cloud.ibm.com/docs/cis?topic=cis-getting-started) and its global load balancer capability to provide global endpoint for the web application.

* Origin pools are created for each region application endpoints, to which traffic is intelligently routed to when attached to a global load balancer as above.

* A health check is created to gain insight into the availability of pools so that traffic is always routed to healthy ones making the app highly available.

* By setting Traffic Steering to ‘Geo’ the load balancer directs incoming traffic to origin pools based on the client’s region or point of presence.

* IBM Cloud® Code Engine provides immediate DDoS (Distributed Denial of Service) protection for your application. IBM Cloud® Code Engine 's DDoS protection is provided by Cloud Internet Services (CIS) at no additional cost. DDoS protection covers System Interconnection (OSI) Layer 3 and Layer 4 (TCP/IP) protocol attacks. Layer 7 protection is implemented by configuring WAF (Web Application Firewall) ruleset sensitivity and response behavior, adding rate limiting and adding firewall rules. WAF is also included as part of CIS at no additional charge.


## Design scope
{: #design-scope}

Following the [Architecture Framework](https://cloud.ibm.com/docs/architecture-framework?topic=architecture-framework-taxonomy), the AI Summarization Using Highly Resilient Serverless Architecture in IBM Cloud pattern covers design considerations and architecture decisions for the following aspects and domains:

* **Data: Artificial Intelligence**

* **Compute:** Serverless

* **Networking:** Isolation, Cloud Native Connectivity, Load Balancing, DNS

* **Security:** Data Security, Identity and Access, Application Security, Infrastructure Security

* **DevOps:** Code Repository

* **Resiliency:** High Availability, Disaster Recovery

* **Service management:** Monitoring, Logging, Auditing

![Design Scope](/images/heat-map-template-codeengine-app.svg){: caption="Figure 2. AI Summarization Using Highly Resilient Serverless Architecture in IBM Cloud® design scope" caption-side="bottom"}

The Architecture Framework provides a consistent approach to design cloud solutions by addressing requirements across a set of "aspects" and "domains", which are technology-agnostic architectural areas that need to be considered for any enterprise solution. See [Introduction to the architecture framework](https://cloud.ibm.com/docs/architecture-framework?topic=architecture-framework-intro) for more details.


## Requirements
{: #requirements}

The following represents a baseline set of requirements that are applicable to most clients and critical to successful AI Summarization Using Highly Resilient Serverless Architecture in an IBM Cloud®deployment.

| **Aspect**         |**Requirement**                                                        |
|--------------------|-----------------------------------------------------------------------|
| Data               | Provide a way to perform summarization of input.                      |
| Compute            | Provide different levels of CPU and memory options to match the type of workloads.    |
| Network            | Provide connectivity to web application from public internet or privately in IBM Cloud private network by using VPE. \n * Provide isolation with the ability to deploy application with different level of visibility such as at project level, public or private.     |
| Security           | Grant access to other users for IBM Cloud® Code Engine by using Cloud Identity and Access Management (IAM). \n * Provide DDoS and Layer-7 attack protection for web application. \n * Provide a method to store and access sensitive configuration information, such as secrets, passwords, and keys.   |
| DevOps             | Provide private image repository with vulnerability scanning capability                     |
| Resiliency         | Deploy application across multiple regions to make it resilient to regional failures.       |
| Service management | Provide Health and System Monitoring with ability to monitor and correlate performance metrics, events and provide alerting across applications and infrastructure. \n * Ability to diagnose issues and exceptions and identify error source. Get insight into the performance of your workloads   |
{: caption="Table 1. AI Summarization Using Highly Resilient Serverless Architecture in IBM Cloud® requirements" caption-side="bottom"}


## Components
{: #components}

| **Aspect**             | **Component**                                        | **How the component is used**                                                             |
|------------------------|------------------------------------------------------|-------------------------------------------------------------------------------------------|
| Data                   | [IBM watsonx.ai](https://www.ibm.com/watsonx)        | Summarization will be performed by the IBM Developed GRANITE model, hosted and used by IBM watsonx.ai, bringing together new generative AI capabilities powered by foundation models and traditional machine learning (ML) into a powerful studio spanning the AI lifecycle.       |
| Compute                | [IBM Cloud® Code Engine Application](https://cloud.ibm.com/docs/codeengine?topic=codeengine-ceapplications) | Abstracts the operational burden of building, deploying, and managing workloads in Kubernetes                                                                                                                             |
| Networking             | [Global Load Balancer](https://cloud.ibm.com/docs/cis?topic=cis-configure-glb)  | Public Load balancing of web server traffic across regions     |
| | [DNS Services](https://cloud.ibm.com/docs/dns-svcs?topic=dns-svcs-about-dns-services)  | The domain Name System (DNS) to associate human-friendly domain names with IP addresses     |
| Security           | Code IBM Cloud® Code Engine Secret                       | A secret provides a method to include sensitive configuration information, such as passwords or SSH keys, to your deployment. By referencing values from your secret, you can decouple sensitive information from your deployment to keep your app, function, or job portable.        |
| | [IAM](https://cloud.ibm.com/docs/account?topic=account-cloudaccess)         | IBM Cloud® Identity & Access Management                                                   |
| | [Cloud Internet Services (CIS)](https://cloud.ibm.com/docs/cis?topic=cis-getting-started)                   | IBM Cloud® Code Engine provides immediate DDoS protection for your application. DDoS protection covers System Interconnection (OSI) Layer 3 and Layer 4 (TCP/IP) protocol attacks, but not Layer 7 attacks. CIS provides capability to further add security against Layer 7 attacks by configuring WAF rulesets and WAF firewall rules. |
| Resiliency    | [Cloud Internet Services (CIS)](https://cloud.ibm.com/docs/cis?topic=cis-getting-started)                   | For highly resilient application, Cloud Internet Services (CIS) Global Load Balancer provides your application a global endpoint. The Origin Pools serves as a backend target to the Load Balancer. Origin Pools are setup for each of the region where application is deployed.  |
| Service management | [IBM Cloud® Monitoring](https://cloud.ibm.com/docs/monitoring?topic=monitoring-about-monitor)               | IBM Cloud® Monitoring service to monitor IBM Cloud® Code Engine workloads. IBM Cloud® Code Engine forwards selected information about your workloads to Monitoring so that you can monitor specific metrics such as requests, revisions, and duration.   |
| | [IBM Log Analysis](https://cloud.ibm.com/docs/log-analysis?topic=log-analysis-getting-started)              | IBM Cloud® Code Engine apps, jobs, functions, or builds in the console with logging enabled, logs are forwarded to an IBM Log Analysis service where they are indexed, enabling full-text search through all generated messages and convenient querying based on specific fields. |
| | [Activity Tracker Event Routing](https://cloud.ibm.com/docs/atracker?topic=atracker-about)                  | View, manage, and audit user-initiated activities made in your IBM Cloud® Code Engine service instance by using the IBM Cloud Activity Tracker service.           |
{: caption="Table 2. AI Summarization Using Highly Resilient Serverless Architecture in IBM Cloud® components" caption-side="bottom"}
