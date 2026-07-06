# 🚀 Class 2: Python AI Fundamentals & Pydantic Setup

**Course:** Agentic AI 3.0[cite: 2]  
**Instructor:** Mayank Aggarwal[cite: 2]  
**Date:** June 28, 2026[cite: 2]  

---

## 📌 1. Class Logistics & Windows Development Setup

### Centralized Learning Resources
* **Bug Sleep (Craft) Link:** Acts as the central hub for all class notes, links, and updates to prevent resources from getting lost in chat[cite: 2].
* **Mayank GPT:** A custom-built GPT assistant tailored to the course curriculum[cite: 2]. It explains code line-by-line, uses beginner-friendly analogies, and provides context-specific production insights[cite: 2].

### Windows Terminal Configuration
* Real-world AI and software development heavily relies on Linux/Unix-based terminal commands[cite: 2].
* Standard Windows Command Prompt (CMD) and PowerShell often fail to execute `sh` scripts or native Linux commands[cite: 2].
* **Solution:** Windows users must install **Git Bash**[cite: 2]. This provides a Unix-like command-line environment and can be integrated directly as a terminal profile inside VS Code[cite: 2].

---

## 🐍 2. Python Fundamentals for AI

A solid grasp of Python is mandatory before jumping into frameworks like LangChain or LangGraph[cite: 2]. 

### Dynamic Typing 
* Python is dynamically typed, meaning you do not have to declare variable types explicitly, and types can be changed at runtime (e.g., `age` can be an integer `25` and later reassigned as a string `"twenty-five"`)[cite: 2].
* While flexible, this poses a major risk in production databases, as invalid data types can break the system[cite: 2].

### Dictionaries & JSON
* In Python, JSON structures are functionally treated identically to Dictionaries (key-value pairs)[cite: 2].
* Almost all modern APIs (including LLMs) communicate via JSON[cite: 2].
* **Best Practice:** When extracting values from a dictionary, use the `.get("key")` method[cite: 2]. If a key is missing (e.g., `"humidity"` in a weather JSON), `.get()` returns `None` instead of throwing an application-crashing error[cite: 2].

### Error Handling (`try-except-finally`)
* AI generation is fuzzy and external APIs can fail (e.g., network timeouts or division-by-zero errors)[cite: 2]. 
* Code must be wrapped in `try-except` blocks to prevent the entire agent from dying due to a single failure[cite: 2].
* The `finally` block executes regardless of success or failure and is ideal for cleanup actions, such as closing a database connection[cite: 2].

---

## 🏗️ 3. Object-Oriented Programming (OOP) & `@dataclass`

### The Blueprint Concept
* OOP allows developers to create a `class` (a blueprint) to instantiate multiple unique objects (e.g., creating multiple `BankAccount` objects with isolated balances and deposit/withdrawal methods)[cite: 2].

### The `@dataclass` Decorator
* Writing the `__init__` function repeatedly is considered tedious boilerplate code[cite: 2].
* The `dataclass` module automatically generates initialization methods based on type-hinted attributes[cite: 2].
* **Critical Rule for Mutable Data:** When defining a list inside a dataclass, use `field(default_factory=list)`[cite: 2]. Assigning an empty list directly `[]` will cause all instances of the class to secretly share the exact same list in memory, leading to severe data contamination[cite: 2].

---

## 🎁 4. Decorators

* A decorator modifies or extends the behavior of a function without altering its core source code[cite: 2].
* **Analogy:** It is like wrapping a gift. The original function is the gift, and the decorator is the wrapping paper that adds new properties[cite: 2].
* Under the hood, a decorator takes a function as an argument, wraps it inside an inner `wrapper` function, and returns the newly enhanced function[cite: 2].
* **AI Use Case:** Decorators are heavily used in AI frameworks (e.g., placing `@tool` above a Python function converts it into an executable tool for an AI agent)[cite: 2].

---

## 🌍 5. API Integrations & Fake AI Concept

* **APIs:** Applications talk to external services over the web (e.g., requesting live currency conversion rates from the Frankfurter API using the `requests` library)[cite: 2].
* **LLM APIs:** Hitting ChatGPT or Claude is fundamentally just making an API call[cite: 2]. The prompt is sent as a JSON payload containing the `role` ("user" or "assistant") and the `content` (the prompt text)[cite: 2].
* **Fake AI Simulation:** To demystify LLMs, the instructor demonstrated a "Fake AI" function that accepts a user prompt and returns a hardcoded JSON response, proving that AI interactions are standard software-to-software API exchanges[cite: 2].

---

## 🛡️ 6. Introduction to Pydantic

Pydantic solves the inherent dangers of Python's dynamic typing by enforcing strict data validation.

* **What it does:** By inheriting from Pydantic's `BaseModel`, you create rigid data models for your inputs and outputs, ensuring data integrity across your application[cite: 2].
* **Type Coercion:** If an attribute requires an integer, but receives a string containing a number (e.g., `"25"`), Pydantic safely converts it to an integer (`25`)[cite: 2].
* **Strict Validation:** If fundamentally incompatible data is passed (e.g., an array instead of a string), Pydantic immediately throws a `ValidationError`[cite: 2].
* Pydantic is an absolute prerequisite for building FastAPI servers and ensuring structured, predictable JSON outputs from LLMs[cite: 2].

# Class 2 — Actual file list and simple summaries

This folder has only the actual Class 2 files. The previous README listed files that do not exist in this folder.

## Files and short summaries

- [`0 Basics_Python.py`](./0%20Basics_Python.py) — Python basics: variables, types, strings, and control flow.
- [`1 Data Structures.py`](./1%20Data%20Structures.py) — lists, dictionaries, tuples, and loops.
- [`2 OOP.py`](./2%20OOP.py) — classes and objects.
- [`3 Error Handling.py`](./3%20Error%20Handling.py) — try/except examples.
- [`4 Decorators.py`](./4%20Decorators.py) — how decorators work.
- [`5 Calling real api.py`](./5%20Calling%20real%20api.py) — real API call with `requests`.
- [`6 Fake ai call.py`](./6%20Fake%20ai%20call.py) — fake AI-style function.
- [`7 Ai_call_free_and_paid.py`](./7%20Ai_call_free_and_paid.py) — AI provider examples.
- [`8 Pydantic with ai.py`](./8%20Pydantic%20with%20ai.py) — Pydantic validation.
- [`9 Api call with structure.py`](./9%20Api%20call%20with%20structure.py) — API call with Pydantic.


## How to open a file

Click any linked file name above in the README to open it in VS Code.

## How to run a file

Use `uv run` with quotes around names that have spaces:

```bash
uv run "0 Basics_Python.py"
uv run "8 Pydantic with ai.py"
uv run "9 Api call with structure.py"
```

## Setup

Install the required packages:

```bash
uv add requests pydantic python-dotenv
```

If you also want AI provider support:

```bash
uv add openai
```

Copy the example environment file:

```bash
copy .env.example .env
```

Then add your provider key to `.env` if needed.
