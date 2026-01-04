# RAG Technical Test

This project implements a Retrieval-Augmented Generation (RAG) prototype using Langflow for visual orchestration and Qdrant as vector database.
The objective is to demonstrate correct RAG system design rather than model training.

Architecture

The pipeline is split into two flows:

Ingestion:
URL / Document → Chunking → Embeddings → Qdrant

Retrieval:
User Query → Vector Search → Context → LLM → Answer


This separation reflects production best practices.

Ingestion

Documents are loaded via URL-based ingestion, then chunked with overlap and stored in Qdrant together with metadata (source and page).
Chunking improves retrieval accuracy and reduces hallucinations.

Retrieval & Prompting

User queries are matched against the vector store via similarity search.
The LLM is prompted to answer only using retrieved context and to explicitly state when information is missing.

Vector Store

Qdrant is used for efficient similarity search and metadata management, enabling traceability and future citation support.

Embeddings & Limitations

OpenAI embeddings were used to align with the required tooling.
Due to API quota limits, runtime ingestion was not executed, but the pipeline is complete and reproducible with a valid API key.

Notes

Langflow is used as a visual prototyping tool.
The flow is exported as JSON and versioned in GitHub.

