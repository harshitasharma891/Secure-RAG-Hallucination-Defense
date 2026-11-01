# Secure RAG: Hallucination and Context Grounding

## Project Overview

This project demonstrates how a Retrieval-Augmented Generation (RAG) system can be affected by malicious or misleading content in its knowledge base.

The project creates a vulnerable knowledge base by combining a source document with an injected instruction containing false information. A RAG pipeline retrieves this content and generates responses using a language model.

The project also introduces a validation step that checks whether a user question can be answered directly from the retrieved context before returning a response.

## Key Features

- Retrieval-Augmented Generation (RAG) pipeline.
- Semantic document retrieval using FAISS.
- Text embeddings using Hugging Face.
- Demonstration of a vulnerable knowledge base containing injected instructions.
- LLM-based answer validation.
- Context-grounding checks before generating a final response.
- Handling of questions that cannot be answered from the knowledge base.

## Project Workflow

```text
Source Document + Injected Content
              ↓
      FAISS Vector Database
              ↓
          User Query
              ↓
       Context Retrieval
              ↓
      Answer Validation
          ↙       ↘
   Not Available   Generate Response
                       ↓
                  Final Answer
```

## How the Project Works

### 1. Knowledge Base Creation

The project loads a source document and adds an injected document containing misleading instructions.

Both documents are added to a FAISS vector store for semantic retrieval.

### 2. Vulnerable RAG Pipeline

The initial RAG pipeline retrieves relevant context and passes it directly to the language model.

This demonstrates how untrusted or malicious content in retrieved documents can influence generated responses.

### 3. Context Validation

The project adds an answer validation step before returning a response.

The language model is asked whether the user's question can be answered directly from the retrieved context.

If the required information is unavailable, the system returns:

`Information not available in the knowledge base.`

Otherwise, the query proceeds through the RAG pipeline.

## Models and Tools Used

### Embedding Model

`sentence-transformers/all-MiniLM-L6-v2`

Used to generate vector embeddings for the documents and user queries.

### Language Model

`TinyLlama/TinyLlama-1.1B-Chat-v1.0`

Used for response generation and answer validation.

### Vector Store

**FAISS**

Used for semantic similarity search and context retrieval.

## Technologies Used

- Python
- Hugging Face Transformers
- LangChain Community
- LangChain Hugging Face
- FAISS
- Sentence Transformers
- Google Colab

## Installation

Install the required libraries:

```bash
pip install transformers langchain-community langchain-huggingface faiss-cpu sentence-transformers
```

## Running the Project

1. Provide a source document for the knowledge base.
2. Add the documents to the FAISS vector store.
3. Load the embedding model and language model.
4. Run the vulnerable RAG pipeline to observe the effect of injected content.
5. Run the secure validation function to check whether the query can be answered from the retrieved context.

## Repository Structure

```text
Secure-RAG-Hallucination-Defense/
│
├── Secure_RAG_Hallucination_Defense.ipynb
└── README.md
```

## Important Note

This project is intended to demonstrate potential security and reliability issues in RAG systems. Any injected content used in the notebook is included only for controlled testing and evaluation.

## Author

**Harshita Sharma**

AI/ML Engineer

GitHub: github.com/harshitasharma891  
LinkedIn: linkedin.com/in/harshita-sharma-b843031b5
