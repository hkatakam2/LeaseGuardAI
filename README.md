# LeaseGuard AI 🛡️⚖️

> **Tenant Rights Defender & Lease Analyzer.**

LeaseGuard is a full-stack legal-tech platform designed to protect students from predatory housing leases. It uses OCR to parse PDF contracts and a RAG (Retrieval-Augmented Generation) pipeline to cross-reference clauses against the *New York State Tenants' Rights Guide*.

![Status](https://img.shields.io/badge/Status-Production_Ready-green)
![Stack](https://img.shields.io/badge/Frontend-Next.js-black)
![Stack](https://img.shields.io/badge/Backend-FastAPI-teal)
![AI](https://img.shields.io/badge/AI-RAG_%2B_LangChain-purple)

## 🧩 Architecture

The application uses a decoupled **Microservices** architecture:

1.  **Frontend (Next.js):** Handles PDF uploads and renders the interactive "Red Flag" dashboard.
2.  **Backend (FastAPI):**
    * **OCR Service:** Extracts text from scanned PDFs.
    * **Embedding Service:** Converts text into vector embeddings using OpenAI models.
    * **RAG Engine:** Queries the Pinecone vector DB (loaded with NY Law) to find violations.

## 🛠 Tech Stack

* **Frontend:** Next.js 14, TypeScript, Tailwind CSS, Shadcn UI
* **Backend:** Python, FastAPI, PyPDF2
* **AI/ML:** LangChain, OpenAI API, Pinecone (Vector DB)
* **Infrastructure:** Docker

## 🚀 Getting Started

### Backend Setup (Python)
```bash
cd backend
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
uvicorn main:app --reload
```

### Frontend Setup (TypeScript)
```bash
cd frontend
npm install
npm run dev
```

## 💡 How it Works (The RAG Pipeline)
1. Ingestion: User uploads a lease PDF.
2. Chunking: The backend splits the lease into legal clauses (semantic chunking).
3. Retrieval: For every clause, the system searches the NY Tenant Rights vector store for relevant laws.
4. Analysis: The LLM compares the Lease Clause vs. The Law. If they conflict, it is flagged as "High Risk."

## 🔒 Privacy First
LeaseGuard processes documents in-memory. Once the analysis is complete, the PDF and its contents are wiped from the server to ensure user privacy.

