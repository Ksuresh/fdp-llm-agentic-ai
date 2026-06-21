# Faculty Development Programme — Large Language Models & Agentic AI

> **5 Days · 30 Hours · Concept → Demo → Lab**

A hands-on Faculty Development Programme (FDP) covering the full stack of modern AI — from how LLMs work to building production-ready autonomous agents. Every session follows the same rhythm: understand the concept, see it run live, then build it yourself.

---

## 🗓️ Programme at a Glance

| Day | Theme | Key Topics |
|-----|-------|-----------|
| **Day 1** | LLM Foundations & Multimodal AI | How LLMs work · API calls · Prompt engineering · Multimodal AI · RAG |
| **Day 2** | Fine-tuning, Evaluation & No-code Agents | Fine-tuning (LoRA/QLoRA) · LLM Evaluation · Intro to Agentic AI · FlowiseAI · Agent ecosystem |
| **Day 3** | Coded Agents — OpenAI SDK & CrewAI | OpenAI Agents SDK · Multi-agent patterns · CrewAI · Flows |
| **Day 4** | AutoGen, LangChain & Deployment | Guest lecture · AutoGen · LangChain & LangGraph · Observability · Deployment |
| **Day 5** | MCP, Capstone & Future | Guest lecture · Model Context Protocol · Capstone presentations · Ethics |

---

## ⚙️ Setup — Do This Before Day 1

### 1. Clone this repository
```bash
git clone https://github.com/Ksuresh/fdp-llm-agentic-ai.git
cd fdp-llm-agentic-ai
```

### 2. Create a Python virtual environment
```bash
python -m venv venv
# On Mac/Linux:
source venv/bin/activate
# On Windows:
venv\Scripts\activate
```

### 3. Install all dependencies
```bash
pip install -r requirements.txt
```

### 4. Set up your API keys
```bash
cp .env.example .env
# Now open .env and fill in your API keys
```

### 5. Launch Jupyter
```bash
jupyter lab
```

> **Prefer Google Colab?** Each notebook has a "Open in Colab" badge at the top. No local setup needed — just a Google account.

---

## 🔑 API Keys You'll Need

| Provider | Used In | Get Key |
|----------|---------|---------|
| OpenAI | Days 1, 2, 3, 4 | [platform.openai.com](https://platform.openai.com) |
| Anthropic | Days 1, 5 | [console.anthropic.com](https://console.anthropic.com) |
| Google Gemini | Day 1 | [aistudio.google.com](https://aistudio.google.com) |
| HuggingFace | Day 2 | [huggingface.co/settings/tokens](https://huggingface.co/settings/tokens) |

> **Cost estimate:** Total API spend for all 5 days is typically under ₹500 (~$5 USD). Use the cheapest model variant when experimenting — `gpt-4o-mini` for OpenAI, `claude-haiku-4-5` for Anthropic.

---

## 📁 Repository Structure

```
fdp-llm-agentic-ai/
├── day1-llm-foundations/       ← Session notebooks for Day 1
│   ├── lab/                    ← Lab assignment + solution
│   └── data/                   ← Sample PDFs and datasets
├── day2-finetuning-agents/     ← Session notebooks for Day 2
├── day3-openai-crewai/         ← Session notebooks for Day 3
├── day4-autogen-langchain/     ← Session notebooks for Day 4
├── day5-mcp-capstone/          ← Session notebooks for Day 5
├── slides/                     ← All session slide decks (PPT)
├── resources/                  ← Setup guide, API guide, reading list
├── .env.example                ← API key template
└── requirements.txt            ← All Python dependencies
```

---

## 📓 Notebook Convention

Every notebook is structured the same way so you always know where you are:

```
Cell 1  — pip installs (run once)
Cell 2  — imports + load API keys from .env
Cells 3–N — concept demo with markdown explanations between blocks
Last cell — "Your Turn" — the mini-assignment prompt
```

Run cells top to bottom. Every notebook is self-contained.

---

## 🛠️ Tools & Frameworks Covered

| Category | Tools |
|----------|-------|
| Frontier LLMs | OpenAI GPT-4o · Anthropic Claude · Google Gemini |
| Open-source LLMs | Ollama · Mistral · LLaMA 3 (via HuggingFace) |
| RAG | FAISS · ChromaDB · LangChain |
| Fine-tuning | HuggingFace PEFT · LoRA · QLoRA (Google Colab) |
| Evaluation | RAGAS · LLM-as-a-judge |
| No-code Agents | FlowiseAI · n8n |
| Coded Agents | OpenAI Agents SDK · CrewAI · AutoGen · LangGraph |
| MCP | Model Context Protocol · Claude MCP server |
| Observability | LangSmith |

---

## 📚 Source Material

This FDP draws from two excellent courses by [Ed Donner](https://www.linkedin.com/in/eddonner/):
- [LLM Engineering — Master AI and LLMs](https://www.udemy.com/course/llm-engineering-master-ai-and-large-language-models) → code in [llm_engineering](https://github.com/ed-donner/llm_engineering)
- [The Complete Agentic AI Engineering Course](https://www.udemy.com/course/the-complete-agentic-ai-engineering-course/) → code in [agents](https://github.com/ed-donner/agents)

Examples have been simplified, contextualised for Indian academic settings, and adapted for a faculty audience.

---

## 🙋 Questions?

Raise an [Issue](https://github.com/Ksuresh/fdp-llm-agentic-ai/issues) on this repo or reach out to the programme coordinator.

---

*Programme designed for faculty of engineering and technology institutions. Participants are expected to be comfortable with Python basics.*
