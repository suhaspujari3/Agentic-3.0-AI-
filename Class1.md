# 🚀 Class 1: Python AI & Development Setup

**Course:** Agentic AI 3.0  
**Instructor:** Mayank Aggarwal  
**Key Topics:** Environment Setup, `uv` Package/Project Manager, Virtual Environments, Core Python, and API Integrations.

---

## 📌 Overview
This foundational session focuses on transitioning from traditional data science setups (like Jupyter Notebooks and Anaconda) to a robust, industry-standard software engineering environment tailored for building enterprise-grade AI applications. The primary goals are to establish environment reproducibility, proper isolation, and token-efficient coding practices.

---

## 🛠️ Development Environment Setup

To build production-ready AI agents, a strict development environment is required. 

*   **IDE:** **Visual Studio Code (VS Code)** is the industry standard and the required IDE for this bootcamp. 
    *   *Note:* Avoid Jupyter Notebooks for AI development. Using AI-assisted coding tools (like Claude Code or Cursor) inside notebooks results in a massive waste of API tokens.
*   **Terminal Mastery:** Real development happens in the terminal.
    *   **Mac/Linux:** Use the native Unix-based terminal.
    *   **Windows:** Standard `cmd` and `PowerShell` often fail with advanced development scripts. Windows users must install and use **Git Bash** or **Windows Terminal** to properly execute Linux-based commands, mimicking real-world cloud deployments.
*   **Python Version:** Python **3.10 or higher** is strictly required.

---

## ⚡ Package & Project Management with `uv`

Legacy tools like `pip`, `venv`, and `conda` are discouraged in favor of **`uv`**, a blazing-fast project and package manager built in Rust (10x-200x faster than traditional tools).

### 1. Initializing a Project
Instead of managing global packages, `uv` allows you to initialize contained projects.

```bash
# Initialize a new uv project
uv init my_first_project

# Navigate into your project directory
cd my_first_project

2. Understanding the Project Structure
When a project is initialized, uv creates:

pyproject.toml: The modern replacement for requirements.txt. It acts as a central configuration file storing project metadata, the required Python version, and a list of dependencies.

uv.lock: Generated when you sync or add dependencies. This lock file freezes the exact version of every library, guaranteeing that the project runs identically on any machine.


3. Managing Dependencies

# Add packages directly to the project (updates pyproject.toml and uv.lock automatically)
uv add pandas
uv add numpy
uv add requests


🌐 Virtual Environments (VENV)
Virtual environments act as isolated "rooms" for your projects, ensuring that dependencies for one project do not conflict with another.

Isolation: A virtual environment can host its own specific Python version (e.g., 3.12 vs 3.13) completely separate from your machine's global installation.

Automatic Handling: When you build a project using uv init, uv is smart enough to handle the virtual environment in the background based on the pyproject.toml, minimizing the need for manual activation/deactivation.

(Manual creation example, if working outside of a uv-initialized project)

# Create a virtual environment using a specific python version
uv venv --python 3.12

# Activate (Mac/Linux)
source .venv/bin/activate

# Activate (Windows - Git Bash)
source .venv/Scripts/activate

🐍 Python & API Fundamentals
Core Python Refresher
Dynamic Typing: Python does not require strict type declarations for variables (e.g., my_list = [1, 2, 3]).

F-Strings: The cleanest way to inject variables directly into strings.

city = "Tokyo"
print(f"{city} is a great place to visit!")

Functions & Docstrings: Always use docstrings in AI engineering to explain function behavior clearly.

import time

def get_current_time() -> str:
    """
    Fetches the current local time and formats it as a string.
    """
    return time.strftime("%Y-%m-%d %H:%M:%S")

print(get_current_time())

API Integration Basics
APIs allow your code to talk to the outside world (similar to calling a travel agent to get a flight price). Communicating with LLMs requires this exact same foundational knowledge.

Example: Fetching live currency rates via the Frankfurter API



import requests

# Base URL for the API
url = "[https://api.frankfurter.app/latest](https://api.frankfurter.app/latest)"

# Parameters for the API request
params = {
    "from": "USD",
    "to": "INR",
    "amount": 100
}

# Hitting the API with a 10-second timeout
response = requests.get(url, params=params, timeout=10)

if response.status_code == 200:
    data = response.json()
    print(f"Conversion Rate: {data['rates']['INR']} INR")
else:
    print("Failed to fetch data.")




