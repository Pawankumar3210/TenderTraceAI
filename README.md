# 📋 TenderTrace AI

> **From Documents to Decisions**

TenderTrace AI is an AI-powered tender evaluation platform for government procurement. It reads a tender document, extracts eligibility criteria, checks each bidder's documents against those criteria and gives explainable verdicts that officers can audit and trust.

Built for **Solution Challenge 2026** (AI-Based Tender Evaluation for CRPF Government Procurement).

🌐 **Backend API:** [pawan0123-tendertrace-backend.hf.space](https://pawan0123-tendertrace-backend.hf.space)

---

## ✨ Features

1. 📄 **Tender Document Upload** — Upload a tender PDF and extract eligibility criteria automatically
2. 👥 **Multiple Bidder Submissions** — Add several bidders, each with their own name and document
3. 🤖 **Auto Criteria Extraction** — Pulls out turnover, certifications, experience and compliance rules
4. ⚖️ **Mandatory vs Optional** — Clearly marks must-have and nice-to-have criteria
5. ✅ **Eligibility Verdicts** — Eligible, Not Eligible or Needs Review for every bidder
6. 🔍 **Explainable Decisions** — Shows the source document, the value found and the reasoning
7. 🚩 **Ambiguous Case Flagging** — Unclear cases are flagged for human review, never silently rejected
8. 🖼️ **Scanned Document Handling** — Scanned or image-based documents are flagged for manual review (full OCR via Google Cloud Vision is planned)
9. 📑 **PDF Report Export** — Consolidated evaluation report generated with ReportLab
10. 🧾 **Audit Trail** — Every action is logged with a timestamp
11. 📊 **Dashboard** — Visual overview of all bidders and their status
12. ⚔️ **Side-by-Side Comparison** — Compare all bidders against every criterion
13. 📈 **Confidence Scores** — Shows how confident the system is in each decision

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Frontend | React.js (Premium Legal Dark theme) |
| Backend | FastAPI (Python) |
| AI | Google Gemini 2.0 Flash |
| Fallback | Rule-based keyword and regex extraction (GST, ISO, turnover, experience) |
| PDF Parsing | PyMuPDF |
| Reports | ReportLab |
| Deployment | Hugging Face Spaces (backend), Vercel (frontend) |

When the Gemini quota is exhausted, the backend switches automatically to a smart fallback that reads the real PDF text, so evaluations never fail or time out.

---

## 📁 Project Structure

```
TenderTrace-AI/
├── backend/
│   ├── main.py
│   ├── requirements.txt
│   ├── Dockerfile
│   └── routes/
│       ├── tender.py
│       ├── evaluate.py
│       └── report.py
├── frontend/
│   ├── public/
│   └── src/
│       ├── App.js
│       └── App.css
└── README.md
```

---

## 🚀 Getting Started

### Backend

```bash
cd backend
pip install -r requirements.txt
uvicorn main:app --reload
```

Create a `.env` file inside `backend/`:

```env
GEMINI_API_KEY=your_gemini_api_key
```

### Frontend

```bash
cd frontend
npm install --legacy-peer-deps
npm start
```

In `frontend/src/App.js`, set the backend URL:

```javascript
const API = "http://127.0.0.1:8000";
```

Open [http://localhost:3000](http://localhost:3000).

---

## 🔌 API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| POST | `/tender/upload` | Upload a tender PDF and extract criteria |
| POST | `/tender/demo` | Load demo tender data |
| POST | `/evaluate/upload-bidder` | Evaluate a bidder document against the tender |
| POST | `/evaluate/demo` | Run a demo evaluation |
| DELETE | `/evaluate/clear` | Clear all evaluations |
| GET | `/report/generate` | Download the PDF report |

---

## 🌐 Deployment

- **Backend:** Hugging Face Spaces (Docker, port 7860)
- **Frontend:** Vercel (Create React App, root directory `frontend`)

---

<div align="center">
  <strong>Every verdict is explainable and audit-ready.</strong>
</div>
