# 🔍 Week 5 Exercise: Retrieval-Augmented Generation (RAG)

This project demonstrates a **Retrieval-Augmented Generation (RAG)** pipeline using the **LangChain** framework and OpenAI embeddings. The objective is to retrieve relevant context from Wikipedia, store it in a vector database, and generate LLM responses grounded in that retrieved context.

---

## 📌 Objective
- Search for and load Wikipedia content on a given topic.
- Chunk and store the text in a vector database.
- Perform semantic search over the stored chunks.
- Use the retrieved chunks to answer user queries.

---

## 📊 Dataset Overview
- **Source**: Wikipedia via `langchain_community.document_loaders.WikipediaLoader`
- **Example Query**: `"LangChain"`
- **Preprocessing**:
  - Chunk size: 1,000 characters
  - Chunk overlap: 20 characters
  - Text length function: `len`

---

## 🛠 Methods
1. **Document Loading**  
   - `WikipediaLoader` loads top 1 document for the search term.

2. **Text Splitting**  
   - `RecursiveCharacterTextSplitter` divides the document into overlapping chunks for better context retrieval.

3. **Vector Store Creation**  
   - Used `Chroma` as the vector database.
   - Generated embeddings with `OpenAIEmbeddings`.
   - Stored chunks with metadata and unique IDs.

4. **Persistence**  
   - Chroma collection persisted locally in `db/` directory for reuse.

5. **Querying & RAG Pipeline**  
   - Performed semantic similarity search.
   - Passed top-matching chunks to an LLM prompt to answer user questions.

---

## 📈 Analysis & Observations
- RAG successfully returned contextually relevant sections of the Wikipedia article.
- Retrieved chunks significantly improved the factual grounding of generated responses.
- Small chunk overlap improved semantic continuity without excessive redundancy.
- Local persistence allowed reloading the database without recomputation.

---

## 🏆 Key Findings
1. Embedding-based retrieval provides more relevant context than keyword search.
2. Proper chunk sizing (≈1k characters) balances semantic completeness and precision.
3. Persistent vector storage improves workflow efficiency for repeated queries.

---

## 💡 Recommendations
- Experiment with **larger chunk sizes** for narrative-heavy content.
- Try **hybrid search** (keyword + vector) to capture more diverse matches.
- Deploy with **API-based retrieval** for dynamic Wikipedia queries.
- Integrate a **reranker model** for more precise top-k retrieval.

---

## ⚖️ Ethical Considerations
- Wikipedia content is open access, but attribution is recommended.
- Model responses should be validated against authoritative sources for sensitive topics.

---

## 📚 References
- [LangChain Documentation](https://docs.langchain.com/)
- [Chroma Vector Database](https://docs.trychroma.com/)
- [OpenAI Embeddings](https://platform.openai.com/docs/guides/embeddings)

