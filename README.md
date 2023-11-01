# RAG Resources (work in progress)

A collection of curated RAG (Retrieval Augmented Generation) resources.

What is RAG?

**R**etrieval **A**ugmented **G**eneration or RAG for short is the process of having a Large Language Model (LLM) generate text based on a given context.

* **Retrieval** = Find relevant data (texts, images, etc) for a given query.
* **Augmented** = Add the retrieved relevant data as context information for the query.
* **Generation** = Generate responses based on the query and retrieved information.

The goal of RAG is to reduce hallucinations in LLMs (as in, prevent them from making up information that looks right but isn't).

Think of RAG as a tool to improve your calculator for words. 

The workflow looks like this: 

```
Query (e.g. a question) -> Find relevant resources to query (retrieval) -> Add relevant resources to query (augment) -> LLM creates a response to the query based on the context (generate).
```

The following list of resources is my own collection I've been saving in notes.

If I find something valuable, I'll add it here too (feel free to add a pull request with your own).

A focus will be on papers and blog posts with code attached.

## Papers

* May 2020 | [Original RAG paper] Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks | [Paper](https://arxiv.org/abs/2005.11401)
* Oct 2023 | SELF-RAG: Learning to Retrieve, Generate and Critique through Self-reflection | [Paper](https://arxiv.org/abs/2310.11511), [GitHub](https://github.com/AkariAsai/self-rag)

## Tutorials
* [Building RAG-based LLM applications for production](https://www.anyscale.com/blog/a-comprehensive-guide-for-building-rag-based-llm-applications-part-1) - A huge comprehensive guide with a focus on production.

## Blog posts
- [Contextual.ai](http://Contextual.ai) = company based on RAG, see the [launch blog post](https://contextual.ai/announcing-next-generation-language-models/)
- [How an LLM Chatbot works: Exploring Chat with Retrieval-Augmented Generation](https://txt.cohere.com/exploring-chat-rag/) from the Cohere Blog

## Log

* 1 Nov 2023 - Start repo to collect my own resources.
