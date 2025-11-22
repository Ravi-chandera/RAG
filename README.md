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

This data can come from web scrapping, internal documents and pdfs stored in AWS S3, slack, notion, google drive etc.. 

Our data source is web scrapping wikipedia's pages related to marvel cinematic unviverse and saving them as txt file.

- ### Web Scrapping

I am using LangChain's ```RecursiveUrlLoader```. It lets you recursively scrape all child links from a root URL and parse them into Documents. We can specify number of links that we want to travel from base link with ```depth``` parameter. I am taking it's value as 2, so it will go to all links of our base URL and then scrape the content and will not go further from links found in that page. 

- ### Parser

```RecursiveUrlLoader``` gives data with html in it. We need a parser to extract text content. 

- ### Storing 

We are scraping web data and need to save it so we can use it later. Right now I am writing the scraped data to a text file on the same machine that runs the RAG app. In a production setup you usually have a data pipeline that scrapes or collects data on a schedule and saves it to cloud storage like AWS S3. That pipeline normally runs as a separate microservice.


