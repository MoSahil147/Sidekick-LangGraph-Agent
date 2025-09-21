# Sidekick-LangGraph-Agent

This project works by combining a worker–evaluator loop with tool integration through LangGraph. When you enter a request and define success criteria in the Gradio UI, the message is passed to the Worker LLM, which is capable of calling tools like Playwright for browsing, Serper for search, Python REPL for quick code execution, file management, or sending push notifications. If the worker triggers a tool, LangGraph executes it through the ToolNode and returns the results back to the worker. Once the worker produces an answer, the Evaluator LLM checks the response against the given success criteria. If the criteria are met, the process ends; if not, or if the worker needs clarification, the feedback is looped back, and the cycle continues. This design ensures that the assistant not only performs tasks with external tools but also self-monitors through structured feedback to improve accuracy and relevance until completion.

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

## Tech Stack

- Python
- LangGraph
- Groq `llama-3.3-70b-versatile` (worker and evaluator)
- Playwright (Chromium)
- Gradio
- Google Serper, Wikipedia
- Pushover (optional notifications)
