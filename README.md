# 5G & 3GPP Protocol Assistant using RAG

A RAG-powered chatbot for querying the 3GPP TS 38.211 (5G NR) spec. Ask technical questions in plain English, get answers grounded in the actual document — with page citations.

No more ctrl-F'ing through 500-page PDFs.

---

## Stack

- **Embeddings:** `sentence-transformers/all-mpnet-base-v2`
- **Vector store:** ChromaDB (local)
- **LLM:** Groq API (`openai/gpt-oss-120b`)
- **Orchestration:** LangChain LCEL
- **UI:** Gradio

---

## Usage

1. Open `notebook.ipynb` in Jupyter or Google Colab
2. Add your [Groq API key](https://console.groq.com) when prompted
3. Run the ingestion cell once to download the spec and build the vector DB
4. Run the app cell — Gradio will give you a local (or shareable) link

---

## How it works

The spec PDF is chunked, embedded, and stored locally. On each query, the top 6 most relevant chunks are retrieved and passed to the LLM as context. It only answers from the document — if the answer isn't there, it says so.
