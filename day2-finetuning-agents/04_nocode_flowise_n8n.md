# Day 2 · Session 4 — No-Code Agents: FlowiseAI & n8n

> **Session format:** Live walkthrough — this is a guide for the presenter, not a notebook.  
> **Duration:** 75 minutes  
> **Goal:** Build two working AI workflows without writing a single line of code.

---

## Why No-Code Matters

Before writing a single line of code, AI/ML faculty need to understand what these workflows *do*.
No-code tools let you:

- **Prototype fast** — validate an idea in 15 minutes before investing in code
- **Teach concepts visually** — students see the architecture, not just the output  
- **Democratise AI building** — non-programmers on your team can contribute
- **Explore before engineering** — de-risk complex agent designs

---

## Tool 1 — FlowiseAI

**What it is:** Open-source, self-hostable drag-and-drop tool for building LLM applications.  
**Best for:** RAG pipelines, conversational chatbots, simple agents.  
**Installation:**
```bash
npm install -g flowise
npx flowise start
# Open: http://localhost:3000
```
Or use [FlowiseAI Cloud](https://flowiseai.com) for a free hosted version.

---

### Demo 1 — Build a RAG Chatbot in FlowiseAI (15 min)

**What we're building:** A college department Q&A bot that answers questions from uploaded PDF documents.

**Steps in FlowiseAI:**

#### Step 1: Create a new Chatflow
- Click **Add New** → **Chatflow**
- Name it: `College Department Bot`

#### Step 2: Add components (drag from sidebar)
Add these nodes and connect them in order:

```
[PDF File Loader] → [Recursive Text Splitter] → [OpenAI Embeddings] → [Chroma / FAISS]
                                                                              ↓
[ChatOpenAI] ← [Conversational Retrieval QA Chain] ← [Chroma / FAISS]
```

**Component settings:**

| Component | Setting | Value |
|-----------|---------|-------|
| PDF File Loader | Upload | `department_handbook.pdf` |
| Recursive Text Splitter | Chunk Size | `500` |
| Recursive Text Splitter | Chunk Overlap | `80` |
| OpenAI Embeddings | Model | `text-embedding-3-small` |
| ChatOpenAI | Model | `gpt-4o-mini` |
| ChatOpenAI | Temperature | `0` |
| Conversational QA Chain | System Message | *See below* |

**System Message:**
```
You are a helpful assistant for students at our CSE department.
Answer questions using ONLY the provided document context.
If you don't know, say "Please contact the department office."
Be concise and helpful.
```

#### Step 3: Add API key
- Click the lock icon on OpenAI components → enter your OpenAI API key

#### Step 4: Upload document
- Open PDF File Loader → Upload `department_handbook.pdf`
- Click **Upsert** to index the document

#### Step 5: Test
- Click the chat bubble (bottom right) → test with these questions:
  - "What is the M.Tech fee?"
  - "Who teaches NLP?"
  - "What is the attendance rule?"

#### Step 6: Deploy
- Toggle **Publish** → get a shareable link + embed code
- Share link with students as `http://your-server:3000/chatbot/{id}`

---

### Demo 2 — Simple Agent in FlowiseAI (10 min)

**What we're building:** An agent that can search college info AND do calculations.

```
[OpenAI Tool Agent]
       ↓
[Calculator Tool]  +  [Custom Tool: College Search]
```

**Steps:**
1. Add `OpenAI Tool Agent` node
2. Add `Calculator` tool — connect to agent's Tools input
3. Add `Custom Tool` — define it:
   - Name: `college_search`
   - Description: `Search for college fee, course, faculty information`
   - Schema: `{"query": "string"}`
   - URL: `http://localhost:8000/search` (or paste knowledge base text directly)

**Test:**
- "If I'm a GATE scholar, how much do I pay total for M.Tech over 2 years?"
- Watch the agent call Calculator automatically

---

## Tool 2 — n8n

**What it is:** Workflow automation platform with 400+ integrations and AI nodes.  
**Best for:** Multi-step workflows, integrating AI into existing tools (Gmail, Sheets, Slack, etc.).  
**Installation:**
```bash
npx n8n
# Open: http://localhost:5678
```
Or use [n8n Cloud](https://n8n.io) free trial.

> **Your screenshots:** See `assets/n8n_chatbot.png` (simple LLM chatbot) and `assets/n8n_agent.png` (agent with memory + tools)

---

### Demo 3 — Simple LLM Chatbot in n8n (10 min)

*This is what's shown in your Screenshot_2026-06-14_at_8_01_51_PM.png*

**The flow:**
```
[When chat message received] → [Message a model (GPT-4o)] → Response
```

**Steps:**
1. Click **New Workflow** → name it `chatbot connected to LLM`
2. Add node: **Chat Trigger** (When chat message received)
3. Add node: **OpenAI** → Message a model
   - Model: `gpt-4o-mini`
   - System message: `You are a helpful teaching assistant.`
4. Connect: Chat Trigger → OpenAI
5. Click **Test Workflow** → open the chat (bottom left)
6. Test: type "gas in Toronto today?" — model admits it doesn't have real-time data

**What the demo proves:** Without tools, the model can't answer real-time questions. This motivates adding tools.

---

### Demo 4 — AI Agent with Tools + Memory in n8n (20 min)

*This is what's shown in your Screenshot_2026-06-14_at_8_04_38_PM.png*

**The flow:**
```
[Chat Trigger] → [AI Agent] → [Token Meter] → [Precious Metals Import Skill]
                      ↓              
              [OpenAI Chat Model]  
              [Simple Memory]      
              [Calculator]         
              [Search in Tavily]   
```

**Steps:**

1. Create new workflow: `chatGPT-Simple Agent+skill`

2. Add **Chat Trigger** node

3. Add **AI Agent** node (the star of the show):
   - Connect Chat Trigger → AI Agent
   - System Message: `You are a helpful assistant with access to search and calculation tools. Always use tools to get current information.`

4. Add sub-nodes to AI Agent:
   - **Chat Model** input: Add `OpenAI Chat Model` (gpt-4o-mini)
   - **Memory** input: Add `Simple Memory` (keeps conversation context)
   - **Tool** input 1: Add `Calculator`
   - **Tool** input 2: Add `Tavily Search` (web search)
     - Sign up at [tavily.com](https://tavily.com) for a free API key
     - Tavily is purpose-built for AI agents — cleaner results than Google

5. Add **Token Meter** → connect to AI Agent output (track token usage)

6. Test with:
   - "What is the price of 28.3 liters of premium gas in Toronto today?"
   - Watch: Agent calls Tavily search → gets current price → calculates total

**Key teaching moment:** Show the difference between the simple chatbot (can't answer) and the agent (calls web search, gets real data, multiplies price × volume).

---

### The Key Difference: What Tools Add

```
Without tools (simple chatbot):
  "What is the gold price today?"
  → "I don't have access to real-time data..."

With tools (agent):
  "What is the gold price today?"  
  → [calls Tavily search: "gold price USD today"]
  → [gets: $2,340/oz]
  → "The current gold price is $2,340 per troy ounce (as of today)."
```

This is the core value of agentic AI: **the ability to act and retrieve, not just recall.**

---

## FlowiseAI vs n8n — When to Use Which

| Dimension | FlowiseAI | n8n |
|-----------|-----------|-----|
| **Primary use** | LLM apps, RAG, chatbots | Workflow automation with AI |
| **Integrations** | LangChain ecosystem | 400+ business tools |
| **Ideal user** | AI/ML developers | Business analysts + developers |
| **Setup** | Simpler | More configuration |
| **Best for** | Building AI products | Automating AI-enhanced workflows |
| **Community** | Growing fast | Large and mature |
| **Cost** | Free / self-host | Free (limited) / paid plans |

**Rule of thumb:**
- Building a chatbot or RAG product → **FlowiseAI**
- Automating a business workflow (email → AI → Sheets → Slack) → **n8n**
- Both work great for prototyping before writing code

---

## Lab Assignment

**File:** `lab/lab_d2s4_nocode.md`

### Task 1 — FlowiseAI RAG bot
Build the College Department Bot from Demo 1. Upload a PDF from your subject (textbook chapter, lab manual, your own notes). Test with 5 questions. Screenshot the flow.

### Task 2 — n8n simple chatbot  
Build the simple LLM chatbot from Demo 3. Test it. Then ask it a real-time question (stock price, today's news). Notice what it can't do.

### Task 3 — n8n agent
Build the agent from Demo 4. Add the Tavily search tool. Ask it a real-time question. Compare the answer to Task 2.

### Task 4 — Design your own workflow
Without building it, sketch a workflow diagram (boxes + arrows) for an AI workflow that would be genuinely useful in your college. It could be:
- Auto-grading workflow (PDF submission → LLM grader → Google Sheets)
- Student FAQ bot (WhatsApp message → AI → college knowledge base → reply)
- Research digest (RSS feeds → AI summary → email newsletter)

Share your design with the group.

### 🌟 Bonus — Export and share
Export your FlowiseAI chatbot as a JSON, commit it to the repo under `day2-finetuning-agents/flowise-flows/`. Others can import and run it.

---

## Resources

- [FlowiseAI Documentation](https://docs.flowiseai.com)
- [n8n Documentation](https://docs.n8n.io)  
- [Tavily AI Search API](https://tavily.com) — free tier for AI agents
- [FlowiseAI GitHub](https://github.com/FlowiseAI/Flowise)
- [n8n Community Workflows](https://n8n.io/workflows) — ready-to-import templates
