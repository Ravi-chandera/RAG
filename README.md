# RAG

Project to learn about RAG and noting down challenges I faced. 

Large language models (LLMs) are powerful, but they have two key limitations:

- Finite context —> they can’t ingest entire corpora at once.

- Static knowledge —> their training data is frozen at a point in time.

Retrieval addresses these problems by fetching relevant external knowledge at query time. This is the foundation of Retrieval-Augmented Generation (RAG): enhancing an LLM’s answers with context-specific information.

We can do fine-tuning of LLM also, read [here](.\supplementary_readings\RAG_vs_Fine-tuning.md) when to choose RAG over fine-tuning.

# 1. Data Source 

In RAG applications, we have data stored in some file format that we use in downstream applications. 
This data is mostly stored in documents, pdfs, 
