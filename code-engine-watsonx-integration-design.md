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

# Integrating IBM Cloud® Code Engine with watsonx
{: #code-engine-watsonx-integration-design}

![Diagram showing integration with watsonx.ai](/images/watsonx-codeengine-integration-diagram.svg){: caption="Figure 3. Integrating watsonx.ai with IBM Cloud® Code Engine" caption-side="bottom"}

* The Summarization service hosted in IBM Cloud® Code Engine as web application takes input data from a user and is passed to IBM watsonx.ai as a ‘Prompt’.
* The model-ID and the parameters are passed to the watsonx.ai, containing the LLM being used for summarization.
* Summarization response from the model is displayed in the web application as output.
* IBM Cloud® infrastructure handles scaling and management of the service, automatically scaling it based on demand.
