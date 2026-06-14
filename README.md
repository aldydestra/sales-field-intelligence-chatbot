# Sales Field Intelligence Chatbot

Sales Field Intelligence Chatbot adalah aplikasi berbasis Streamlit yang membantu Data Analis membaca data pipeline dan activity, menghasilkan insight, diagnosis masalah, serta rekomendasi coaching untuk Sales dan Supervisor.

Aplikasi ini menggabungkan:

- Excel Analyzer berbasis Pandas
- RAG Knowledge Base berbasis FAISS
- Gemini 2.5 Flash
- Groq Llama
- Auto Router
- Streamlit Chat UI
- Colab + NGROK Demo untuk pengujian sementara

---

## Demo Colab + NGROK

> **Run Demo via Google Colab:**  
> [Open Colab Demo](https://colab.research.google.com/drive/1BTk0Z9FvF5WDT0SJsBaogdoIkHyZYl-E#scrollTo=x0rkcqCj_W6o)

Notebook Colab digunakan untuk melihat proses development dan menjalankan demo Streamlit melalui NGROK. Link ini bersifat sebagai demo sementara, bukan deployment permanen. Untuk penggunaan final, aplikasi tetap dapat dijalankan melalui Streamlit Cloud atau lokal dengan `streamlit run app.py`.

---

## 1. Value Proposition

Chatbot membantu Data Analis mengubah data pipeline/activity menjadi insight, diagnosis masalah, dan rekomendasi coaching secara cepat dan terarah.

---

## 2. Fitur Utama

### Excel Analyzer

User dapat mengupload file Excel pipeline/activity, lalu sistem akan:

- mendeteksi kolom penting secara otomatis
- menyediakan mapping kolom manual jika hasil deteksi belum sesuai
- menormalisasi stage pipeline
- memperbaiki validasi status `Cair` agar `Belum Cair`, `Batal Cair`, dan `Reject` tidak dihitung sebagai pencairan
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

Dokumen akan diproses menjadi vector store FAISS menggunakan embedding lokal, lalu digunakan sebagai dasar jawaban untuk pertanyaan berbasis pengetahuan, definisi, SOP, atau aturan coaching.

### Auto Router

Chatbot akan memilih jalur jawaban secara otomatis:

- Excel Analyzer + Gemini untuk pertanyaan berbasis data Excel
- RAG + Gemini untuk pertanyaan berbasis knowledge base
- Groq Llama untuk task ringan seperti sapaan, parafrase, dan ringkasan singkat
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
- prompt testing library
- final test scenario
- dry route diagnostic

---

## 3. Alur Development Notebook

Notebook Colab disusun sebagai dokumentasi proses development dengan section berikut:

```text
1. API & Environment
2. Knowledge Base
3. Load & Chunk
4. FAISS Index
5. Gemini RAG Engine
6. Batch Query
7. Safe Examples
8. Cache & Usage
9. Model Router
10. Colab Chat Loop
11. Excel Analyzer
12. Excel Chat Router
13. Streamlit Project
14. NGROK Demo
15. Final Package
```

Fungsi utama notebook:

- membangun knowledge base lokal
- membuat index FAISS
- menguji RAG dengan Gemini
- menguji router Gemini/Groq
- menguji Excel Analyzer
- membuat file Streamlit `app.py`
- menjalankan demo Streamlit via NGROK
- membuat package final untuk GitHub

---

## 4. Struktur Project

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
    └── .gitkeep
```

---

## 5. Cara Menjalankan Lokal

Install dependency:

```bash
pip install -r requirements.txt
```

Jalankan aplikasi:

```bash
streamlit run app.py
```

---

## 6. Cara Menggunakan Aplikasi

1. Buka aplikasi Streamlit.
2. Masukkan Gemini API Key.
3. Masukkan Groq API Key jika tersedia.
4. Upload file Excel pipeline/activity.
5. Pilih sheet yang sesuai.
6. Cek mapping kolom.
7. Klik **Proses Excel Analyzer**.
8. Upload knowledge base jika ingin menggunakan RAG.
9. Klik **Build RAG Knowledge Base**.
10. Gunakan chat untuk bertanya.

---

## 7. Cara Menjalankan Demo via Colab + NGROK

1. Buka link Colab Demo di bagian atas README.
2. Pastikan API Key dan NGROK Token disimpan melalui Colab Secrets.
3. Jalankan cell setup sesuai urutan notebook.
4. Jalankan cell Streamlit Project untuk membuat `app.py`.
5. Jalankan cell NGROK Demo.
6. Buka link publik yang dihasilkan oleh NGROK.

Catatan:

- NGROK digunakan untuk demo sementara.
- Link NGROK dapat berubah setiap runtime.
- Jangan menuliskan API Key atau NGROK Token langsung di notebook.

---

## 8. Contoh Pertanyaan

### Excel Analyzer

```text
Berdasarkan data Excel, buatkan ringkasan pipeline dan activity.
```

```text
Sales mana yang perlu menjadi prioritas coaching berdasarkan data Excel?
```

```text
Region mana yang perlu perhatian dari data ini?
```

### RAG Knowledge

```text
Apa itu Panas dalam pipeline?
```

```text
Bagaimana rekomendasi coaching jika activity tinggi tetapi cair rendah?
```

### Groq Light

```text
Halo, jelaskan singkat chatbot ini bisa bantu apa?
```

```text
Parafrase kalimat ini agar lebih formal: Sales harus segera follow up nasabah.
```

---

## 9. Dataset Dummy

Folder `sample_data` berisi data dummy untuk testing:

```text
sales_field_intelligence_dummy_testing.xlsx
```

Data ini bersifat sintetis dan tidak menggunakan data nasabah atau karyawan asli.

Sheet utama yang digunakan:

```text
Pipeline_Activity_Data
```

---

## 10. Knowledge Base Default

Folder `knowledge_base` berisi contoh knowledge base default:

```text
default_sales_field_knowledge.md
```

Dokumen ini dapat digunakan untuk menguji fitur RAG Knowledge Base.

---

## 11. API Key dan Security

Aplikasi tidak menyimpan API Key ke repository. API Key dimasukkan langsung melalui input password di sidebar Streamlit.

Jangan commit file berikut ke GitHub:

```text
.streamlit/secrets.toml
.env
*.key
```

Jangan menuliskan API Key atau token di:

- `app.py`
- `README.md`
- notebook Colab
- file konfigurasi publik

---

## 12. Anti-Hallucination Rules

Chatbot tidak boleh mengarang:

- angka
- nama Sales
- nama Supervisor
- nama Region
- penyebab masalah
- hasil analisis yang tidak tersedia di data

Jika data tidak cukup, chatbot wajib menyampaikan keterbatasan analisis.

---

## 13. Final Test Scenario

Gunakan prompt berikut untuk menguji aplikasi:

| Test | Prompt | Expected Route |
|---|---|---|
| Excel Summary | Berdasarkan data Excel, buatkan ringkasan pipeline dan activity. | excel_analyzer_gemini |
| Coaching Sales | Sales mana yang perlu menjadi prioritas coaching berdasarkan data Excel? | excel_analyzer_gemini |
| Region Insight | Region mana yang perlu perhatian dari data ini? | excel_analyzer_gemini |
| RAG Definition | Apa itu Panas dalam pipeline? | gemini_rag |
| Light Task | Halo, jelaskan singkat chatbot ini bisa bantu apa? | groq_light atau gemini_direct_no_groq |
| Anti-Hallucination | Sebutkan penyebab pasti semua pipeline gagal cair. | Chatbot tidak boleh mengarang penyebab pasti |

---

## 14. Deployment Streamlit Cloud

1. Upload project ke GitHub.
2. Buka Streamlit Community Cloud.
3. Pilih repository project.
4. Pilih branch utama, misalnya `main`.
5. Set main file path ke:

```text
app.py
```

6. Klik **Deploy**.

Karena API Key dimasukkan lewat UI, Streamlit Secrets tidak wajib digunakan.

---

## 15. Status Project

Project ini dibuat sebagai final project AI chatbot dengan integrasi data pipeline/activity dan knowledge base.

Status final:

- Streamlit UI siap digunakan
- Excel Analyzer aktif
- RAG Knowledge Base aktif
- Gemini/Groq Router aktif
- Demo Colab + NGROK tersedia
- Dummy data tersedia
- README dan struktur project siap untuk GitHub
