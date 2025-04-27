# AgenticTradingAssistant

> An intelligent, autonomous trading assistant powered by agentic AI and LLMs — combining search, reasoning, and report synthesis to emulate a multi-agent financial research team.

AgenticTradingAssistant orchestrates a group of autonomous agents to perform end-to-end financial research. The system decomposes a user query into discrete search objectives, retrieves and extracts high-quality information from the web using Tavily, filters and cleans noisy content, and finally synthesizes insights using OpenAI’s GPT-4o.

Each stage is handled by a specialized agent — a planner, multiple researcher/cleaner/summarizer agents, and a final synthesizer — coordinated by LangGraph's agentic control flow.

---

##  Agentic Architecture

This system is structured like a team of AI-powered financial researchers:

| Agent Role         | Responsibility                                                   |
|--------------------|------------------------------------------------------------------|
| 🧭 Planner Agent    | Decomposes the user query into 2–4 actionable search subtasks     |
| 🔍 Research Agents  | Perform Tavily search + extract content for each task            |
| 🧼 Cleaner Agent     | Removes marketing boilerplate, social media prompts, footers     |
| 🧠 Summarizer Agent | Condenses each task’s findings using GPT-4o                      |
| 🧾 Synthesizer Agent | Compiles structured final report with section-wise analysis      |

All agents communicate via LangGraph’s evolving state, enabling seamless multi-step research flows.

---

## ⚙️ Features

- ✅ Multi-agent financial analysis pipeline
- 🔍 Real-time web search (Tavily) for each subtask
- 🧹 Advanced text extraction + noise filtering
- 🧠 GPT-based summarization per task
- 📝 Structured final synthesis via agent collaboration
- 🗂 Per-task & per-run logs (JSON, Markdown)

---

## 🧱 Architecture Overview

```mermaid
graph TD
    A[User Query] --> B[Planner Agent]
    B --> C1[Task 1: Research → Clean → Summarize Agent]
    B --> C2[Task 2: Research → Clean → Summarize Agent]
    B --> C3[Task N: Research → Clean → Summarize Agent]
    C1 --> D[Synthesizer Agent]
    C2 --> D
    C3 --> D
    D --> E[Final Report]

