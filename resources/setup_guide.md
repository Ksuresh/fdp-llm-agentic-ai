# Pre-work Setup Guide for Faculty

Please complete this **before Day 1** of the FDP. It takes about 30–45 minutes.

---

## ✅ Checklist

### Step 1 — Install Python 3.11+

Check your version:
```bash
python --version
```
If below 3.11, download from [python.org](https://www.python.org/downloads/).

---

### Step 2 — Install VS Code + Jupyter extension

1. Download VS Code: [code.visualstudio.com](https://code.visualstudio.com)
2. Install the **Jupyter** extension (search in Extensions sidebar)
3. Install the **Python** extension

> **Alternative:** Use [Google Colab](https://colab.research.google.com) — no local setup needed. All notebooks have an "Open in Colab" button.

---

### Step 3 — Clone the FDP repository

```bash
git clone https://github.com/Ksuresh/fdp-llm-agentic-ai.git
cd fdp-llm-agentic-ai
```

If you don't have Git: [git-scm.com/downloads](https://git-scm.com/downloads)

---

### Step 4 — Create virtual environment & install packages

```bash
python -m venv venv

# Mac/Linux:
source venv/bin/activate

# Windows:
venv\Scripts\activate

pip install -r requirements.txt
```

This will take 5–10 minutes. Make sure you have a stable internet connection.

---

### Step 5 — Install Ollama (for local open-source models)

1. Download from [ollama.com](https://ollama.com)
2. After install, open Terminal and run:
```bash
ollama pull llama3.2
```
This downloads a ~2GB local AI model. Do this on good Wi-Fi.

To verify it works:
```bash
ollama run llama3.2
# Type "hello" and press Enter — you should get a response
# Press Ctrl+D to exit
```

---

### Step 6 — Create API accounts (free tiers available)

| Provider | Sign Up | What For |
|----------|---------|---------|
| **OpenAI** | [platform.openai.com](https://platform.openai.com) | GPT-4o API calls |
| **Anthropic** | [console.anthropic.com](https://console.anthropic.com) | Claude API calls |
| **Google AI Studio** | [aistudio.google.com](https://aistudio.google.com) | Gemini API (free tier) |
| **HuggingFace** | [huggingface.co](https://huggingface.co) | Open-source models |

> **Tip:** OpenAI requires a minimum ₹500 credit top-up. Total usage across all 5 days should stay under ₹200. Always use `gpt-4o-mini` (not `gpt-4o`) when experimenting.

---

### Step 7 — Set up your .env file

```bash
cp .env.example .env
```

Open `.env` in any text editor and paste in your API keys.

---

### Step 8 — Verify everything works

Run this quick test in your terminal:

```bash
python -c "
import openai, anthropic, dotenv, langchain
print('All imports OK')
"
```

If you see `All imports OK` — you're ready for Day 1! 🎉

---

## 🆘 Troubleshooting

**`pip install` fails** → Try `pip install -r requirements.txt --user`

**Ollama not found after install** → Restart your terminal

**API key not working** → Make sure there are no spaces around the `=` in your `.env` file

**Windows path issues** → Use PowerShell, not Command Prompt

Still stuck? Raise an [Issue on GitHub](https://github.com/Ksuresh/fdp-llm-agentic-ai/issues) and tag it `setup-help`.

---

## 💻 Minimum Hardware Requirements

| | Minimum | Recommended |
|--|---------|-------------|
| RAM | 8 GB | 16 GB |
| Storage | 10 GB free | 20 GB free |
| OS | Windows 10 / macOS 12 / Ubuntu 20 | Latest |
| Internet | Required for API calls | Stable broadband |

> GPU is **not required** — all heavy compute runs in the cloud via APIs or Google Colab.
