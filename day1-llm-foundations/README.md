# Day 1 — LLM Foundations & Multimodal AI

> *From tokens to production-ready API calls*

---

## 🎯 Learning Goals

By end of Day 1 you will be able to:
- Explain how LLMs work — tokens, transformers, attention — without hand-waving
- Make API calls to frontier models (OpenAI, Anthropic, Gemini) and local open-source models (Ollama)
- Write effective prompts using zero-shot, few-shot, and chain-of-thought techniques
- Build a multimodal app that accepts images and documents as input
- Build a basic RAG pipeline that answers questions from your own PDF

---

## 📓 Notebooks — Run in Order

| # | Notebook | Source | Time |
|---|----------|--------|------|
| 01 | `01_how_llms_work.ipynb` | Adapted from llm_engineering/week1 | 45 min |
| 02 | `02_api_calls_frontier_opensource.ipynb` | Adapted from llm_engineering/week1 | 45 min |
| 03 | `03_prompt_engineering.ipynb` | Adapted from llm_engineering/week1 | 30 min |
| 04 | `04_multimodal_ai.ipynb` | Adapted from llm_engineering/week2 | 30 min |
| 05 | `05_rag_fundamentals.ipynb` | Adapted from llm_engineering/week5 | 45 min |

---

## 🧪 Lab Assignment

**File:** `lab/lab1_rag_chatbot.ipynb`

Build a RAG chatbot that answers questions from `data/sample_syllabus.pdf` (a sample college syllabus). Then swap in a PDF of your own choosing.

**Solution:** `lab/lab1_rag_chatbot_solution.ipynb` — don't peek until you've tried!

---

## 📰 AI Pulse — Discussion Topics

Two news stories are woven into today's sessions to spark discussion:

1. **The DeepSeek Shock** (after notebook 02) — How a Chinese startup matched GPT-4 for $5.6M and wiped $593B from Nvidia's market cap in a day
2. **How the Labs Train Differently** (after notebook 04) — OpenAI vs Anthropic vs Google vs DeepSeek — completely different philosophies

---

## 🔧 Prerequisites for Today

- `.env` file set up with `OPENAI_API_KEY` and `ANTHROPIC_API_KEY`
- Ollama installed and `llama3.2` pulled (`ollama pull llama3.2`)
- `pip install -r requirements.txt` completed

---

## 📎 Key Concepts Covered

`tokens` `embeddings` `transformer` `attention` `context window` `temperature` `top-p` `hallucination` `prompt` `system message` `few-shot` `chain-of-thought` `RAG` `vector store` `FAISS` `ChromaDB` `multimodal`
