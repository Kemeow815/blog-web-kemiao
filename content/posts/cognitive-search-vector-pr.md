---
title: cognitive-search-vector-pr
date: 2023-05-27T12:17:08+08:00
draft: False
featuredImage: https://wallpaperhub.app/api/v1/get/12173/0/1080p
featuredImagePreview: https://wallpaperhub.app/api/v1/get/12173/0/1080p
---

# [Azure/cognitive-search-vector-pr](https://github.com/Azure/cognitive-search-vector-pr)

# Vector search (private preview) - Azure Cognitive Search

**DISCLAIMER**
Preview functionality is provided under [Supplemental Terms of Use](https://azure.microsoft.com/support/legal/preview-supplemental-terms/), without a service level agreement, and isn't recommended for production workloads.

Welcome to the private preview of the vector search feature in Azure Cognitive Search! When done correctly, vector search is a proven technique for significantly increasing the semantic relevance of search results. By participating in this private preview, you can help us improve our implementation of this feature by [providing your feedback and suggestions](#contact-us).

Cognitive Search can index and store vectors, but it doesn't generate them out of the box. The documents that you push to your search service must contain vectors within the payload. Alternatively, you can use the Indexer to pull vectors from your data sources such as Blob Storage JSON files or CSVs. You can also use a Custom Skill to generate embeddings as part of the AI Enrichment process.

To create vectorized data, you can use any embedding model, but we recommend [Azure OpenAI Embeddings models](https://learn.microsoft.com/azure/cognitive-services/openai/how-to/embeddings?tabs=console) or [Cognitive Services Vision Image Retrieval API](https://learn.microsoft.com/azure/cognitive-services/computer-vision/how-to/image-retrieval) for images. The Python and .NET samples in this repository call Azure OpenAI to generate text embeddings. You can request [access to Azure OpenAI](https://aka.ms/oai/access) in your Azure subscription to use the demo samples we've provided.

## Pricing

This private preview requires billable resources. You'll need to cover the cost of running Azure Cognitive Search, as well as Azure OpenAI if you choose to use their embedding models.

- [Azure Cognitive Search pricing](https://azure.microsoft.com/pricing/details/search/#pricing) for a tier (SKU) that's Basic or higher (see also [Plan and manage costs](https://learn.microsoft.com/azure/search/search-sku-manage-costs)).

- [Azure OpenAI pricing](https://azure.microsoft.com/pricing/details/cognitive-services/openai-service/) for metered usage of embedding models.

## Get started

For this private preview, we've enabled vector search support in all Azure Cognitive Search regions, on all tiers except Free.

You can use an existing billable search service, but you must create a new index. Be sure to review [preview limitations](#private-preview-limitations) and [storage and float limits](#storage-and-float-limits).

### 1 - Setup

If you fork or clone this repo, help us protect the private preview status of this feature by making sure your forked and cloned repositories remain private.

To verify feature availability, issue a REST call that creates a new vector search index using the new preview REST API. A successful response confirms feature availability.

```http
POST https://{{YOUR-SEARCH-SERVICE-NAME}}.search.windows.net/indexes?api-version=2023-07-01-Preview
  Content-Type: application/json
  api-key: {{YOUR-ADMIN-API-KEY}}
    {
      "name": "do-i-have-vector-search",
      "fields": [
        {
          "name": "id",
          "type": "Edm.String",
          "key": true
        },
        {
          "name": "MyVectorField",
          "type": "Collection(Edm.Single)",
          "searchable": true,
          "filterable": false,
          "sortable": false,
          "facetable": false,
          "retrievable": true,
          "analyzer": "",
          "dimensions": 5,
          "vectorSearchConfiguration": "vectorConfig"
        }
      ],
        "vectorSearch": {
            "algorithmConfigurations": [
                {
                    "name": "vectorConfig",
                    "kind": "hnsw"
                }
            ]
        }
    }
```

### 2 - Demos

We provide multiple demo solutions to get you started.

| Sample             | Purpose                                                                      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| ------------------ | ---------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| .NET               | Creates vector representations of images or text                             | A .NET Console App that calls OpenAI to create vectorized data. We used this console app to create the sample data for the demo index. You can revise your copy of the notebook to test vector search with other data and your own schemas. See the [sample readme](/demo-dotnet/readme.md) for instructions on console app setup.                                                                                                                                                                                                                                                                                                                     |
| Python             | Creates vector representations of images or text                             | A notebook that calls OpenAI to create vectorized data. We used this notebook to create the sample data for the demo index. You can revise your copy of the notebook to test vector search with other data and your own schemas. See the [sample readme](/demo-python/readme.md) for instructions on notebook setup.                                                                                                                                                                                                                                                                                                                                   |
| JavaScript         | Creates vector representations of images or text                             | A node.js version of the Python sample. See the [sample readme](/demo-javascript/readme.md) for instructions on sample setup.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Postman collection | Create, load, and query a search index that contains text and vector fields. | A collection of REST API calls to an Azure Cognitive Search instance. The requests in this collection include an index schema, sample documents, and sample queries. The collection is documented in [Quickstart: Vector search](/docs/vector-search-quickstart.md). Each query demonstrates key scenarios. <p>Use the [Postman app](https://www.postman.com/downloads/) and import the collection.</p> <p>Set collection variables to provide your search service URI and admin key</p> If you're unfamiliar with Postman, see this [Postman/REST quickstart for Cognitive Search](https://learn.microsoft.com/azure/search/search-get-started-rest). |

## 3 - Quickstart

For your first experience with the end-to-end workflow, begin with the [vector search quickstart](/docs/vector-search-quickstart.md). It takes you through a series of HTTP requests that create, load, and query an index. You'll find combinations of vector-only search, hybrid search, vectors with filters, and so on.

Sample data can be found in the Upload Docs request. It consists of 108 documents about Azure services and includes vectorized data created from demo code.

1. Import the collection into Postman.
1. In collection variables, provide your search service URI, an admin API key, an index name.
1. Run each request in sequence using API version: **2023-07-01-Preview**.

## 4 - Try it with your data

When you're ready to extend the quickstart or adapt the collection to you data, you'll need to:

- Create vector representations for specific fields. Choose fields that have semantic value, such as descriptions or summaries. You can useany of the demos currently available in .NET, Python, and JavaScript to generate embeddings. To use the demos as-is, you'll need [Azure OpenAI](https://aka.ms/oai/access) in your subscription.

- Create, load, and query your custom index. Use the **2023-07-01-Preview** REST API for these operations. We recommend Postman or a similar tool for proof-of-concept testing.

## Private preview limitations

- This feature is only available via indexes and queries that target **2023-07-01-Preview** REST API. There is no Portal support at this time. If you view or query a search index that has vector fields, the portal treats them as strings and any queries will be scored using BM25.
- You can either create a new index or add a vector field to an existing index but you must target the preview API.
- Your search service must be a billable tier. If the search service is already billable, there is no additional charge for the vector search feature.

- Service and subscription limits haven't been finalized, but the [API request limits](https://learn.microsoft.com/azure/search/search-limits-quotas-capacity#api-request-limits) do apply. Request payloads cannot exceed 8K for URIs or 16 MB for the request body. The following additional limits apply to this preview:

  - Maximum number of vectors fields per index: Subject to [existing index field limits](https://learn.microsoft.com/en-us/azure/search/search-limits-quotas-capacity#index-limits). However, please keep in mind the float limit and index size limitations per SKU.

  - Maximum number of dimensions: 2048

- Index definitions are currently subject to the following limitations:

  - Vector fields with complex types or collections of complex types aren't supported.

- Query definitions are currently subject to these limitations:

  - POST verbs are required. Don't use GET.
  - Multi-field vector queries aren't supported. Specifically, you can't set "vector.fields" property to multiple vector fields. For example, the Postman collection has vector fields named TitleVector and ContentVector. Your query can include TitleVector or ContentVector, but not both.
  - Multi-vector queries aren't supported. A search request can carry a single vector query.
  - Sorting ($orderby) and pagination ($skip) are not supported for hybrid queries.
  - Facets ($facet) and count ($count) are not supported for vector and hybrid queries.

- There is no official public documentation or samples beyond what you'll find in this private repository. Please contact us with any questions or concerns.

## Storage and vector index size limits

The size of your vector index in memory is restricted based on the reserved memory for the chosen SKU. It is calculated **per partition** and is a hard limit. The storage and vector index size quotas are not separate quotas; vector indexes share the same underlying storage quota. For example, if storage quota is exhausted but there is remaining vector quota, you won't be able to index any more documents, regardless if they're vector documents, until you scale up in partitions or delete some documents.

The limits are set conservatively and are preliminary during this period. We are still investigating performance if the limits are raised.

An approximate translation into the number of floating point numbers is provided. **This is not the same number as vector dimensionality.** The dimensionality of a vector field affects how many floating point numbers are contained in one vector embedding.

For example, using the most popular Azure OpenAI model, `text-embedding-ada-002` with 1,536 dimensions means one document would consume 1,536 floats. Similarily, 100 documents with a single, 1,536-dimensional vector field would consume in total 100 docs x 1536 floats/doc = 153,600 floats. 1,000 documents with two 768-dimensional vector fields, consume 1000 docs x 2 fields x 768 floats/doc = 1,536,000 floats.

| SKU   | Storage quota (GB) | Vector index size quota per partition (GB) | Approx. floats per partition |
| ----- | ------------------ | ------------------------------------------ | ---------------------------- |
| Basic | 2                  | 0.5                                        | 134 million                  |
| S1    | 25                 | 1                                          | 268 million                  |
| S2    | 100                | 6                                          | 1,611 million                |
| S3    | 200                | 12                                         | 3,221 million                |
| L1    | 1,000              | 12                                         | 3,221 million                |
| L2    | 2,000              | 36                                         | 9,664 million                |

## Documentation

For the private preview, we're providing the following documentation:

- This readme covers installation and introduces you to the private preview.
- This [FAQ](/docs/faq.md) answers basic questions about feature capabilities.
- The .NET, Python, and JavaScript demos have readme files for setting up and running the demo code.
- REST API reference in the [/docs folder](/docs/rest-api-reference/rest-api-reference.md).
- Concept docs and How-to's for the main scenarios can be found in the [/docs folder](/docs/).
- For updates to features and samples, see this [change list](changelist.md)

## References

- [Azure Search OpenAI Demo](https://github.com/Azure-Samples/azure-search-openai-demo/tree/vectors) A sample app for the Retrieval-Augmented Generation pattern running in Azure, using Azure Cognitive Search for retrieval and Azure OpenAI large language models to power ChatGPT-style and Q&A experiences. Use the "vectors" branch to leverage Vector retrieval.
- [Azure Search OpenAI Demo - C#](https://github.com/Azure-Samples/azure-search-openai-demo-csharp/tree/feature/embeddingSearch) A sample app for the Retrieval-Augmented Generation pattern running in Azure, using Azure Cognitive Search for retrieval and Azure OpenAI large language models to power ChatGPT-style and Q&A experiences using C#.
- [Azure OpenAI Embeddings QnA with Azure Search as a Vector Store](https://github.com/ruoccofabrizio/azure-open-ai-embeddings-qna) (github.com) A simple web application for a OpenAI-enabled document search. This repo uses Azure OpenAI Service for creating embeddings vectors from documents. For answering the question of a user, using Azure Cognitive Search for retrieval and Azure OpenAI large language models to power ChatGPT-style and Q&A experiences.
- [ChatGPT Retreival Plugin Azure Search Vector Database](https://github.com/openai/chatgpt-retrieval-plugin/blob/main/README.md#azure-cognitive-search) The ChatGPT Retrieval Plugin lets you easily find personal or work documents by asking questions in natural language. Azure Cognitive Search now supported as an official vector database.
- [Azure Search Vector Search Demo Web App Template](https://github.com/farzad528/azure-search-vector-search-demo) A Vector Search Demo React Web App Template using Azure OpenAI for Text Search and Cognitive Services Florence Vision API for Image Search.
- [Azure Cognitive Search Documentation](https://learn.microsoft.com/azure/search/)
- [Azure OpenAI Service Documentation](https://learn.microsoft.com/azure/cognitive-services/openai/)
- [Azure OpenAI Service Documentation](https://learn.microsoft.com/azure/cognitive-services/openai/)
- [Cognitive Services Computer Vision Documentation](https://learn.microsoft.com/azure/cognitive-services/computer-vision/)

## Contact us

For questions, concerns, or other feedback about vector search, please reach out to azuresearch_contact@microsoft.com.

For suggestions about docs or samples, please file a pull request or issue on this repo.
