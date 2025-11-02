# Question

### 1. What is a retriever in a RAG system?

A retriever fetches the most relevant pieces of information (text chunks, documents, or embeddings) from a knowledge base based on a user query. It narrows the search space before the generator (LLM) produces an answer.

---

### 2. What are the main types of retrievers?

* Dense retrievers: Use embeddings (e.g., FAISS, Chroma) for semantic similarity.

* Sparse retrievers: Use keyword-based matching (e.g., BM25).

* Hybrid retrievers: Combine both, balancing semantic understanding and exact term matching.

---

### 3. When should you use Chroma, FAISS, Pinecone, or Neo4j as a vector store?

| Vector Store | Best Use Case | Notes |
|---------------|---------------|-------|
| **Chroma** | Local development, small-to-medium projects | Easy to use, great for prototyping |
| **FAISS** | High-performance, on-prem or GPU-accelerated setups | Excellent for large-scale vector search |
| **Pinecone** | Cloud-native, scalable production systems | Fully managed and easy to integrate |
| **Neo4j** | When relationships matter (graph + vector) | Ideal for knowledge graphs with embeddings |

---

### 4. What is post-retrieval context compression?

Post-retrieval context compression refines or summarizes the retrieved text before passing it to the LLM.
It reduces token usage and improves accuracy by removing redundancy.

Techniques include:
    * Deduplication or Maximal Marginal Relevance (MMR)
    * Abstractive or extractive summarization
    * Re-ranking and filtering
    * Entity or keyword extraction
    * LLM-based compression

---

### 5. Why is answer grounding important in RAG?

Answer grounding ensures the model’s output is anchored to the retrieved evidence rather than generated from its prior knowledge.

Methods:
* Include citations linking to document sources
* Use entailment or alignment models to verify factual consistency
* Apply verifier models to check each claim.
Result: Fewer hallucinations and more trustworthy answers.
---

### 6. What is context window optimization?

Context window optimization is the process of maximizing the value of limited context space in LLMs.

Key steps:
* Smart document chunking (200–1000 tokens)
* Re-ranking to keep the most relevant chunks
* Compression (summarization or deduplication)
* Dynamic allocation of tokens based on query type
* Prioritization of high-relevance chunks

Goal: Keep only the most relevant information while staying within the model’s token limit.

---

### 7. How does multi-step reasoning help with limited context?

Instead of retrieving and generating in one shot, multi-step RAG loops through:
* Retrieve
* Summarize
* Re-retrieve

Each iteration refines the context, keeps it compact, and ensures the final answer is grounded and complete.

---

### 8. What metrics define a good retriever?

Recall: Does it find all relevant documents?

Precision: Are retrieved docs actually relevant?

Latency: How fast can it retrieve?

Scalability: How well does it handle large datasets?

Memory efficiency: How large is the index footprint?


---

### 9. How does a hybrid retriever improve performance?

Sparse retrieval ensures keyword coverage, while dense retrieval captures semantic meaning.

Hybrid methods combine both to reduce misses and boost both recall and precision.

---

### 10. Why are compression and grounding critical for reliable RAG outputs?

Because raw retrieval often contains redundant or irrelevant text, and ungrounded generation can hallucinate.
Compression keeps the context lean, while grounding ensures every part of the answer is verifiable.