# RAG Document Q&A — Local Pipeline

**Stack:** LangChain · Ollama · FAISS · nomic-embed-text · Llama 3.2

A fully **local** Retrieval-Augmented Generation (RAG) pipeline that lets you upload any PDF and ask questions about it in natural language. No API keys, no data sent to the cloud.

## Architecture

```
PDF → Text Splitting → Embeddings (nomic-embed-text) → FAISS Vector Store
                                                               ↓
Answer ← Llama 3.2:3b ← Retrieved Chunks ← User Question
```

## Requirements

- [Ollama](https://ollama.com) installed and running
- Models pulled:
  ```bash
  ollama pull llama3.2:3b
  ollama pull nomic-embed-text
  ```

## Setup

```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

## Usage

1. Place your PDF in the `docs/` folder
2. Update `PDF_PATH` in `rag_pipeline.ipynb`
3. Open the notebook and select the `venv` kernel
4. Run all cells

## Notebook walkthrough

| Step | Description |
|------|-------------|
| 1 | Imports & configuration |
| 2 | Load & split the PDF into chunks |
| 3 | Generate embeddings & build FAISS index |
| 4 | Build the RAG chain (retriever + LLM) |
| 5 | Ask questions with source attribution |
| 6 | Interactive Q&A loop |
| 7 | Batch evaluation on multiple questions |
| 8 | Save & reload the vector store |
