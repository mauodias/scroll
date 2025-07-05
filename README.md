# scroll

**scroll** is a minimal, private web app for AI-driven interactive storytelling with a book-like reading experience optimized for e-readers and low-resource devices.

---

## 🚀 Project Overview

**scroll** enables you to generate and interact with AI-powered roleplay stories (initially focused on text-based interactive fiction).  
It features:

- Minimal UI designed for e-ink and weak touchscreens  
- Paginated, book-style reading interface  
- AI-generated reply options as large buttons, with fallback free text input  
- Passwordless, QR-based authentication optimized for device pairing  
- NoSQL-based local-first data storage with optional serverless deployment  
- Extensible backend with FastAPI, easily containerized for local or cloud use

---

## 🧱 Architecture

```
[Frontend (Static, minimal JS)]
        ↓
[FastAPI Backend API]
        ↓
[NoSQL Storage (TinyDB or similar)]
        ↓
[LLM Provider (OpenAI API or local stub)]
```

---

## 🛠️ Getting Started

### Prerequisites

- Python 3.10+  
- Node.js 16+ (if using a frontend build tool like Vite)  
- Docker & Docker Compose (optional, recommended for local dev)  

### Running Locally (Docker)

```bash
docker-compose up --build
```

This spins up:

- Backend API on `http://localhost:8000`  
- Frontend UI on `http://localhost:3000`

---

## 🏗️ Development Workflow

- Backend code lives in `/backend` — FastAPI with routes for `/chat`, `/auth`, `/stories`, etc.  
- Frontend code lives in `/frontend` — minimal UI with pagination and reply buttons  
- Use dummy LLM responses initially for rapid frontend/backend integration  
- Integrate real OpenAI API calls later with environment variable `OPENAI_API_KEY`  
- Use `.env` files to manage secrets and config  

---

## 🔐 Authentication

- Passwordless login via QR code device pairing flow  
- Backend manages device codes and login status in NoSQL storage  
- JWT tokens issued upon successful confirmation  

---

## 📚 Story Management

- Stories stored as JSON blobs with context, summary, and message history  
- Backend exposes endpoints to create, update, and fetch story state  
- Summarization logic trims context to optimize token usage  

---

## 🧪 Testing

- Use the dummy LLM mode (`backend/services/llm_dummy.py`) for fast iteration  
- Run unit tests with `pytest` in the backend folder  
- Frontend can mock API calls or use actual backend during development  

---