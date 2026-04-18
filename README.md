# LangChain RunnableBranch Routing
[![LangChain](https://img.shields.io/badge/Framework-LangChain-green)](https://www.langchain.com/)
[![Python](https://img.shields.io/badge/Python-3.9%2B-blue)](https://www.python.org/)
[![Routing](https://img.shields.io/badge/Concept-Conditional%20Logic-orange)](https://python.langchain.com/docs/expression_language/how_to/routing)

## 🏗️ Project Overview
This repository explores **`RunnableBranch`**, the definitive component for adding decision-making capabilities to the LangChain Expression Language (LCEL). `RunnableBranch` acts as the `if/elif/else` statement of your AI architecture. Instead of forcing all inputs through a single, generic prompt, this project demonstrates how to classify an input and route it to a specialized sub-chain, resulting in higher accuracy and optimized token usage.

---

## 🛠️ Key Technical Implementations

### 1. Intent Classification & Evaluation
* **Condition Functions:** Writing lightweight, deterministic Python functions (or small LLM calls) that evaluate the incoming dictionary state and return a boolean (`True`/`False`).
* **State Assessment:** Checking user input for specific keywords, sentiment, or formatting requirements before deciding how to process it.

### 2. Conditional Execution Architecture
* **The Branching Logic:** Structuring the `RunnableBranch` with tuples of `(condition, runnable)`. If the condition evaluates to true, that specific runnable (sub-chain) is executed, and the rest are ignored.
* **Specialized Experts:** Creating distinct `Prompt | Model | Parser` chains for different topics, allowing each branch to have its own highly optimized system instructions.

### 3. Fallback and Error Handling
* **The Default Path:** Implementing a mandatory "catch-all" default chain at the end of the branch. This ensures the pipeline never crashes if the user provides an input that doesn't match any of the predefined conditions.

---

## 💻 Tech Stack
* **Language:** Python 3.9+
* **Orchestration:** LangChain (`langchain-core`, `langchain-google-genai`)
* **Model:** Google Gemini Pro
* **Environment:** `python-dotenv`

---

## 🚀 Getting Started

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/your-username/langchain-runnable-branch-routing.git](https://github.com/your-username/langchain-runnable-branch-routing.git)

2. **Install Dependencies:**
   ```bash
   pip install -U langchain-core langchain-google-genai python-dotenv

3. **Setup API Key:**
   Create a .env file in the root directory:
   ```bash
   GOOGLE_API_KEY=your_gemini_key_here

4. **Run the Implementation:**
   ```bash
   python runnable_branch.py   
