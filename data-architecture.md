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

# Architecture decisions for data
{: #data-decisions}

The following are data architecture decisions for the inclusion of watsonx.ai summarization in the AI Summarization Using Highly Resilient Serverless Architecture in IBM Cloud® pattern.

| Architecture decision          | Requirement          | Options    | Decision     | Rationale        |
|-------------------------------------|---------------------------|-------------------|-------------------|-----------------------|
| LLM for summarization in watsonx.ai | A model that can be accessed via API. A model trained to generate summarization. | * IBM-supported custom foundation models from Hugging Face. \n * IBM-developed foundation models of different sizes and architectures, including open-source Granite models and IBM customized Granite models to support enterprise domains and use cases such as RAG. | GRANITE_13B_INSTRUCT_V2 | * IBM Developed foundation model \n * Supports Q&A, summarization, classification, generation, extraction and RAG tasks. \n * Note:  Model selection is a matter of taste and the requirements. Select a generative foundation model that best fits your needs. After you have a short list of models for your use case, systematically test the models by using prompt engineering techniques to see which ones consistently return the desired results. |
{: caption="Table 1. Architecture decisions for data" caption-side="bottom"}
