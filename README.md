# Notify
AI-powered study platform that transforms PDFs and YouTube lectures into Cornell Notes, Gap Analysis, and smart summaries — built with FastAPI, React, GPT-4, and AWS S3.
# 🎓 Notify — AI-Powered Learning Platform

> Transform any lecture or PDF into smart study material — Cornell Notes, Gap Analysis, and AI Summaries — powered by GPT-4 and Google Gemini.

Final Year Project · Computer Science · 2025

---

## 📌 Overview

Notify is a full-stack AI learning platform that solves a core student problem: passive reading doesn't lead to retention. Students upload a PDF or paste a YouTube lecture link, and Notify automatically generates structured Cornell Notes, identifies knowledge gaps using the Feynman technique, and delivers personalized AI feedback — all in one place.

---

## 😓 The Problem

| Problem | Description |
|---|---|
| 📚 Passive Reading | Students read but don't retain — no active engagement with material |
| ⏱️ Time Wasted | Making notes manually takes hours. Lecture → Notes → Study = Exhaustion |
| 🎯 No Feedback | Students don't know their weak areas — they study everything, retain little |
| 🔗 Disconnected Tools | PDF reader here, notes there, YouTube lectures somewhere else. No integration |

---

## ✨ Features

- 📄 **PDF Upload** — Upload any PDF; AI reads and extracts key content
- 🎬 **YouTube Lectures** — Paste a video link; AI transcribes and processes it
- 📝 **Cornell Notes Generator** — Auto-structured Main Notes, Cues & Summary
- 🔍 **Feynman Gap Analysis** — AI finds your knowledge gaps from your own explanation
- 🤖 **Dual AI Engine** — GPT-4 primary with Google Gemini fallback
- 💾 **Session History** — All AI outputs saved and revisitable anytime

---

## 🔄 How It Works

```
User → Frontend (React) → Backend (FastAPI) → Processing Layer → AI Engine → Output
 ↑                                                                              |
 └──────────────────────── Study Material Returned ─────────────────────────────┘
```

1. **User** logs in and uploads a PDF or pastes a YouTube link
2. **Frontend** sends the request via React + Axios
3. **Backend** authenticates via JWT and routes the request
4. **Processing Layer** extracts text from PDF / transcribes audio from YouTube
5. **AI Engine** runs GPT-4 (or Gemini fallback) through custom prompt pipelines
6. **Output** — Cornell Notes or Gap Analysis returned to the student

---

## 🧠 Features In Depth

### Feature 01 — Cornell Notes Generator

```
PDF / YouTube Link → Text Extraction → AI Prompt Pipeline → Cornell Format Output
```

| Section | Description |
|---|---|
| Main Notes | Key concepts, definitions, and explanations from the lecture |
| Cues | Important questions and keywords for quick revision |
| Summary | A concise 3–4 line overview of the entire lecture |

### Feature 02 — Feynman Gap Analysis Engine

> *"If you cannot explain it simply, you do not understand it enough."* — Richard Feynman

1. **Student Explains** — writes their own explanation of a concept
2. **AI Reads & Analyzes** — GPT-4 checks understanding depth
3. **Gaps Identified** — AI pinpoints weak areas and misconceptions
4. **Feedback Returned** — personalized, encouraging feedback sent back

---

## 🛠️ Tech Stack

### Frontend
| Technology | Purpose |
|---|---|
| React | Component-based UI |
| Tailwind CSS | Utility-first styling |
| Axios | API communication |

### Backend
| Technology | Purpose |
|---|---|
| FastAPI | High-performance API server |
| JWT Auth | Secure authentication |
| PostgreSQL | Relational database |

### AI Layer
| Technology | Purpose |
|---|---|
| OpenAI GPT-4 | Primary AI model |
| Google Gemini | Fallback AI model |
| Prompt Pipelines | Cornell & Feynman custom prompts |

### Processing Layer
| Technology | Purpose |
|---|---|
| PyMuPDF (fitz) | High-performance PDF text extraction |
| python-docx | Word document processing |
| python-pptx | PowerPoint processing |
| yt-dlp | YouTube & video platform audio extraction |
| Aiofiles | Async file I/O for non-blocking uploads |
| Boto3 / AWS S3 | Cloud file storage and retrieval |

---

## 🤖 AI Fallback System

```
OpenAI GPT-4  →  (if fail)  →  Google Gemini  →  Response to User
```

---

## 👥 The Team

| Member | Role | Responsibilities |
|---|---|---|
| Aswerah | Frontend UI | React components, Dashboard & Interface, Whiteboard & Notes UI |
| Ibrahim | Frontend Logic | Form handling, API integration, State management |
| Ahmad | Backend Core | FastAPI server, JWT authentication, PostgreSQL database |
| **Umer** | **Backend — File & Media Processing** | **PDF/DOCX/PPTX extraction, YouTube audio, AWS S3, async file I/O** |
| Hidayat Ullah | AI Engine | Prompt engineering, Cornell & Feynman pipelines, GPT-4 + Gemini integration |

---

## 🗂️ My Contribution — Role 04: File & Media Processing

> **Umer Farooq** — *"The Translator"*

I built the entire file ingestion and media processing pipeline — everything between a user uploading a file or pasting a YouTube link, and that content reaching the AI engine as clean, structured text.

### What I Built

**📄 Document Processing**
- Built file upload endpoints using FastAPI
- Extracted and cleaned text from PDF, DOCX, and PPTX files using `PyMuPDF`, `python-docx`, and `python-pptx`
- Chunked large documents into AI-context-safe segments for the GPT-4 / Gemini prompt pipeline

**🎬 YouTube & Audio Processing**
- Integrated `yt-dlp` to download audio from YouTube lecture links
- Piped extracted audio into the transcription layer for AI processing

**☁️ Cloud Storage**
- Designed and implemented all AWS S3 upload, retrieval, and lifecycle operations using `Boto3`
- Ensured scalable, reliable file storage for uploaded documents and processed outputs

**⚡ Performance**
- Used `Aiofiles` for async, non-blocking file I/O to handle large uploads without blocking the server

---

## ⚙️ Installation

### Prerequisites
- Python 3.10+
- Node.js 18+
- PostgreSQL
- AWS S3 bucket
- OpenAI API key
- Google Gemini API key

### Backend Setup

```bash
# Clone the repository
git clone https://github.com/your-username/notify.git
cd notify/backend

# Install dependencies
pip install -r requirements.txt

# Configure environment variables
cp .env.example .env
# Fill in: DATABASE_URL, OPENAI_API_KEY, GEMINI_API_KEY, AWS credentials

# Run the server
uvicorn main:app --reload
```

### Frontend Setup

```bash
cd notify/frontend

# Install dependencies
npm install

# Run the dev server
npm run dev
```

---

## 🔐 Environment Variables

```env
DATABASE_URL=postgresql://user:password@localhost/notify_db
SECRET_KEY=your_jwt_secret_key
OPENAI_API_KEY=your_openai_key
GEMINI_API_KEY=your_gemini_key
AWS_ACCESS_KEY_ID=your_aws_key
AWS_SECRET_ACCESS_KEY=your_aws_secret
AWS_BUCKET_NAME=your_bucket_name
AWS_REGION=us-east-1
```

---

## 📄 License

This project is open source and available for educational use.

---

*Final Year Project · Computer Science · 2025*
*Aswerah · Ibrahim · Ahmad · Umer · Hidayat Ullah*
