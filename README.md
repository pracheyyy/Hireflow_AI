
# HireFlow AI — AI-Powered Placement Preparation Platform

**Build skills. Find your flow. Prepare for your next opportunity.**

HireFlow AI is a personalized placement preparation platform designed to help students organize their learning, improve their profiles, prepare for interviews, and track their career-readiness journey — all from one workspace.

Instead of managing preparation across multiple disconnected tools, students can use HireFlow AI to create structured learning plans, manage daily goals, evaluate resumes, explore career opportunities, and receive AI-powered guidance.

---

## 1. Overview

Placement preparation can become overwhelming when students have to manage DSA practice, core subjects, aptitude, resume building, interviews, and internship applications separately.

HireFlow AI brings these activities together in a single preparation workspace.

The platform helps students:

- Understand what to learn next.
- Create personalized preparation roadmaps.
- Break large goals into manageable daily tasks.
- Monitor learning and syllabus completion.
- Identify opportunities to improve their resumes.
- Discover internships and entry-level opportunities.
- Get personalized preparation guidance through an AI assistant.

**Our goal:** Make placement preparation more organized, consistent, and accessible.


##
<!-- <img width="1731" height="1288" alt="image" src="https://github.com/user-attachments/assets/660081d2-28df-468e-b161-a12335e4be10" /> -->
<img width="1731" height="1502" alt="image" src="https://github.com/user-attachments/assets/de268c0a-2f13-414f-bb58-86c912fd4e52" />


---

## 2. Key Features

### Personalized Placement Dashboard
- Centralized preparation workspace.
- Overview of DSA, core subjects, aptitude, and domain skills.
- Visual progress indicators.
- Daily task management.
- Personalized user profile.

### AI Preparation Planner
- Generates personalized learning roadmaps.
- Considers target role, experience level, available study hours, weak areas, and deadlines.
- Organizes preparation into structured daily activities.
- Supports flexible preparation durations.

### Structured Syllabus Tracker
Four major preparation areas:

| Workspace | Coverage |
|---|---|
| DSA | Data structures, algorithms, and interview practice |
| Core Subjects | Important computer science subjects |
| Domain Skills | Web Development, Cybersecurity, AI/ML, Java Backend, Data Science, Cloud/DevOps |
| Aptitude | Quantitative aptitude, reasoning, and related topics |

Additional capabilities:
- Topic-wise checklists.
- Add custom topics.
- Mark learning milestones as completed.
- Track progress across different domain selections.
- Retain previously saved progress.

### Daily Task Manager
- Create and manage daily preparation tasks.
- Mark tasks as completed.
- Maintain a task completion history.
- Record completion timestamps.
- Keep daily tasks separate from syllabus milestones.

### ATS-Style Resume Checker
- Upload PDF, DOCX, or TXT resumes.
- Compare resume content against a target job description.
- Identify matched and missing keywords.
- Highlight potential resume improvements.
- Generate AI-powered suggestions.

*The resume score is an advisory heuristic, not an official ATS score.*

### Career Opportunities
- Browse internship and fresher-level opportunities.
- Search and filter available listings.
- Save interesting opportunities.
- Track application statuses.

*Listings currently contain sample opportunity data. Always verify eligibility, deadlines, and availability on the original application page.*

### AI Preparation Assistant
- Ask questions about placement preparation and learning.
- Receive explanations and study guidance.
- Retrieve relevant information from uploaded study notes.
- Supports Markdown-formatted responses, including headings, lists, links, and code blocks.

### Retrieval-Augmented Generation (RAG)
The chatbot can use personal study materials as an additional knowledge source.

Supported formats:
- `.txt`
- `.md`

The retrieval system uses embeddings and FAISS when available, with keyword-based retrieval as a fallback.

### Authentication and Personal Workspace
- Sign-in and account creation.
- Account-based user identification.
- Personalized preparation data.
- Access to saved progress and tasks after signing in.

---

## 3. Platform Modules

| Module | Purpose |
|---|---|
| Dashboard | View overall preparation progress |
| DSA Workspace | Track DSA learning and interview practice |
| Core Subjects | Organize computer science subject preparation |
| Domain Skills | Select and track a career-related domain |
| Aptitude | Monitor aptitude preparation |
| Daily To-Do | Manage everyday learning goals |
| AI Planner | Generate personalized preparation roadmaps |
| Resume Checker | Review resumes against job descriptions |
| Opportunities | Explore and manage career opportunities |
| AI Chatbot | Receive preparation assistance |

---

## 4. Technology Stack

| Layer | Technologies |
|---|---|
| Frontend | HTML5, CSS3, JavaScript |
| Backend | Python, FastAPI |
| AI Integration | Google Gemini, LangChain |
| RAG | HuggingFace Embeddings, FAISS |
| Document Processing | PDF, DOCX, TXT extraction |
| Data Management | JSON-based application storage |
| Development Tools | VS Code, Git, GitHub, Postman |

---

## 5. Project Structure

```text
Hireflow_AI/
│
├── main.py
├── requirements.txt
├── README.md
├── .env.example
├── .gitignore
│
├── data/
│   ├── app_data.json
│   └── knowledge_base/
│       ├── notes.txt
│       └── study_material.md
│
└── static/
    ├── landing.html
    ├── landing.css
    ├── login.html
    ├── index.html
    ├── style.css
    ├── app.js
    └── app_old.js
```

*The structure above represents the main application files. Runtime-generated files and additional directories may vary.*

---

## 6. Getting Started

