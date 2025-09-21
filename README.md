# Sidekick-LangGraph-Agent

A LangGraph-powered AI sidekick that uses tools (browser, search, Python, files, notifications) with an evaluator loop to meet explicit success criteria via a Gradio chat interface.

## Features

- **Tool-using worker**
  - Playwright browser control
  - Google Serper web search (`search` tool)
  - Python REPL execution
  - File management in a sandbox directory
  - Push notifications via Pushover
  - Wikipedia queries

- **Evaluator for quality control**
  - Structured feedback
  - Clear decision: success met vs. needs user input

- **Gradio UI**
  - Chatbot panel for responses and feedback  
  - Inputs for your task and success criteria  
  - Reset button to start a fresh agent

## Architecture
[Gradio UI] --(message + success criteria)--> [LangGraph]
      |                                             |
      v                                             v
   display <----------- [Worker LLM] <----------- [ToolNode executes tool calls]
      ^                         
      |                         
      |-----------------------> [Evaluator LLM] --(feedback/decision)-->
                                                      |          |
                                                 continue      stop

## Tech Stack

- Python
- LangGraph
- Groq `llama-3.3-70b-versatile` (worker and evaluator)
- Playwright (Chromium)
- Gradio
- Google Serper, Wikipedia
- Pushover (optional notifications)
