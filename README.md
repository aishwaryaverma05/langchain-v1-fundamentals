# LangChain v1 Fundamentals

A hands-on learning notebook covering the core concepts of **LangChain v1**, including LLM integration, model interactions, tools, agents, structured outputs, middleware, token management, and human-in-the-loop workflows using Python.

## Overview

This repository contains practical experiments with LangChain v1 to understand how Large Language Models (LLMs) can be integrated into Python applications and extended with tools, structured responses, and agent workflows.

The notebook uses Groq-hosted models and Google Gemini to explore different LangChain features through code examples.

## Topics Covered

### 1. LLM Integration

- Initialize chat models using LangChain's `init_chat_model()`.
- Connect to Groq-hosted models and Google Gemini.
- Send prompts using `invoke()`.
- Understand basic model responses and access response content.

### 2. Model Interaction Methods

- **Invoke:** Send a request and receive a model response.
- **Stream:** Receive output in chunks as it is generated.
- **Batch:** Send multiple independent prompts and collect their responses.

These methods demonstrate different ways to interact with LLMs depending on the application requirements.

### 3. Tools and Tool Calling

- Create Python functions that can be exposed as tools using the `@tool` decorator.
- Bind tools to a chat model using `bind_tools()`.
- Explore how a model can identify when a tool is relevant to a user's request.
- Build a basic weather tool example.

The notebook also introduces agents, which can use tools as part of their workflow.

### 4. Building Agents

- Create agents using LangChain's `create_agent()`.
- Provide a model, tools, and a system prompt.
- Invoke an agent with user messages.
- Explore a basic weather assistant example.

### 5. Messages and Prompt Context

Learn about the main message types used in LangChain:

- `SystemMessage` — Defines the assistant's role, behavior, and instructions.
- `HumanMessage` — Represents the user's input.
- `AIMessage` — Represents the model's response.
- Tool messages — Represent tool execution results in a conversation.

The notebook also explores system instructions, message metadata, and providing additional context to an LLM.

### 6. Structured Output

Learn how to obtain structured data instead of relying only on free-form text responses.

The notebook covers:

- **Pydantic:** Define schemas with fields, types, and descriptions using `BaseModel` and `Field`.
- **TypedDict:** Define dictionary-based output structures with type information.
- **Nested structures:** Represent complex data containing lists of objects and optional fields.
- **Raw model output:** Explore structured-output responses with additional raw response information.
- **Contact information extraction:** Practice defining a schema for contact details.

Movie information is used as an example to demonstrate structured output.

### 7. Middleware and Conversation Management

Explore middleware as a way to control aspects of an agent's execution.

Topics include:

- `SummarizationMiddleware` for summarizing conversation history.
- Configuring summarization triggers and how much recent conversation to retain.
- Using `InMemorySaver` for in-memory checkpointing.
- Configuring a thread ID to maintain conversation state.
- Running repeated queries within a conversation thread.

### 8. Token Management

- Explore why long conversations and tool responses can increase context usage.
- Build an example that returns long hotel-search responses.
- Experiment with summarization middleware to manage conversation history.
- Inspect message counts and estimated token usage.

**Note:** The notebook's `count_tokens()` helper estimates token usage from text length; it is not an exact tokenizer-based count.

### 9. Human-in-the-Loop (HITL)

Explore a workflow where an agent's execution can be paused for human review before a sensitive action.

The notebook demonstrates:

- Creating mock email-reading and email-sending tools.
- Configuring `HumanInTheLoopMiddleware`.
- Setting up an in-memory checkpointer.
- Exploring approval, editing, and rejection decisions for a tool action.

This introduces the idea of keeping a human involved when an AI agent is about to perform an action that requires oversight.

## Tech Stack

- **Language:** Python
- **LLM Framework:** LangChain v1
- **Model Providers:** Groq and Google Gemini
- **Agent State and Checkpointing:** LangGraph
- **Structured Data:** Pydantic, TypedDict, and Python dataclasses
- **Environment Configuration:** `python-dotenv`
- **Environment:** Jupyter Notebook

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/langchain-v1-fundamentals.git
cd langchain-v1-fundamentals
```

Replace `YOUR_USERNAME` with your GitHub username.

### 2. Create and activate a virtual environment

```bash
python -m venv venv
```

On Windows:

```powershell
venv\Scripts\activate
```

### 3. Install dependencies

Install the packages required by the notebook and its model integrations. Exact package versions should be selected and tested against the notebook.

```bash
pip install langchain langchain-groq langchain-google-genai langgraph python-dotenv pydantic typing-extensions jupyter
```

### 4. Configure API keys

Create a local `.env` file in the project directory:

```env
GROQ_API_KEY=your_groq_api_key
GOOGLE_API_KEY=your_google_api_key
```

Replace the placeholders with your own API keys.

**Security:** Never commit your `.env` file or expose API keys in your notebook, screenshots, or GitHub repository.

### 5. Run the notebook

Open Jupyter Notebook:

```bash
jupyter notebook
```

Then open `langChainintro.ipynb` and run the cells in order. Some examples require valid API keys and access to the selected models.

## Repository Structure

```text
langchain-v1-fundamentals/
├── langChainintro.ipynb   # Hands-on LangChain examples
├── README.md              # Project overview and setup instructions
├── requirements.txt       # Python dependencies
├── .gitignore             # Files excluded from Git
└── .env.example           # API-key configuration template
```

## Learning Objectives

By working through this notebook, the goal is to understand how to:

- Connect Python applications to different LLM providers.
- Invoke, stream, and batch model requests.
- Define tools and build basic agents.
- Structure model responses using schemas.
- Manage conversation state and summarize long histories.
- Introduce human oversight into agent workflows.

## Scope

This repository is a learning and experimentation project focused on LangChain fundamentals. The weather, hotel-search, and email examples are demonstrations using mock functions; they are not integrations with live weather, hotel-booking, or email services.

## Future Improvements

- Organize examples into smaller, topic-specific notebooks.
- Add tested dependency versions and reproducible setup instructions.
- Add error handling and validation for model and tool responses.
- Build an end-to-end application using retrieval-augmented generation (RAG).
- Add automated tests and practical evaluation examples.