Follow these steps to run HireFlow AI locally.

### Prerequisites

- Python 3.10 or higher.
- pip package manager.
- Git.
- Internet connection for dependency installation and Gemini API requests.
- Google Gemini API key for AI-powered features.

### Step 1: Clone the Repository

```bash
git clone YOUR_REPOSITORY_URL
cd Hireflow_AI
```

Replace `YOUR_REPOSITORY_URL` with your actual GitHub repository URL.

### Step 2: Create a Virtual Environment

**Windows PowerShell:**

```powershell
py -3.11 -m venv .venv
```

Activate it:

```powershell
.\.venv\Scripts\Activate.ps1
```

**macOS / Linux:**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### Step 3: Install Dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### Step 4: Configure Environment Variables

Create a `.env` file from the example:

**Windows:**

```powershell
Copy-Item .env.example .env
```

**macOS / Linux:**

```bash
cp .env.example .env
```

Add your Gemini API key to `.env`.

```env
GEMINI_API_KEY=your_gemini_api_key_here
```

Keep your API key private. Never commit `.env` to GitHub.

Get a Gemini API key:

https://aistudio.google.com/apikey

### Step 5: Run the Application

```bash
uvicorn main:app --reload
```

### Step 6: Open HireFlow AI

| Page | URL |
|---|---|
| Landing Page | http://127.0.0.1:8000/ |
| Login / Signup | http://127.0.0.1:8000/login |
| Dashboard | http://127.0.0.1:8000/dashboard |
| API Documentation | http://127.0.0.1:8000/docs |

---

## 7. Environment Configuration

The application requires a Gemini API key for its AI-powered functionality.

Example `.env.example`:

```env
GEMINI_API_KEY=your_gemini_api_key_here
```

If your authentication implementation uses additional environment variables, include their names in `.env.example` without publishing their actual values.

---

## 8. AI-Powered Features

### AI Planner

The planner generates a structured preparation roadmap using information such as:

- Target career role.
- Current preparation level.
- Available daily study hours.
- Current skills and weak areas.
- Preparation deadline.

The generated plan is normalized into structured daily activities for easier tracking.

### Resume Analysis

The resume checker:

1. Extracts content from an uploaded resume.
2. Processes the target job description.
3. Compares relevant keywords.
4. Identifies matched and missing terms.
5. Generates suggestions for improving the resume.

### RAG-Based Chatbot

The chatbot can retrieve relevant information from the user's uploaded notes before generating an answer.

**Knowledge-base directory:**

```text
data/
└── knowledge_base/
    ├── dsa_notes.txt
    ├── operating_systems.md
    └── interview_preparation.txt
```

Supported file types: `.txt` and `.md`.

Files can also be uploaded using the knowledge-base API.

Example:

```bash
curl -X POST http://127.0.0.1:8000/api/knowledge-base \
  -F "file=@your-notes.txt"
```

**Retrieval workflow:**

```text
User Question
     |
     v
Knowledge Base Retrieval
     |
     v
Relevant Study Notes
     |
     v
AI Response Generation
     |
     v
Formatted Chatbot Response
```

The first embedding-backed request may take longer because the sentence-transformer model may need to be downloaded.

If embedding initialization fails, the application can fall back to keyword-based retrieval.

If no knowledge-base files are available, the chatbot uses general knowledge and does not claim that local notes were retrieved.

---

## 9. API Reference

The following endpoints are part of the application API.

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/health` | Check backend and AI-key status |
| GET | `/api/data` | Retrieve dashboard data |
| PUT | `/api/data` | Update dashboard data |
| GET | `/api/opportunities` | Retrieve and filter opportunities |
| POST | `/api/plan` | Generate an AI preparation plan |
| POST | `/api/chat` | Send a chatbot question |
| POST | `/api/resume-text` | Extract resume text |
| POST | `/api/ats` | Analyze resume against a job description |
| POST | `/api/knowledge-base` | Upload study notes |

Authentication endpoints are also available for account registration and login.

For complete request and response schemas, open:

http://127.0.0.1:8000/docs

---

## 10. Data Management

HireFlow AI maintains preparation data separately from the frontend interface.

Current application data includes:

- Syllabus completion.
- Domain-specific progress.
- Daily tasks.
- Task completion history.
- AI-generated roadmaps.
- Profile information.
- Saved opportunities and application statuses.

Syllabus progress and daily task history are tracked separately to avoid mixing learning milestones with everyday tasks.

The current project uses JSON-based application storage. For production deployment, use a persistent database and secure storage configuration to protect user data and preserve it across application restarts.

---

## 11. Current Limitations

HireFlow AI is an evolving placement-preparation project. Some capabilities are still under development.

- Career opportunities currently use sample data rather than a live job-board integration.
- Resume scoring is heuristic and should not be treated as an official ATS evaluation.
- AI-generated suggestions may require manual review.
- RAG responses depend on the quality and relevance of uploaded notes.
- Gemini-powered features require a valid API key and internet access.
- Production deployment requires additional security, persistent storage, and infrastructure configuration.

---

## 12. Future Enhancements

Planned improvements include:

- Live internship and job-board integrations.
- More advanced resume-to-job matching.
- Interview preparation and mock interview modules.
- Personalized DSA practice recommendations.
- Enhanced analytics and learning insights.
- Improved roadmap customization.
- Production-grade database integration.
- Cloud deployment and performance optimization.
- Notifications and preparation reminders.

---


## Built with a goal to make placement preparation more focused and organized.

**HireFlow AI — Build skills. Find your flow.**
