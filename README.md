# RAG

Project to learn about RAG and noting down challenges I faced. 

What is Retrieval Augmentation Generation (RAG)?

Large language models (LLMs) are powerful, but they have two key limitations:

- Finite context —> they can’t ingest entire corpora at once.

- Static knowledge —> their training data is frozen at a point in time.

Retrieval addresses these problems by fetching relevant external knowledge at query time. This is the foundation of Retrieval-Augmented Generation (RAG): enhancing an LLM’s answers with context-specific information.

We can do fine-tuning of LLM also but not suitable here, read [here](supplementary_readings/RAG_vs_Fine-tuning.md) when to choose RAG over fine-tuning.

Let's setup pipeline for our RAG application.

## 1. Data Source 

Our data needs to be in string formate. This string will be part of our prompt and LLM will use it. 

This data can come from web scrapping, internal documents, pdfs, google drive, AWS S3 etc.. I am scrapping wikipedia's pages related to marvel cinematic unviverse and saving them as txt file. So our source is text file. 

- ### Web Scrapping

I am using LangChain's ```RecursiveUrlLoader```. It lets you recursively scrape all child links from a root URL and parse them into Documents. We can specify number of links that we want to travel from base link with ```depth``` parameter. I am taking it's values as 2, so it will go to all links of our base URL and then scrape the content and will not go further from links found in that page. 

- ### Parser

```RecursiveUrlLoader``` gives data with html in it. We need a parser to get text content only.

