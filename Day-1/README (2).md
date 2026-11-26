# Agentic AI – Day 1

This project is a Day 1 introduction to building an AI-powered assistant using LangChain, Groq, and Google Colab.

## 📌 Project Overview

The notebook demonstrates how to:

- Install and use `langchain_groq`
- Connect to the Groq API
- Configure a Groq-hosted LLM
- Store and retrieve API keys securely using Google Colab Secrets
- Define system instructions for an AI assistant
- Create a reusable function to send user questions to the LLM
- Build a simple bakery assistant with predefined rules
- Explore prompt-guard functionality using Groq

## 🛠️ Technologies Used

- Python
- Google Colab
- LangChain
- LangChain Groq
- Groq API
- `openai/gpt-oss-120b`
- `meta-llama/llama-prompt-guard-2-22m`

## 🚀 Getting Started

### 1. Open the Notebook

Open `agenticAI_Day1.ipynb` in Google Colab and run the cells sequentially.

### 2. Install Required Package

```python
!pip install langchain_groq
```

### 3. Configure the Groq API Key

Add your `GROQ_API_KEY` to Google Colab Secrets.

The notebook retrieves the key using:

```python
userdata.get("GROQ_API_KEY")
```

The API key should not be directly written inside the notebook.

### 4. Initialize the LLM

The notebook initializes the Groq model using:

```python
llm = ChatGroq(
    model="openai/gpt-oss-120b",
    temperature=0
)
```

## 🤖 AI Assistant Example

The notebook creates a simple assistant for **Sweet Crumbs Home Bakery**.

The assistant is given rules such as:

- The bakery bakes to order.
- Orders require 24 hours' notice.
- Cakes have eggless versions.
- The assistant should never promise delivery times.
- If information is unknown, it should say so.
- Responses should be polite and under 60 words.

Example system configuration:

```python
SYSTEM = """You are the assistant for Sweet Crumbs Home Bakery.
Facts: we bake to order; orders need 24 hours' notice; all cakes have eggless versions.
Rules: never promise delivery times; if you do not know, say so.
Format: reply politely in under 60 words."""
```

A reusable function is then created:

```python
def ask(question):
    return llm.invoke(
        [("system", SYSTEM), ("human", question)]
    ).content
```

## 🔐 Prompt Guard

The notebook also demonstrates the use of:

```text
meta-llama/llama-prompt-guard-2-22m
```

This is used to explore prompt-injection and unsafe-instruction detection.

## 📂 Project Structure

```text
.
├── agenticAI_Day1.ipynb
└── README.md
```

## ▶️ Running the Project

1. Open `agenticAI_Day1.ipynb` in Google Colab.
2. Add your `GROQ_API_KEY` to Colab Secrets.
3. Run the installation cell.
4. Run the LLM initialization cells.
5. Run the assistant configuration.
6. Use the `ask()` function to interact with the AI assistant.

## 📚 Learning Outcomes

After completing this notebook, you will understand the basics of:

- Connecting an application to an LLM
- Using LangChain with Groq
- Writing system prompts
- Controlling AI assistant behavior with rules
- Securely handling API keys in Colab
- Calling an LLM through a reusable Python function
- Basic prompt-guard concepts
