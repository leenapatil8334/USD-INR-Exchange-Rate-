
# YOUTUBE_chatbot
# 🎙️ RAG-based YouTube Chatbot with LangChain & Hugging Face

This project implements a Retrieval-Augmented Generation (RAG) based chatbot that can answer questions using transcripts from YouTube videos. It leverages `LangChain`, `FAISS` for vector search, and Hugging Face models like `LLaMA 3` for generating contextually relevant responses.

---

## 📌 Features

- ✅ Automatically fetches YouTube video transcripts using `youtube-transcript-api`.
- ✅ Splits transcript into meaningful chunks using `RecursiveCharacterTextSplitter`.
- ✅ Generates dense vector embeddings using Hugging Face embedding models.
- ✅ Stores and retrieves text chunks using FAISS vector store.
- ✅ Uses semantic search to find the most relevant chunks.
- ✅ Constructs prompt and sends it to a Hugging Face-hosted LLM (e.g. `LLaMA 3 8B`).
- ✅ Fully modular pipeline powered by LangChain runnables.

---

## 🔁 Workflow

1. **Transcript Fetching**  
   Uses `YouTubeTranscriptApi` to extract the transcript of a given video ID.

2. **Trimming and Preprocessing**  
   The transcript is optionally trimmed to a manageable length to reduce token load.

3. **Text Splitting**  
   `RecursiveCharacterTextSplitter` divides the transcript into overlapping chunks for better context handling.

4. **Embeddings Generation**  
   Chunks are embedded using `sentence-transformers/all-MiniLM-L6-v2` via `HuggingFaceEmbeddings`.

5. **FAISS Vector Store Creation**  
   Embeddings are stored in a FAISS vector store to enable fast vector similarity search.

6. **Retriever Setup**  
   A retriever queries the FAISS store and returns the top-`k` relevant chunks using semantic search.

7. **Prompt Construction**  
   Retrieved chunks and the user's query are merged using a `PromptTemplate`.

8. **LLM Invocation**  
   The final prompt is sent to a Hugging Face-hosted model like `meta-llama/Meta-Llama-3-8B-Instruct`.

9. **Answer Generation**  
   The model generates a concise and relevant answer, forming the final response.

---


