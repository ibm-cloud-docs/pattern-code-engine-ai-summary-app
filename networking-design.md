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

# Network design
{: #network-design}

All IBM Cloud® Code Engine projects offer integration with IBM Cloud® Virtual Private Endpoints (VPE) for Virtual Private Cloud (VPC). This support gives you the ability to connect from your VPC network to IBM Cloud® Code Engine applications or functions by using the IP addresses of your choosing, which are allocated from a subnet within your VPC.

With IBM Cloud® Code Engine, you can use the following types of VPEs:

* [Virtual Private Endpoints to manage project resources](https://cloud.ibm.com/docs/codeengine?topic=codeengine-regions#endpoints-project). There is one static VPE per region.
* [Virtual Private Endpoints to access applications](https://cloud.ibm.com/docs/codeengine?topic=codeengine-regions#endpoints-app). There is one VPE per IBM Cloud® Code Engine project. All apps within the project can be accessed by using this VPE.

Private endpoints provide a connection to your project resources, applications, or functions on the IBM Cloud® Private network. When you connect through a virtual private endpoint, all traffic is routed to hardware that is dedicated to IBM Cloud® Code Engine applications and remains on the IBM Cloud Private network. There are no additional charges for all traffic to and from this endpoint on the condition that the traffic remains in IBM Cloud®.

An IBM Cloud® Code Engine project is automatically configured with both a public and a virtual private endpoint.

You can control the [visibility](https://cloud.ibm.com/docs/codeengine?topic=codeengine-application-workloads#optionsvisibility) of IBM Cloud® Code Engine applications and specify whether to expose the application or functions to public or private endpoints. An application or function that is configured for the private network can be accessed through the VPE or by other Code Engine applications or functions. Applications or functions that are accessed through the VPE do not leave the IBM network and stay within the IBM Cloud® network.
