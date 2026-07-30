# 🚀 AI-Powered Recruitment & Hiring Platform

An end-to-end AI Recruitment Automation System built with **n8n**, **Google Gemini AI**, **PostgreSQL (Supabase)**, and **Google Workspace APIs**.

The platform automates the complete recruitment lifecycle—from candidate registration to AI resume screening, HR approval, interview scheduling, offer letter generation, and recruitment analytics—while ensuring HR remains in control of all final hiring decisions.

---

# 📖 Project Overview

Recruitment involves multiple repetitive tasks such as collecting resumes, screening candidates, coordinating approvals, scheduling interviews, and generating offer letters.

This project automates those processes using **five interconnected n8n workflows**.

Instead of building one massive workflow, the system is divided into independent automation pipelines connected through the candidate status stored in PostgreSQL.

This makes the project modular, scalable, and easy to maintain.

---

# 🏗 System Architecture

```
Candidate Application
        │
        ▼
Workflow 1
Candidate Registration & Resume Collection
        │
        ▼
Workflow 2
Resume Parsing & AI Evaluation
        │
        ▼
Workflow 3
Candidate Shortlisting & HR Approval
        │
        ▼
Workflow 4
Interview Scheduling & Notifications
        │
        ▼
Workflow 5
Offer Letter Generation & Recruitment Analytics
```

---

# 📌 Workflow 1 — Candidate Registration & Resume Collection

### Purpose

Collect candidate applications and store them securely.

### Features

- Accepts candidate applications via Webhook
- Uploads resumes to Google Drive
- Stores candidate information in PostgreSQL
- Associates candidates with job openings
- Prevents duplicate registrations
- Sends confirmation email to candidates

---

# 🤖 Workflow 2 — Resume Parsing & AI Evaluation

### Purpose

Automatically evaluate candidate resumes using AI.

### Features

- Downloads resumes from Google Drive
- Extracts resume text
- Uses **Google Gemini AI**
- Compares resumes against job descriptions
- Generates:
  - AI Score
  - AI Summary
  - Extracted Skills
  - Candidate Strengths
  - Candidate Weaknesses
- Saves evaluation into PostgreSQL

---

# ✅ Workflow 3 — Candidate Shortlisting & HR Approval

### Purpose

Allow HR to approve AI-recommended candidates.

### Features

- Retrieves candidates above the AI threshold
- Creates approval requests
- Emails HR managers
- HR approves/rejects candidates using Webhooks
- Updates candidate status automatically

This keeps a **human in the loop** instead of allowing AI to make hiring decisions independently.

---

# 📅 Workflow 4 — Interview Scheduling & Notifications

### Purpose

Automatically schedule interviews for approved candidates.

### Features

- Checks interviewer availability
- Creates Google Calendar events
- Sends interview invitations
- Sends reminder emails
- Updates interview records in PostgreSQL

---

# 📄 Workflow 5 — Offer Letter Generation & Recruitment Analytics

### Purpose

Automate the final recruitment stage.

### Features

### Offer Letter

- Receives interview feedback
- Evaluates final interview score
- Generates personalized offer letters
- Creates Google Docs offer letters
- Sends offer emails
- Marks rejected candidates automatically

### Recruitment Analytics

Runs weekly and:

- Generates recruitment statistics
- Updates Google Sheets dashboard
- Sends recruitment reports to management

---

# 🛠 Tech Stack

## Automation

- n8n

## AI

- Google Gemini AI

## Database

- PostgreSQL
- Supabase

## Google Workspace

- Google Drive API
- Google Docs API
- Google Calendar API
- Google Sheets API
- Gmail API

## Other

- Webhooks
- JSON
- REST APIs

---

# 🗄 Database

### Main Tables

- candidates
- jobs
- interviews
- hr_approvals
- offers
- activity_log

### Reporting View

- recruitment_funnel

---

# ⚙ Installation

## 1. Clone Repository

```bash
git clone https://github.com/YOUR_USERNAME/AI-Recruitment-System.git
```

## 2. Setup Database

Run:

```sql
schema.sql
```

inside your PostgreSQL or Supabase instance.

## 3. Configure Credentials in n8n

Create credentials for:

- PostgreSQL
- Google Drive
- Gmail
- Google Calendar
- Google Docs
- Google Sheets
- Google Gemini API

## 4. Import Workflows

Import the five workflow JSON files into n8n.

```
workflows/
├── 1_candidate_registration.json
├── 2_resume_parsing_ai_evaluation.json
├── 3_shortlisting_hr_approval.json
├── 4_interview_scheduling.json
└── 5_offer_generation_analytics.json
```

## 5. Replace Configuration Values

Update:

- Google Drive Folder IDs
- Google Docs Template ID
- Google Sheets ID
- Gmail addresses
- Webhook URLs

---

# 📂 Repository Structure

```
.
├── schema.sql
├── README.md
├── workflows/
│   ├── 1_candidate_registration.json
│   ├── 2_resume_parsing_ai_evaluation.json
│   ├── 3_shortlisting_hr_approval.json
│   ├── 4_interview_scheduling.json
│   └── 5_offer_generation_analytics.json
```

---

# ⭐ Features

- AI Resume Screening
- Resume Parsing
- Candidate Scoring
- Human-in-the-loop HR Approval
- Interview Scheduling
- Google Calendar Integration
- Offer Letter Generation
- Recruitment Analytics Dashboard
- Weekly Reports
- Email Automation
- Cloud File Storage
- Modular Workflow Architecture

---

# 💡 Design Decisions

Instead of creating one large workflow, the recruitment pipeline is divided into five independent workflows.

Each workflow monitors candidates based on their **status** stored in PostgreSQL.

Advantages:

- Easier debugging
- Independent deployment
- Better scalability
- Easier maintenance
- Modular architecture

---

# 🚀 Future Improvements

- Slack Integration
- Microsoft Teams Integration
- WhatsApp Notifications
- Candidate Portal
- Recruiter Dashboard
- AI Interview Analysis
- Resume Ranking Dashboard
- OCR Support for Image-based Resumes

---

# 👨‍💻 Author

**Rishabh**

AI & Backend Developer

- LinkedIn: *(Add your LinkedIn profile URL)*
- GitHub: *(Add your GitHub profile URL)*

---

# 📄 License

This project is licensed under the MIT License.
