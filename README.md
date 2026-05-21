# 🚀 Google ADK – End-to-End Setup & Deployment Guide

> **Build, Run, and Deploy AI Agents using Google ADK with Google AI & Vertex AI**  
> Beginner-friendly setup guide for **Cloud Shell**, **VS Code**, and **Agent Engine Deployment**

![Python](https://img.shields.io/badge/Python-3.10+-blue)
![Google ADK](https://img.shields.io/badge/Google-ADK-green)
![Vertex AI](https://img.shields.io/badge/Vertex-AI-orange)
![Status](https://img.shields.io/badge/Status-Working-success)

---

# 📌 Project Overview

This repository demonstrates how to:

✅ Set up **Google ADK** in Cloud Shell and VS Code  
✅ Create your **first AI agent**  
✅ Use **Google AI backend**  
✅ Use **Vertex AI backend**  
✅ Run agents locally using **Web UI** and terminal  
✅ Deploy agents to **Agent Engine**  
✅ Troubleshoot common issues  

---

# 🏗 Architecture

```text
User Prompt
   ↓
Google ADK Agent
   ↓
Backend Selection
 ┌───────────────┬────────────────┐
 │ Google AI     │ Vertex AI      │
 │ (API Key)     │ (GCP Project)  │
 └───────────────┴────────────────┘
   ↓
ADK Web / ADK Run
   ↓
Optional Deployment
   ↓
Agent Engine
```

---

# 📂 Project Structure

```text
ADK_DEMO/
│
├── .env
├── README.md
├── .gitignore
│
├── testAgent/
│   ├── firstAgent/
│   │   ├── __init__.py
│   │   ├── agent.py
│   │   └── .env
│   │
│   └── secondAgent/
│       ├── __init__.py
│       ├── agent.py
│       └── .env
│
└── adk/ (virtual environment)
```

---

# ⚙️ Prerequisites

Before you begin, make sure you have:

- Python **3.10+**
- Google Cloud account
- Google AI Studio API Key
- Google Cloud project
- `gcloud` CLI installed
- VS Code
- Internet connection

---

# ☁️ Google Cloud Shell Setup (Google AI Backend)

## 1️⃣ Create Working Directory

```bash
mkdir adk
cd adk
```

---

## 2️⃣ Install Google ADK

```bash
pip install google-adk
pip show google-adk
```

---

## 3️⃣ Create Agent Workspace

```bash
mkdir test-agent
cd test-agent
```

---

## 4️⃣ Add ADK to PATH

```bash
export PATH=$PATH:$HOME/.local/bin
```

---

## 5️⃣ Create First Agent

```bash
adk create firstAgent
```

### Choose:

```text
Model → gemini-2.5-flash
Backend → Google AI
```

Enter:

```text
Google API Key
```

---

## 6️⃣ Update Environment Variables

Edit:

```bash
vi .env
```

Useful commands:

| Command | Action |
|---|---|
| `i` | Insert |
| `Esc` | Exit insert |
| `dd` | Delete line |
| `:wq` | Save and quit |
| `:q!` | Quit without saving |

---

## 7️⃣ Run Agent

### Web UI

```bash
adk web
```

### Terminal mode

```bash
adk run firstAgent
```

---

# 💻 VS Code Setup (Windows – Google AI Backend)

## 1️⃣ Create Virtual Environment

```powershell
python -m venv adk
.\adk\Scripts\activate
```

---

## 2️⃣ Install Google ADK

```powershell
pip install --upgrade "google-cloud-aiplatform[agent_engines,adk]>=1.112"
```

---

## 3️⃣ Create Agent Folder

```powershell
mkdir testAgent
cd testAgent
```

---

## 4️⃣ Create First Agent

```powershell
adk create firstAgent
```

### Choose:

```text
Model → gemini-2.5-flash
Backend → Google AI
```

Enter:

```text
Google API Key
```

---

## 5️⃣ Run Agent

### Web UI

```powershell
adk web
```

### Terminal Mode

```powershell
adk run firstAgent
```

---

# 🔁 Vertex AI Backend Setup

## 1️⃣ Create Vertex AI Agent

```powershell
adk create secondAgent
```

Choose:

```text
Model → gemini-2.5-flash
Backend → Vertex AI
```

Provide:

- Google Cloud Project ID
- Region (`us-central1`)

---

## 2️⃣ Authenticate

```powershell
gcloud auth application-default login
```

---

## 3️⃣ Run Agent

```powershell
adk web
```

or

```powershell
adk run secondAgent
```

---

# 🚀 Deploy to Agent Engine

---

## Reference Labs

### Skills Boost Lab

Deploy ADK Agents to Agent Engine

https://www.skills.google/catalog_lab/32019

---

### Official Quickstart

https://docs.cloud.google.com/agent-builder/agent-engine/quickstart-adk

---

## 1️⃣ Create Storage Bucket

Example:

```text
adk_agent_deploy002xxxxx
```

---

## 2️⃣ Update `.env`

```env
# GOOGLE_GENAI_USE_VERTEXAI=0
# GOOGLE_API_KEY=YOUR_API_KEY

GOOGLE_CLOUD_PROJECT=your-project-id
GOOGLE_CLOUD_REGION=us-central1
```

---

## 3️⃣ Deploy Agent

```bash
adk deploy agent_engine firstAgent \
  --display_name="currency_agent_v2" \
  --project="your-project-id" \
  --region="us-central1"
```

---

## 4️⃣ Invoke Deployed Agent

Use a Python client to:

- Authenticate
- Call endpoint
- Send prompt
- Receive response

---

# 🛠 Troubleshooting

---

## Port 8000 already in use

Error:

```text
WinError 10048
```

Find process:

```powershell
netstat -ano | findstr :8000
```

Kill:

```powershell
taskkill /PID <PID> /F
```

Alternative:

```powershell
adk web --port 8001
```

---

## root_agent not found

Check:

### `agent.py`

```python
root_agent = Agent(...)
```

### `__init__.py`

```python
from .agent import root_agent
```

---

## Authentication error

Run:

```powershell
gcloud auth application-default login
```

---

# 📦 Recommended `.gitignore`

```gitignore
adk/
.env
.adk/
__pycache__/
*.pyc
```

---

# 🔑 Common Commands

### Activate Virtual Environment

```powershell
.\adk\Scripts\activate
```

---

### Deactivate

```powershell
deactivate
```

---

### Run Web UI

```powershell
adk web


### Run on another port

```powershell
adk web --port 8001
```

---

# 📚 Key Learnings

- Google ADK basics
- Agent creation
- Google AI backend
- Vertex AI backend
- Agent Engine deployment
- Web UI debugging
- Port troubleshooting
- Environment setup


Cloud & AI Trainer | Google Cloud Certified | Generative AI Enthusiast  

> Building AI agents with Google ADK 🚀
