# Week 01 Questions: The AI Landscape — What AI Is and Is Not

---

## Q1 — AI → ML → Deep Learning → Generative AI → Agents

### A — Answer
* **Artificial Intelligence (AI):** The overarching discipline of creating computational systems capable of performing tasks that ordinarily require human intelligence, such as reasoning, pattern recognition, sensory perception, and problem-solving. Example: An autonomous robotic vacuum mapping a living space and navigating dynamically around obstacles.
* **Machine Learning (ML):** A specialized subset of AI where mathematical models identify statistical patterns, optimize objective functions, and infer decision boundaries directly from data without hand-coded procedural rules. Example: An email filtering engine trained on large labeled datasets to classify incoming mail as spam or legitimate.
* **Deep Learning (DL):** A technical subfield within ML based on multi-layered artificial neural network architectures capable of learning hierarchical feature representations directly from raw, high-dimensional input. Example: A facial recognition model extracting facial landmarks to unlock a mobile device.
* **Generative AI (GenAI):** A branch of deep learning models designed to sample from high-dimensional probability distributions to synthesize original content (text, source code, images, audio) that mirrors their training corpus. Example: A foundation language model generating a Python script based on a natural language prompt.
* **AI Agent:** A goal-oriented software system combining a foundation model reasoning core with memory, multi-step planning, and external tool execution (APIs, code interpreters, database connectors) to accomplish workflows iteratively. Example: A meeting assistant that inspects calendar availability, queries an airline API, books a flight, and sends confirmation details.

#### Concept Hierarchy
```text
┌─────────────────────────────────────────────────────────────┐
│ Artificial Intelligence (AI)                                │
│   ┌─────────────────────────────────────────────────────────┤
│   │ Machine Learning (ML)                                   │
│   │   ┌─────────────────────────────────────────────────────┤
│   │   │ Deep Learning (DL)                                  │
│   │   │   ┌─────────────────────────────────────────────────┤
│   │   │   │ Generative AI (GenAI)                           │
│   │   │   │ (e.g., LLMs, Diffusion Models)                  │
│   │   │   └─────────────────────────────────────────────────┘
└───────┴─────────────────────────────────────────────────────┘

[AI Agent: Systems & Workflow Architecture]
Agent = Core Foundation Model (Reasoning) + Planning + Memory + Tool Integration (APIs/Execution)

## Q6 — What Is an AI Agent?

### A — Answer
* **LLM (Large Language Model):** A foundation neural network trained to predict the next token given a context window.
* **LLM Application:** A software interface built around an LLM to manage user input, chat state, and prompt rendering (e.g., standard ChatGPT UI).
* **RAG System (Retrieval-Augmented Generation):** An architecture that retrieves external reference documents matching the user query from a database and injects them into the prompt to ground the LLM's answers in facts.
* **Tool-Using Assistant:** An LLM equipped with structured API calling capabilities (e.g., executing Python, invoking a calculator, or querying a weather API) when computation is required.
* **AI Agent:** An autonomous system where an LLM acts as the decision engine inside a multi-step loop: setting plans, invoking tools, inspecting results, adjusting actions, and maintaining state until a complex goal is achieved.

#### Agent Architecture Flow Diagram
```text
User Request ──► [Agent Core / Reasoning Engine] ◄── Memory (Short & Long Term)
                         │
                         ▼
                  [Plan & Decide]
                         │
                         ▼
                 [Emit Tool Call]
                         │
                         ▼
             [External Tool Execution] (Search, Python REPL, APIs)
                         │
                         ▼
                 [Receive Tool Output]
                         │
                         ▼
                 [Inspect & Verify] ──(Goal achieved?)──► YES ──► Final Response
                         │
                         └──(NO: Re-plan & loop)
