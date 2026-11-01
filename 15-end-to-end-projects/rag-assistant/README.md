# Enterprise RAG Assistant

**Goal:** retrieve relevant evidence and generate grounded answers over a controlled document collection.

## Planned engineering scope
- Ingestion, parsing, chunking, metadata, and source traceability.
- Dense retrieval with FAISS or Chroma.
- BM25 lexical retrieval and hybrid rank fusion.
- Optional reranking and query transformation.
- Labeled evaluation set; Recall@K, MRR/nDCG, answer faithfulness, latency.
- Local inference option, API/UI, tests, and reproducible indexing.

**Existing foundation:** a local RAG prototype using LangChain, FAISS, BM25 hybrid retrieval, RRF/MMR, Ollama, and Streamlit. This project should document and benchmark the implementation rather than claim production readiness.

