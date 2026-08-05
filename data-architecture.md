---
copyright:
  years: 2024, 2026
lastupdated: "2026-08-05"
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

The following are data architecture decisions for the inclusion of watsonx.ai summarization in the AI summarization using highly resilient serverless architecture pattern.

| Architecture decision          | Requirement          | Options    | Decision     | Rationale        |
|-------------------------------------|---------------------------|-------------------|-------------------|-----------------------|
| LLM for summarization in watsonx.ai | A model that can be accessed via API. A model trained to generate summarization. | * IBM-supported custom foundation models from Hugging Face. \n * IBM-developed foundation models of different sizes and architectures, including open-source Granite models and IBM customized Granite models to support enterprise domains and use cases such as RAG. | `ibm/granite-3-8b-instruct` | * IBM-developed Granite 3.x foundation model. \n * Supports Q&A, summarization, classification, generation, extraction, and RAG tasks. \n * Model selection depends on your requirements. Select a generative foundation model that best fits your needs from the current [watsonx.ai model catalog](https://www.ibm.com/products/watsonx-ai/foundation-models){: external}. After you have a short list of models for your use case, systematically test the models by using prompt engineering techniques to see which ones consistently return the desired results. |
{: caption="Architecture decisions for data" caption-side="bottom"}
