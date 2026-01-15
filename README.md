# Multilingual AI Chat System

A robust, fully open-source AI chat application with text and voice support.
Migrated from Google Gemini to a high-performance open-source stack using **Groq (Llama 3)**, **HuggingFace**, and **OpenAI Whisper**.

Built with **Expo (React Native)** for the frontend and **FastAPI** for the backend.

## 🚀 Features

- **Y-Shaped Architecture**: Unified pipeline for both Text and Audio inputs.
- **Open-Source Stack**:
    - **Text Gen**: [Groq](https://groq.com) (Llama 3.3-70b) - Blazing fast & Free.
    - **Embeddings**: [HuggingFace](https://huggingface.co) (`all-MiniLM-L6-v2`) - Local & Unlimited.
    - **Transcription**: [OpenAI Whisper](https://github.com/openai/whisper) - Local & Accurate.
    - **Language Detect**: `langdetect` library - Local.
- **RAG System**: Professional-grade Retrieval Augmented Generation using FAISS vector store.
- **Multilingual**: Supports English, Hindi, Tamil, Telugu.
- **Cross-platform**: iOS, Android, and Web.

## 🛠️ Architecture

The backend implements a 4-stage Y-shaped pipeline:

1.  **Input Processing**:
    *   **Stage 1a (Text)**: Preprocessing & cleaning.
    *   **Stage 1b (Audio)**: Transcription via local Whisper model.
2.  **Query Refiner (Stage 2)**: Language detection & unified query formatting.
3.  **RAG Retriever (Stage 3)**: Semantic search using HuggingFace embeddings & FAISS.
4.  **Response Generator (Stage 4)**: Final answer generation using Groq API.

## 📦 Quick Start

### 1. Backend Setup

```bash
cd backend

# Install dependencies (Python 3.10+)
pip install -r requirements.txt

# Create .env file
echo "GROQ_API_KEY=your_groq_api_key_here" > .env
# Get free API key from: https://console.groq.com/keys

# Add documents (Optional)
# Copy PDF or PPTX files to backend/documents/ folder

# Start server
python main.py
```

Server runs on `http://localhost:8000`

### 2. Frontend Setup

```bash
cd frontend

# Install dependencies
npm install

# Configure API URL in frontend/services/api.ts if testing on device:
# export const API_BASE_URL = 'http://YOUR_LOCAL_IP:8000';

# Start app
npm start
```

## 📂 Project Structure

```
ADK/
├── backend/
│   ├── main.py              # FastAPI server (Lifespan managed)
│   ├── pipeline.py          # Y-shaped pipeline orchestrator
│   ├── langchain_rag.py     # RAG Entine (Groq + HuggingFace)
│   ├── requirements.txt     # Dependencies
│   └── documents/           # Knowledge base files
│
└── frontend/
    ├── app/
    │   ├── _layout.tsx      # Root layout
    │   └── index.tsx        # Main chat interface
    ├── components/
    │   ├── chat-input.tsx   # Input & recording logic
    │   ├── chat-messages.tsx # Message list display
    │   └── language-selector.tsx # Language string picker
    ├── services/
    │   └── api.ts           # API client
    ├── hooks/               # Custom React hooks
    ├── constants/           # App constants
    └── assets/              # Static assets
```
