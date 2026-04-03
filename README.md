# AI_EVALUATOR
# 🎓 SmartGrade AI — Automated Answer Sheet Evaluator

[![Live Demo](https://img.shields.io/badge/Live%20Demo-AWS-orange?style=for-the-badge&logo=amazon-aws)](http://54.196.215.244:8501/)
[![Hackathon](https://img.shields.io/badge/Hackathon-AI%20Powered%20Tools-blue?style=for-the-badge)](.)
[![Python](https://img.shields.io/badge/Python-3.10+-green?style=for-the-badge&logo=python)](https://www.python.org/)
[![Streamlit](https://img.shields.io/badge/Streamlit-1.35+-red?style=for-the-badge&logo=streamlit)](https://streamlit.io/)

> **Intelligent answer sheet evaluation powered by AI — eliminating manual grading bottlenecks**

---

## 🌟 Overview

**SmartGrade AI** is an AI-powered evaluation system that automates the tedious process of grading student answer sheets. Built for the **AI-Powered Everyday Tools Hackathon**, it leverages Large Language Models (LLMs) to evaluate conceptual understanding, assign marks, and provide detailed feedback — all in seconds.

### 🎯 Problem Statement

Traditional manual grading is:
- ⏰ **Time-consuming**: Hours spent reading and scoring each paper
- 😰 **Inconsistent**: Human fatigue leads to subjective scoring
- 📊 **Non-scalable**: Bottleneck for large batches of students

### 💡 Our Solution

An intelligent system that:
- ✅ Automatically parses questions and detects mark allocations
- ✅ Evaluates answers using AI (Groq LLaMA 3.3 70B)
- ✅ Provides similarity scores and detailed feedback
- ✅ Supports handwritten answer sheets via Vision OCR
- ✅ Generates professional PDF reports

---

## 🚀 Live Demo

**🌐 Try it now:** [http://54.196.215.244:8501/](http://54.196.215.244:8501/)

Access the deployed application on AWS and evaluate answer sheets instantly!

---

## ✨ Features

### 📥 **Multi-Format Input**
- ✏️ Manual text entry for quick testing
- 📄 PDF upload with automatic text extraction
- 📷 Image upload with Vision OCR (supports handwritten papers)

### 🤖 **AI-Powered Evaluation**
- **Model**: Groq LLaMA 3.3 70B (free tier)
- **Intelligent scoring**: Evaluates conceptual understanding, not just keyword matching
- **Similarity scoring**: 0-100% match score per question
- **Detailed feedback**: Key points covered + missing points

### 🎚️ **Configurable Grading**
- **3 Strictness Levels**:
  - **Lenient**: Credit for basic understanding
  - **Moderate**: Require clear explanations
  - **Strict**: Demand complete, detailed answers
- **Partial Credit**: Toggle on/off
- **Custom Grade Thresholds**: Adjust A/B/C/D boundaries

### 📊 **Visual Dashboard**
- Score ring with color-coded grades (A–F)
- Breakdown chart (Full / Partial / Zero marks)
- Per-question analysis with similarity scores
- Overall performance feedback

### 📄 **PDF Report Export**
- Professional evaluation report
- Summary table with score, grade, model, strictness
- Question-wise breakdown with feedback
- Covered/missing points per question

---

## 🛠️ Tech Stack

| Component | Technology |
|---|---|
| **Frontend** | Streamlit 1.35+ |
| **AI/LLM** | Groq API (LLaMA 3.3 70B) |
| **OCR (Handwriting)** | Groq Vision Model + Pytesseract fallback |
| **PDF Processing** | PyMuPDF (fitz) |
| **Report Generation** | ReportLab |
| **Deployment** | AWS EC2 |
| **Language** | Python 3.10+ |

---

## 📦 Installation

### Prerequisites
- Python 3.10 or higher
- Groq API key ([Get free key](https://console.groq.com))

### Steps

1. **Clone the repository**
```bash
git clone <your-repo-url>
cd smartgrade-ai
```

2. **Install dependencies**
```bash
pip install -r requirements.txt
```

3. **Install Tesseract OCR** (for image fallback)
   - **Ubuntu/Debian**: `sudo apt install tesseract-ocr`
   - **macOS**: `brew install tesseract`
   - **Windows**: [Download installer](https://github.com/UB-Mannheim/tesseract/wiki)

4. **Run the application**
```bash
streamlit run app.py
```

5. **Access locally**
   - Open your browser and navigate to `http://localhost:8501`

---

## 🔑 Getting Your Groq API Key

1. Visit [console.groq.com](https://console.groq.com)
2. Sign up / Log in with your account
3. Navigate to **API Keys** section
4. Click **Create API Key**
5. Copy the key (starts with `gsk_...`)
6. Paste it into the sidebar in SmartGrade AI

> **Note**: Groq offers a generous free tier — no credit card required!

---

## 📖 Usage Guide

### Basic Workflow

1. **Enter API Key**: Paste your Groq API key in the sidebar
2. **Configure Settings**:
   - Select model (recommended: `llama-3.3-70b-versatile`)
   - Set grading scale thresholds (A/B/C/D)
   - Choose strictness level
   - Toggle partial credit on/off
3. **Input Question Paper & Answer Sheet**:
   - **Option A**: Paste text directly
   - **Option B**: Upload PDF/image files
4. **Evaluate**: Click "🚀 Evaluate Answer Sheet"
5. **Review Results**:
   - View score, grade, and breakdown
   - Expand questions for detailed analysis
   - Download PDF report

### Supported File Formats

| Format | Question Paper | Answer Sheet |
|---|---|---|
| Plain Text (.txt) | ✅ | ✅ |
| PDF (.pdf) | ✅ | ✅ |
| Images (.jpg, .png) | ✅ | ✅ (with OCR) |

---

## 📁 Project Structure

```
smartgrade-ai/
├── app.py                  # Main Streamlit application
├── evaluator.py            # AI evaluation engine (Groq API integration)
├── utils.py                # File extraction & PDF report generation
├── requirements.txt        # Python dependencies
└── README.md               # This file
```

### Key Files

- **`app.py`**: Streamlit UI with dark theme, input handlers, result visualization
- **`evaluator.py`**: Core logic — sends prompts to Groq, parses JSON responses, computes scores
- **`utils.py`**: Handles PDF/image text extraction (Vision OCR) and PDF report generation

---

## 👥 Team

**AI Evaluator Team** — Hackathon 2025

| Member | Role |
|---|---|
| Gattadi Praneesh | Team Lead / Full Stack |
| Vadla Navadeep | AI / Backend Developer |
| Male Bhadrinath | Frontend / UI Developer |
| Veerla Sai Gangadhar | Integration / Testing |

---

## 🎯 How It Works

### Evaluation Pipeline

```
┌─────────────────────────┐
│  Question Paper +       │
│  Student Answer Sheet   │
└───────────┬─────────────┘
            │
            ▼
┌─────────────────────────┐
│  Text Extraction        │
│  (PDF/Image OCR)        │
└───────────┬─────────────┘
            │
            ▼
┌─────────────────────────┐
│  AI Prompt Engineering  │
│  (Groq LLaMA 3.3)       │
└───────────┬─────────────┘
            │
            ▼
┌─────────────────────────┐
│  Structured JSON Output │
│  (Questions + Scores)   │
└───────────┬─────────────┘
            │
            ▼
┌─────────────────────────┐
│  Visual Dashboard +     │
│  PDF Report Generation  │
└─────────────────────────┘
```

### AI Prompt Strategy

The evaluator uses carefully crafted prompts with:
- **Strictness rules**: Explicit scoring bands for Lenient/Moderate/Strict
- **Mark detection**: Auto-parses `(5 marks)`, `[3]`, etc.
- **JSON enforcement**: Structured output for reliable parsing
- **Feedback generation**: AI explains what was covered/missing

---

## 🔮 Future Enhancements

- [ ] **Batch Processing**: Evaluate multiple students simultaneously
- [ ] **Reference Answers**: Upload ideal answers for more precise scoring
- [ ] **Multi-language Support**: Evaluate papers in Hindi, Telugu, etc.
- [ ] **Teacher Dashboard**: Class-wide analytics and trends
- [ ] **LMS Integration**: Connect with Moodle, Canvas, Google Classroom
- [ ] **Mobile App**: iOS/Android for on-the-go evaluation

---

## 🐛 Known Limitations

- **Handwriting OCR**: Accuracy depends on legibility; unclear handwriting may need manual correction
- **Internet Required**: Groq API calls need active internet connection
- **API Rate Limits**: Free tier has request limits (usually sufficient for hackathon demos)

---

## 📜 License

This project was created for the **AI-Powered Everyday Tools Hackathon 2025**.

For educational and demonstration purposes.

---

## 🙏 Acknowledgments

- **Groq** for providing free-tier access to LLaMA models
- **Streamlit** for the rapid prototyping framework
- **ReportLab** for PDF generation capabilities
- **PyMuPDF** for PDF text extraction

---

## 📞 Contact & Support

- **Live Demo**: [http://54.196.215.244:8501/](http://54.196.215.244:8501/)
- **Issues**: Open an issue in the repository
- **Hackathon Theme**: AI-Powered Everyday Tools

---

## 🚀 Quick Start Commands

```bash
# Install dependencies
pip install -r requirements.txt

# Run locally
streamlit run app.py

# Access at http://localhost:8501
```

---

<div align="center">

**Built with ❤️ by Team AI Evaluator | Hackathon 2025**

⭐ Star this repo if you found it helpful!

</div>
