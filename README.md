# Sales Field Intelligence Chatbot

Sales Field Intelligence Chatbot adalah aplikasi berbasis Streamlit yang membantu membaca data pipeline dan activity, menghasilkan insight, serta memberikan rekomendasi coaching untuk Sales dan Supervisor.

Aplikasi ini menggabungkan:

- Excel Analyzer berbasis Pandas
- RAG Knowledge Base
- Gemini 2.5 Flash
- Groq Llama
- Auto Router
- Streamlit Chat UI

---

## 1. Fitur Utama

### Excel Analyzer

User dapat mengupload file Excel pipeline/activity, lalu sistem akan:

- mendeteksi kolom penting
- melakukan mapping kolom
- menormalisasi stage pipeline
- menghitung summary pipeline
- menghitung summary activity
- membuat prioritas coaching Sales
- membuat prioritas coaching Supervisor
- membuat context ringkas untuk AI

### RAG Knowledge Base

User dapat mengupload dokumen knowledge base dalam format:

- PDF
- DOCX
- TXT
- MD

Dokumen akan diproses menjadi vector store FAISS menggunakan embedding lokal (Huggingface).

### Auto Router

Chatbot akan memilih jalur jawaban:

- Excel Analyzer + Gemini untuk pertanyaan berbasis data Excel
- RAG + Gemini untuk pertanyaan berbasis knowledge base
- Groq Llama untuk task ringan
- Gemini Direct untuk analisis umum

### Utility

Aplikasi juga menyediakan:

- route info
- source reference
- clear chat
- clear cache
- reset Excel Analyzer
- reset RAG
- export chat JSON
- export chat Markdown
- final test scenario
- dry route diagnostic

---

## 2. Struktur Project

```text
sales_field_intelligence_streamlit/
│
├── app.py
├── requirements.txt
├── README.md
├── .gitignore
├── .streamlit/
│   └── config.toml
├── knowledge_base/
│   └── default_sales_field_knowledge.md
├── sample_data/
│   └── sales_field_intelligence_dummy_testing.xlsx
└── exports/
