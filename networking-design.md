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

# Network design
{: #network-design}

All {{site.data.keyword.codeenginefull}} projects offer integration with {{site.data.keyword.vpe_full}}. This support gives you the ability to connect from your {{site.data.keyword.vpc_full}} network to {{site.data.keyword.codeengineshort}} applications or functions by using the IP addresses of your choosing, which are allocated from a subnet within your {{site.data.keyword.vpc_short}}.

With {{site.data.keyword.codeengineshort}}, you can use the following types of {{site.data.keyword.vpe_short}}:

* [Virtual Private Endpoints to manage project resources](/docs/codeengine?topic=codeengine-regions#endpoints-project). There is one static VPE per region.
* [Virtual Private Endpoints to access applications](/docs/codeengine?topic=codeengine-regions#endpoints-app). There is one VPE per {{site.data.keyword.codeengineshort}} project. All apps within the project can be accessed by using this VPE.

Private endpoints provide a connection to your project resources, applications, or functions on the {{site.data.keyword.cloud}} Private network. When you connect through a {{site.data.keyword.vpe_short}}, all traffic is routed to hardware that is dedicated to {{site.data.keyword.codeengineshort}} applications and remains on the {{site.data.keyword.cloud_notm}} Private network. There are no additional charges for all traffic to and from this endpoint on the condition that the traffic remains in {{site.data.keyword.cloud_notm}}.

An {{site.data.keyword.codeengineshort}} project is automatically configured with both a public and a virtual private endpoint.

You can control the [visibility](/docs/codeengine?topic=codeengine-application-workloads#optionsvisibility) of {{site.data.keyword.codeengineshort}} applications and specify whether to expose the application or functions to public or private endpoints. An application or function that is configured for the private network can be accessed through the {{site.data.keyword.vpe_short}} or by other {{site.data.keyword.codeengineshort}} applications or functions. Applications or functions that are accessed through the {{site.data.keyword.vpe_short}} do not leave the {{site.data.keyword.cloud_notm}} network and stay within the {{site.data.keyword.cloud_notm}} network.
