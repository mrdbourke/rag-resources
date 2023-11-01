# RAG Resources (work in progress)

A collection of curated RAG (Retrieval Augmented Generation) resources.

## What is RAG?

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
* Dec 2022 | Precise Zero-Shot Dense Retrieval without Relevance Labels (HyDE - Hypothetical Document Embedding) | [Paper](https://arxiv.org/abs/2212.10496)
* Oct 2023 | SELF-RAG: Learning to Retrieve, Generate and Critique through Self-reflection | [Paper](https://arxiv.org/abs/2310.11511), [GitHub](https://github.com/AkariAsai/self-rag)

## Guides and Recipes

* TK - Anthropic Retrieval Demo - https://github.com/anthropics/anthropic-retrieval-demo (a bunch of cool ideas around retrieval)
* TK - Anthropic Cookbook - https://github.com/anthropics/anthropic-cookbook/tree/main 
* TK - OpenAI Cookbook - https://github.com/openai/openai-cookbook
* TK - Brex's Prompt Engineering Guide - https://github.com/brexhq/prompt-engineering 

## Tutorials

* [Building RAG-based LLM applications for production](https://www.anyscale.com/blog/a-comprehensive-guide-for-building-rag-based-llm-applications-part-1) - A huge comprehensive guide with a focus on production.

## Blog posts

- [Contextual.ai](http://Contextual.ai) = company based on RAG, see the [launch blog post](https://contextual.ai/announcing-next-generation-language-models/)
- [How an LLM Chatbot works: Exploring Chat with Retrieval-Augmented Generation](https://txt.cohere.com/exploring-chat-rag/) from the Cohere Blog

## 10 second walkthrough

The following is a basic RAG workflow.

It can be implemented in ~100-200 lines of Python code (maybe less).

1. Get a corpus of target data (e.g. pages of Wikipedia, transcripts of your favourite podcaster, your own notes lost in the void)
2. Split target data into chunks (e.g. groups of 10 sentences, paragraphs, overlapping or not)
3. Embed your chunks into vector space (e.g. text -> model from Hugging Face -> vectors)
4. Store your embedded chunks in memory (e.g. this could be a simple `np.array` or a Python dictionary or a vector database)
5. Make a query (e.g. "How many minutes a day should I spend in a cold plunge?")
6. Embed the query using the same model from step 3 (crucial)
7. Search across your embedded chunks from step 4 for items that are similar or related to your query (retrieval), to measure similarity between two vectors, use dot product or cosine distance (what you're doing here is ["semantic similarity"](https://www.sbert.net/docs/usage/semantic_textual_similarity.html))
8. Optional: Use the top-n (e.g. 3-5 or more if your LLM context window allows) results from step 7 to answer the question directly
9. Use the top-n (e.g. 3-5 or more if your LLM context window allows) results from step 7 as input to your LLM prompt (augment) to help it generate an answer
10. *Hopefully* reduce hallucinations in the LLM response thanks to the added context from the retrieved chunks

## FAQ

**RAG sounds like a hack, is it?**

Yes, it's a nice hack that works.

**Is RAG just another form of prompt engineering?**

Yes.

**Which embedding model should I use?**

Start with a model somewhere near the top of [Hugging Face MTEB (Massive Text Embedding) leaderboard](https://huggingface.co/spaces/mteb/leaderboard), [`sentence-transformers`](https://www.sbert.net/) is a great library too.

**Do I need a vector database?**

Under 100,000 chunks? 

Probably not (use [`np.array`](https://twitter.com/karpathy/status/1647374645316968449?lang=en) instead).  

100,000+ chunks? 

See how you go without one first, calculating `np.dot` over 1,000s of embeddings is quite fast.

**Which LLM should I use?**

Generally, the biggest one you can afford will give the best results.

## Log

* 1 Nov 2023 - Start repo to collect my own resources.
