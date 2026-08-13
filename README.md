# Autonomous Research Agent (v1.0 MVP)

An autonomous, self-correcting AI research agent that breaks down complex queries, scours the web, evaluates its own knowledge gaps, and synthesizes cited, production-ready Markdown reports. 

Unlike standard chatbots that do a single retrieval pass, this agent utilizes a **LangGraph state machine** to reflect on its findings and execute targeted sub-queries until it has enough information to write a comprehensive report.

## 🚀 Features

*   **True Agentic Self-Correction:** Evaluates its own research notes and generates targeted follow-up queries to fill knowledge gaps (up to a safe depth of 5 iterations).
*   **Asynchronous Execution:** Non-blocking DuckDuckGo web search via thread executors (`asyncio.to_thread`) prevents event loop freezing.
*   **Source Integrity:** Deduplicates URLs across search iterations and explicitly cites sources in the final Markdown artifact.
*   **Fault Tolerance:** Implements exponential backoff for search rate limits and API network blips.
*   **State Persistence:** Utilizes LangGraph's `MemorySaver` to checkpoint state per-session (ready to be upgraded to PostgreSQL for production).
*   **Live SSE Dashboard:** A React/Vanilla JS frontend that streams the agent's internal "thought process" (Planning → Executing → Reflecting → Synthesizing) via Server-Sent Events.

## 🛠️ Tech Stack

*   **AI Engine:** Google Gemini (`gemini-2.5-flash`) — *100% Free Tier*
*   **Orchestration:** LangGraph (StateGraph, Checkpointing)
*   **Web Search:** DuckDuckGo Search (`duckduckgo-search`)
*   **Backend:** FastAPI, Uvicorn, Server-Sent Events (SSE)
*   **Frontend:** HTML5, DOMPurify, Marked.js (XSS-safe Markdown rendering)

## 📦 Setup & Installation

**1. Clone the repository and navigate to the project directory:**
```bash
git clone [https://github.com/YOUR_USERNAME/ai-agent-portfolio.git](https://github.com/YOUR_USERNAME/ai-agent-portfolio.git)
cd ai-agent-portfolio/project1_research_agent
