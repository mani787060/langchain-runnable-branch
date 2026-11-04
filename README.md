# LangChain RunnableBranch – Conditional Routing in LCEL

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![LangChain](https://img.shields.io/badge/Framework-LangChain-green)
![Google Gemini](https://img.shields.io/badge/LLM-Google%20Gemini-orange)
![Concept](https://img.shields.io/badge/Concept-Conditional%20Routing-purple)

## Overview

This repository demonstrates how to implement conditional execution and decision-making in **LangChain Expression Language (LCEL)** using `RunnableBranch`.

In traditional applications, conditional statements such as `if`, `elif`, and `else` determine which operation should execute based on specific conditions.

Similarly, `RunnableBranch` enables LangChain applications to dynamically select and execute different processing chains depending on the incoming input.

Instead of sending every request through the same prompt and processing pipeline, we can define multiple specialized branches and a default fallback chain.

This approach makes LLM workflows more modular, flexible, and easier to organize.

## Key Concepts Demonstrated

### 1. RunnableBranch

`RunnableBranch` is a LangChain component that provides conditional routing between different runnable components.

It accepts condition-runnable pairs and executes the first branch whose condition evaluates to `True`. If no condition matches, it executes the default branch.

Conceptually:

```python
RunnableBranch(
    (condition_1, chain_1),
    (condition_2, chain_2),
    default_chain
)
```

This makes it possible to build structured decision-making workflows without manually writing routing logic for every execution.

### 2. Conditional Routing

Conditional routing determines which processing chain should handle an input.

For example, an application could route:

- Technical questions to a technical explanation chain.
- General questions to a general response chain.
- Unmatched inputs to a default fallback chain.

The conditions can be based on deterministic Python logic or other classification results.

### 3. Specialized Processing Chains

Different branches can use different prompts and processing components.

A typical branch can follow this structure:

```text
Input
  |
  v
Condition Evaluation
  |
  +------> Specialized Chain 1
  |
  +------> Specialized Chain 2
  |
  +------> Default Chain
```

Each specialized chain can contain its own prompt template, language model, and output parser.

This allows different types of requests to receive appropriate instructions and processing.

### 4. Default Fallback Chain

A default chain handles inputs that do not satisfy any predefined branch condition.

It acts as the final alternative in the routing system and helps ensure that unmatched inputs still receive a response.

## Workflow Architecture

```text
             User Input
                  |
                  v
          Input Processing
                  |
                  v
          RunnableBranch
                  |
          Condition Checking
                  |
        +---------+---------+
        |         |         |
        v         v         v
     Branch 1  Branch 2  Default
        |         |         |
        v         v         v
     Chain 1   Chain 2   Fallback
        |         |         |
        +---------+---------+
                  |
                  v
             Final Output
```

## Why RunnableBranch?

Without conditional routing, an application may use the same instructions and processing logic for every request.

`RunnableBranch` provides a structured way to:

- Separate different types of requests.
- Execute specialized processing chains.
- Apply different prompt instructions to different inputs.
- Define a fallback for unmatched conditions.
- Build modular and maintainable LLM applications.

## Technologies Used

| Technology | Purpose |
|---|---|
| Python 3.9+ | Core programming language |
| LangChain Core | LCEL orchestration |
| RunnableBranch | Conditional routing |
| Google Gemini | Language model |
| Prompt Templates | Structuring model instructions |
| Output Parsers | Processing model responses |
| python-dotenv | Environment variable management |

## Project Structure

```text
langchain-runnable-branch/
│
├── runnable_branch.py
├── README.md
└── .env
```

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/mani787060/langchain-runnable-branch.git
cd langchain-runnable-branch
```

### 2. Create a Virtual Environment

```bash
python -m venv venv
```

Activate the environment:

**Windows:**
```bash
venv\Scripts\activate
```

**macOS/Linux:**
```bash
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -U langchain-core langchain-google-genai python-dotenv
```

### 4. Configure Your Gemini API Key

Create a `.env` file in the root directory:

```env
GOOGLE_API_KEY=your_gemini_api_key
```

Keep your API key private. Never upload your `.env` file to GitHub.

### 5. Run the Project

```bash
python runnable_branch.py
```

## Learning Outcomes

After exploring this project, you should understand:

- How conditional routing works in LangChain.
- How to use `RunnableBranch` within LCEL pipelines.
- How to define condition-runnable pairs.
- How to organize specialized processing chains.
- Why default fallback chains are important.
- How conditional execution helps structure more flexible LLM applications.

## Future Improvements

Some possible extensions include:

- Building an intent-based customer support chatbot.
- Integrating an LLM-based classification step before routing.
- Connecting conditional routing with RAG pipelines.
- Adding more specialized branches for complex applications.
- Combining `RunnableBranch` with `RunnableParallel` and `RunnableLambda`.

## Repository

GitHub: https://github.com/mani787060/langchain-runnable-branch

---

**Learning Focus:** LangChain LCEL, RunnableBranch, conditional execution, and modular LLM workflow design.
