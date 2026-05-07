# Resume Proxy Chatbot

An AI-powered chatbot that acts as your professional proxy to recruiters.
Built with FastAPI + Claude API. Deployable in minutes.

---

## Project Structure

```
resume-proxy/
├── main.py          ← FastAPI backend + API route
├── profile.md       ← YOUR resume/profile (edit this!)
├── static/
│   └── index.html   ← Chat UI (no framework needed)
├── requirements.txt
├── Procfile         ← For Railway / Render deploy
└── README.md
```

---

## Setup (Local)

### 1. Get your Gemini API key
Sign up at https://aistudio.google.com and create an API key.

### 2. Clone / download this project
```bash
cd resume-proxy
```

### 3. Create a virtual environment
```bash
python -m venv venv
source venv/bin/activate      # Mac/Linux
venv\Scripts\activate         # Windows
```

### 4. Install dependencies
```bash
pip install -r requirements.txt
```

### 5. Set your API key
```bash
export GEMINI_API_KEY=AIza...   # Mac/Linux
set GEMINI_API_KEY=AIza...      # Windows
```

### 6. Edit your profile
Open `profile.md` and replace the template content with your actual resume.
The more detail you add, the better the AI will answer questions.

### 7. Run locally
```bash
uvicorn main:app --reload
```

Open http://localhost:8000 in your browser. You're live!

---

## Customisation Tips

### Tune the AI's persona
Edit the `SYSTEM_PROMPT_TEMPLATE` in `main.py` to change tone, add rules,
or adjust how it handles questions it can't answer.

### Add your photo / name to the UI
Edit `static/index.html`:
- Change `[Your Name]` to your actual name in the `<title>` and `<h1>`
- Change the avatar letter (`A`) to your initial
- Adjust the suggestion chips to reflect your actual profile


---

## How it works

1. Your `profile.md` is loaded into Gemini's system prompt on every request
2. The recruiter's question + conversation history is sent to Gemini
3. Gemini responds in first person, as your proxy
4. Responses stream back token-by-token for a smooth chat feel

No database, no vector store, no embeddings needed —
your profile is small enough to fit directly in Gemini's context window.
