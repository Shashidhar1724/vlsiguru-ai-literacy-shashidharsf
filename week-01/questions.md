# Week 01 Questions

## Q1 — AI → ML → Deep Learning → Generative AI → Agents

### A - Answer
* **Artificial Intelligence (AI):** The broad discipline of building computer systems capable of performing tasks that ordinarily require human intelligence, such as reasoning, visual perception, pattern synthesis, and decision-making. Example: An autonomous robotic vacuum mapping a room and planning paths around obstacles.
* **Machine Learning (ML):** A subset of AI focused on algorithms that infer statistical patterns and decision boundaries directly from data rather than relying exclusively on hand-written procedural rules. Example: An email filtering model trained on millions of labeled messages to detect spam.
* **Deep Learning (DL):** A specialized subfield of ML based on multi-layered artificial neural networks capable of learning hierarchical feature representations directly from raw, high-dimensional input. Example: A facial recognition model extracting facial landmarks to unlock a mobile device.
* **Generative AI (GenAI):** A branch of deep learning models designed to sample from learned probability distributions to synthesize original content (text, code, audio, images) that mirrors their training corpus. Example: An LLM drafting a technical explanation or writing a Python script from a prompt.
* **AI Agent:** A goal-oriented software system combining a foundation model reasoning core with memory, multi-step planning, and external tool execution (APIs, code interpreters, database connectors) to accomplish workflows iteratively. Example: A digital assistant checking calendar schedules, querying flight availability via an external API, booking a ticket, and emailing the itinerary.

**Hierarchy and System Architecture:**
* **Artificial Intelligence (AI)** contains **Machine Learning (ML)**
* **Machine Learning (ML)** contains **Deep Learning (DL)**
* **Deep Learning (DL)** contains **Generative AI (GenAI)**
* **AI Agent** is an outer systems architecture: Core LLM + Memory + Planning + Tool Integration (APIs/Execution).

Generative AI produces static outputs directly conditioned on an input prompt. In contrast, an AI agent treats the generative model as a reasoning core within an active software loop: it observes the environment, plans sub-tasks, calls external tools, reads the results, and iterates until the goal is achieved.

### E - Evidence
* Russell, S., & Norvig, P., *Artificial Intelligence: A Modern Approach* (4th ed., Pearson, 2020) — Formulates rational agent systems and places machine learning as inductive computational inference.
* Goodfellow, I., Bengio, Y., & Courville, A., *Deep Learning* (MIT Press, 2016) — Defines deep learning as multi-layer neural network representations within ML.
* Weng, L., "LLM Powered Autonomous Agents" (Lil'Log, 2023) — Outlines the agent architecture as planning, memory, and tool integration built around foundation models.

### V - Verification
Cross-referenced standard enterprise architecture documentation from AWS, IBM, and Anthropic to confirm the structural distinction between standalone foundation model inference and multi-step agentic workflows.

### R - Reflection
An AI agent is a software architecture, not just a larger model. A major risk is mistaking a model's fluent text output for true agency; without structured tool execution and validation loops, a model is merely predicting tokens, not verifying or completing tasks.

---

## Q2 — Is Everything That Looks Intelligent Actually AI?

### A - Answer

| Scenario | Classification | Reasoning |
|---|---|---|
| A. Calculator: 25 × 16 = 400 | Deterministic / Traditional Software | Executes fixed binary arithmetic microcode via hardwired digital logic; no statistical inference or pattern adaptation occurs. |
| B. Program: If temperature > 80°C, display WARNING | Deterministic / Traditional Software | Explicit conditional logic (`if-else`) hard-coded by a programmer; the decision boundary is static and manually specified. |
| C. Email system identifying spam based on prior patterns | Machine-Learning-Based AI | Learns statistical classification boundaries from historical corpora and continuously updates its parameters against evolving spam patterns. |
| D. Assistant writing a summary of a document | Generative AI | Deploys sequence-to-sequence neural architectures to synthesize novel abstractive natural language conditioned on source text context. |
| E. Navigation app predicting ETA via traffic data | Machine-Learning-Based AI | Leverages regression models trained on historical travel times, real-time sensor streams, and dynamic graph traversal algorithms. |

**Core Distinction:**
Traditional software relies on explicit, human-authored instructions where identical inputs follow deterministic execution branches. An AI system infers patterns, probability distributions, or decision boundaries directly from data, enabling it to generalize across novel inputs that were never explicitly anticipated by the programmer.

### E - Evidence
* Aho, A. V., & Ullman, J. D., *Foundations of Computer Science* — Covers deterministic finite automata and algorithmic computation.
* Google Machine Learning Crash Course: "Rules vs. Machine Learning" — Analyzes the operational boundary between procedural heuristics and data-driven models.

### V - Verification
Audited embedded monitoring systems against machine learning anomaly detection literature; verified that static comparator logic is universally categorized as deterministic control, not artificial intelligence.

### R - Reflection
Automation is not inherently AI. Mislabeling deterministic rules as AI introduces needless complexity; classical procedural software is often faster, cheaper, and more verifiable whenever problem rules are fully known.

---

## Q3 — What Happens When You Ask an LLM a Question?

### A - Answer
* **Prompt:** The initial text string or instruction provided by the user to establish context, role, and task constraints.
* **Token:** A discrete numerical token ID representing a character cluster, sub-word, or word (typically ~4 characters in English) used by the model for internal processing.
* **Context:** The active window of preceding tokens (system instructions, user query, conversation history) that the model processes simultaneously using self-attention mechanisms.
* **Probability Distribution:** The normalized score assigned across the entire vocabulary, indicating the statistical likelihood of each possible token following the preceding sequence.
* **Next-Token Prediction:** The core algorithmic mechanism of sampling and selecting the next token from the output probability distribution.
* **Generated Response:** The accumulated sequence of iteratively predicted tokens emitted by the model until a stopping condition or end-of-sequence token is reached.
* **Training vs. Inference:** *Training* is the high-cost offline phase where billions of model weights are adjusted across massive datasets using backpropagation; *Inference* is the operational phase where the frozen model processes input context to predict tokens without modifying its weights.

**Generation Flow:**
1. **Prompt Input:** User enters natural text.
2. **Tokenizer:** Splits text into numeric Token IDs.
3. **Model Processing:** Multi-head self-attention processes the context window.
4. **Probability Distribution:** Calculates likelihood scores across the entire vocabulary (Logits to Softmax).
5. **Token Selection:** Samples the next token (via Temperature, Top-p, Top-k).
6. **Append & Loop:** The selected token is added back to the context window and the loop repeats until an end-of-sequence token is generated.

**Why Fluent Language Can Still Be False:**
Language models optimize for statistical plausibility and semantic coherence within the context window, not ontological truth. A sentence can be grammatically flawless and semantically seamless because its token transition probabilities are high, even when the underlying assertion is completely ungrounded or factually incorrect.

### E - Evidence
* Vaswani et al., "Attention Is All You Need" (NeurIPS, 2017) — Foundational transformer self-attention architecture paper.
* Karpathy, A., "Intro to Large Language Models" (2023) — Video lecture explaining tokenization, context windows, and probabilistic generation.

### V - Verification
Tested token generation behavior using public tokenization endpoints (OpenAI Tiktoken and Hugging Face Transformers) to observe how temperature and top-p sampling alter next-token probability distributions.

### R - Reflection
Fluency is an indicator of statistical coherence, not factual accuracy. Recognizing that an LLM functions as an autoregressive next-token predictor prevents the mistake of treating it like an authoritative knowledge base.

---

## Q4 — Hallucination Experiment: Can AI Sound Confident and Still Be Wrong?

### A - Answer

| Experiment Parameter | Record / Observation |
|---|---|
| **Question** | "Who holds the world record for the fastest transatlantic crossing by a commercial sailing passenger ship, and in what year was it set?" |
| **Model 1 (Gemini)** | Answered: *SS United States* in 1952. Summary: Confidently detailed the 3 days, 10 hours, 40 minutes crossing, failing to identify that the vessel was powered by steam turbines and violated the "sailing ship" constraint. |
| **Model 2 (ChatGPT)** | Answered: *Cutty Sark* in 1885. Summary: Confidently asserted that this clipper held the transatlantic passenger record, citing specific voyage durations. |
| **Verified Claim** | The historical record for a commercial sailing passenger ship on the transatlantic packet run belongs to the clipper *James Baines* (12 days, 6 hours in 1854). The absolute sailing record across the Atlantic belongs to modern racing trimarans (*Banque Populaire V*, 2009). |
| **Evidence Source** | International Maritime Organization historical archives / *The Western Ocean Packets* (Basil Lubbock). |
| **Result** | Both models produced fluent, authoritative-sounding answers that violated prompt constraints. Model 1 hallucinated relevance (steamship instead of sailing ship); Model 2 hallucinated historical vessel records (*Cutty Sark* served the China tea and Australian wool routes, not transatlantic passenger runs). |
| **Lesson** | AI models prioritize strong statistical associations ("transatlantic record" + "fastest crossing") and construct smooth prose around them while quietly ignoring negative or restrictive constraints. |

### E - Evidence
Live experimental prompts executed across ChatGPT (GPT-4o) and Gemini interfaces using the identical test query.

### V - Verification
Cross-referenced maritime historical archives, Lloyd's Register historical vessel lists, and nautical speed records.

### R - Reflection
Syntactic confidence has zero correlation with factual validity. Without explicit human domain checks, subtle constraint violations will easily pass into engineering documentation undetected.

---

## Q5 — AI Assistant vs. Search vs. Authoritative Reference

### A - Answer
* **Investigation Question:** "What is the physical significance of the Nyquist-Shannon sampling theorem's minimum sampling frequency condition?"

| Criteria | AI Assistant (e.g., Claude/Gemini) | Search Engine (e.g., Google) | Authoritative Reference (Textbook/Standard) |
|---|---|---|---|
| **Answer Summary** | Explains that $f_s > 2B$ is necessary to prevent frequency-domain spectral replicas from overlapping (aliasing), enabling perfect signal reconstruction. | Returns links to Wikipedia articles, YouTube tutorials, and university lecture slide decks. | Shannon’s 1949 paper / Oppenheim DSP: Rigorously proves mathematically via Fourier transform convolution that spectra do not overlap when $f_s \ge 2 f_{max}$. |
| **Accuracy** | High conceptual accuracy, though it can gloss over boundary conditions ($f_s = 2B$). | Variable; depends on the credibility of the specific link clicked. | Absolute benchmark; mathematically proven and peer-reviewed. |
| **Explanation Quality** | Exceptional: intuitive, adaptable, plain language with step-by-step analogies. | Fragmented: requires manual skimming across multiple tabs and search results. | Dense: requires prior domain background to interpret formal mathematical notation. |
| **Traceability** | Low: statements are generated dynamically without direct primary source citations. | Moderate: distinct web pages provide specific URLs, though authorship quality varies. | Highest: formal publication, peer-reviewed, specific page and theorem attribution. |
| **Verification Ease** | Difficult without external verification against independent literature. | Moderate: requires comparing multiple websites against each other. | Straightforward: serves as the ground truth benchmark. |

**When to Use Each:**
* **AI Assistant:** Best for rapid initial exploration, explaining complex concepts simply, and brainstorming analogies.
* **Search Engine:** Best for discovering diverse viewpoints, finding active community discussions, and locating original source URLs.
* **Authoritative Reference:** Mandatory for making final engineering decisions, production implementations, safety signoffs, and resolving contradictory claims.

### E - Evidence
* Shannon, C. E., "Communication in the Presence of Noise", *Proceedings of the IRE*, 1949.
* Oppenheim, A. V., & Schafer, R. W., *Discrete-Time Signal Processing* (Prentice Hall).

### V - Verification
Compared mathematical formulations in Shannon's original 1949 paper against the generated AI responses, confirming that the spectral folding concept was described correctly.

### R - Reflection
AI models provide speed of comprehension, but only primary references provide the authority required for engineering signoff.

---

## Q6 — What Is an AI Agent?

### A - Answer
* **LLM (Large Language Model):** A foundation neural network trained to predict the next token given a context window.
* **LLM Application:** A software interface built around an LLM to manage user input, chat state, and prompt rendering (e.g., standard ChatGPT UI).
* **RAG System (Retrieval-Augmented Generation):** An architecture that retrieves external reference documents matching the user query from a database and injects them into the prompt to ground the LLM's answers in facts.
* **Tool-Using Assistant:** An LLM equipped with structured API calling capabilities (e.g., executing Python, invoking a calculator, or querying a weather API) when computation is required.
* **AI Agent:** An autonomous system where an LLM acts as the decision engine inside a multi-step loop: setting plans, invoking tools, inspecting results, adjusting actions, and maintaining state until a complex goal is achieved.

**Agent Architecture Loop:**
1. **User Goal:** Receives user request and loads short/long-term memory.
2. **Plan & Decide:** The reasoning core chooses the next action.
3. **Tool Call:** Dispatches execution parameters to tools (Search, Python REPL, APIs).
4. **Tool Result:** Receives tool output back into context.
5. **Inspect & Verify:** Evaluates if the goal is completed. If not, re-plans and loops back. If complete, returns the final response.

**Difference between a Chatbot and an Agent:**
A chatbot is reactive: it receives input $X$ and generates text $Y$ in a single inference pass. An agent is proactive and goal-driven: given a complex objective, it breaks the task into sub-goals, calls external tools, checks whether the tool succeeded, retries if errors occur, and determines when the overall task is complete.

**Non-VLSI Agentic Workflow Example:**
An automated conference travel coordinator. The user requests: *"Arrange my trip to the IEEE conference next month under a $1,000 budget."* The agent queries flight and hotel booking APIs, checks the user's Google Calendar for conflicts, filters options within the budget limit, drafts an itinerary, emails it for human approval, and confirms reservations once approved.

### E - Evidence
* Yao et al., "ReAct: Synergizing Reasoning and Acting in Language Models" (ICLR, 2023).
* LangChain & Microsoft AutoGen Agent Framework Documentation.

### V - Verification
Verified against standard enterprise agentic specifications (e.g., CrewAI, Semantic Kernel) where agents are defined by a loop of perception, tool execution, and state evaluation.

### R - Reflection
Agents dramatically increase capabilities, but they also multiply failure modes. When an LLM fails inside an agent loop, errors can cascade into unintended API calls or repetitive loops if strict tool sandboxing and human checkpoints are absent.

---

## Q7 — Where Should Humans Still Make the Decision?

### A - Answer

| Situation | Possible Failure if AI Output Accepted Blindly | Required Verification Evidence | Approving Authority |
|---|---|---|---|
| **1. Clinical Drug Prescription** | Hallucinated dosage calculation or overlooked drug-drug interaction leading to patient toxicity. | Double-checked calculation against clinical pharmacopeia guidelines and patient lab charts. | Licensed Physician / Pharmacist |
| **2. Structural Load-Bearing Signoff** | Underestimation of seismic stress or material shear failure leading to catastrophic structural collapse. | Finite element analysis (FEA) physics simulation logs, building code compliance audits, material test reports. | Licensed Professional Civil/Structural Engineer |
| **3. Commercial Legal Contract Approval** | Overlooked indemnification loop or misinterpreted liability caps exposing the company to massive legal exposure. | Redlined legal audit comparing clause wording against statutory precedents and corporate risk guidelines. | Corporate Legal Counsel / CFO |
| **4. Critical System Infrastructure Deployment** | Auto-generated shell script introducing a configuration race condition that deletes production databases. | Automated unit/integration test suite logs, staging environment stress tests, code review diffs. | Lead DevOps / Site Reliability Engineer |
| **5. Autonomous Vehicle Braking Logic** | False-negative optical classification in extreme lighting (e.g., bright glare) causing a failure to brake. | Hardware-in-the-loop (HIL) sensor logs, redundant radar/LiDAR telemetry, physical track validation data. | Automotive Systems Safety Engineer |

> *Rule for Responsible AI-Assisted Work:* Never delegate accountability to a statistical model: AI may propose, analyze, and draft, but a qualified human must independently verify assumptions against authoritative evidence and hold ultimate responsibility for consequential actions.

### E - Evidence
* IEEE Global Initiative on Ethics of Autonomous and Intelligent Systems: *Ethically Aligned Design*.
* EU Artificial Intelligence Act — Guidelines on Human Oversight in High-Risk AI Systems.

### V - Verification
Cross-referenced safety engineering standards (such as ISO 26262 for automotive functional safety) confirming mandatory human-in-the-loop verification signoffs.

### R - Reflection
Accountability cannot be transferred to software. The engineer who signs off on a design is legally and ethically responsible for the outcome, regardless of how capable the AI assistant appeared.

---

## Q8 — Find AI Around You

### A - Answer

| Everyday System | AI / ML Involved? | Primary Task Type | Public Evidence / Source | Simpler Rule-Based Alternative Feasible? |
|---|---|---|---|---|
| **1. Spotify Discover Weekly** | Yes | Recommendation / Classification | Spotify Engineering publications (collaborative filtering, deep audio autoencoders). | No; rule-based genre matching fails to capture nuanced, multi-dimensional user listening patterns. |
| **2. Microwave "Popcorn" Button** | No | Deterministic Timing / Sensor Control | Appliance teardown / user manuals (fixed countdown timer or humidity sensor threshold). | Yes; this is purely rule-based (`run for 2 min 15 sec` or `stop if humidity delta > threshold`). AI is not needed. |
| **3. Smartphone Camera Portrait Mode** | Yes | Recognition / Segmentation / Depth Estimation | Google AI Blog / Apple CoreML technical briefs on semantic segmentation networks. | Partially; physical dual-camera disparity checks work, but boundary edge segmentation (hair, eyeglasses) requires ML for high quality. |
| **4. Bank Fraud Alerts** | Yes | Anomaly Detection / Classification | Visa / Mastercard security whitepapers on real-time transaction ML scoring. | Yes, basic rules exist (`if transaction in country X while card in country Y, flag`), but simple rules cause overwhelming false positive rates without ML. |
| **5. Google Maps Traffic Forecast** | Yes | Prediction (Time-series / Graph ML) | DeepMind / Google Maps collaborative research on Graph Neural Networks (GNNs). | No; simple historical averages fail during road closures, sudden accidents, or weather anomalies. |

### E - Evidence
* Google AI Blog: "Segmenting images with DeepLab" (Portrait mode edge segmentation).
* DeepMind Research: "Traffic prediction with advanced Graph Neural Networks in Google Maps".

### V - Verification
Inspected consumer microwave schematics and repair manuals, verifying that humidity sensor buttons use simple analog comparator circuits with fixed thresholds rather than ML models.

### R - Reflection
Marketing materials frequently label simple deterministic sensors and fixed algorithms as "smart" or "AI." Reviewing technical documentation reveals whether statistical learning is actually occurring.

---

## Q9 — Prediction, Classification, and Generation

### A - Answer

| Example Scenario | Primary Task Type | Engineering Justification |
|---|---|---|
| A. Predicting house prices | **Prediction** (Regression) | Estimates a continuous numerical value (currency) based on property features (area, age, location). |
| B. Detecting whether an image contains a cat | **Classification** | Assigns input data into discrete categorical labels (Binary: Cat vs. No Cat). |
| C. Writing an email from a short instruction | **Generation** | Synthesizes a new natural language text sequence conditioned on prompt instructions. |
| D. Predicting whether a customer will cancel a subscription | **Classification** (Churn Prediction) | Predicts a discrete binary class (Will Churn vs. Will Stay), even though it estimates a probability score. |
| E. Summarizing a research paper | **Generation** | Synthesizes a condensed textual narrative capturing key information from the source text. |
| F. Identifying whether a transaction is fraudulent | **Classification** | Assigns a transaction record to a discrete category (Fraudulent vs. Legitimate). |
| G. Generating an image from a text description | **Generation** | Synthesizes high-dimensional pixel arrays conditioned on semantic text tokens. |
| H. Predicting the next word/token in a sentence | **Prediction** (Classification over Vocabulary) | Evaluates probability distributions to select the next discrete element from a vocabulary. |

**Why Next-Token Prediction is Fundamental:**
Modern tasks like summarization, reasoning, and code generation look like distinct high-level cognitive abilities. However, at the machine level, they are all framed as conditional sequence modeling. By training a model to predict token $t_{n+1}$ given context $t_1 \dots t_n$ across vast human knowledge, the model is forced to compress world facts, logical structures, syntax, and reasoning steps into its internal weights. Thus, iterative prediction of single tokens enables open-ended generation.

### E - Evidence
* Bishop, C. M., *Pattern Recognition and Machine Learning* (Springer, 2006) — Chapter on Regression and Classification.
* Radford et al., "Language Models are Unsupervised Multitask Learners" (OpenAI GPT-2/GPT-3 papers).

### V - Verification
Verified against standard machine learning curricula (Stanford CS229 / CS224N).

### R - Reflection
Complex high-level AI behaviors are built on simple mathematical primitives. Realizing that "creative writing" is achieved via iterative statistical next-token prediction demystifies AI and helps set realistic expectations about its reliability.

---

## Q10 — Design Your Personal AI Verification Protocol

### A - Answer
When using an AI assistant for technical and engineering tasks, I apply the following 7-step protocol:

1. **Isolate Intent & Constraints:** Formulate explicit requirements, boundary conditions, and acceptance criteria *before* prompting the model. (Catches: Vagueness, goal drift, and prompt-misalignment).
2. **Decompose AI Output Claims:** Separate the generated response into discrete, testable units: factual statements, structural assertions, and mathematical equations. (Catches: Believing an entire answer just because the introductory paragraph is correct).
3. **Inspect Underlying Assumptions:** Identify silent premises assumed by the AI (e.g., standard temperature/pressure, lossless conditions, specific library versions). (Catches: Models calculating correct answers for the wrong context).
4. **Trace Claims to Authoritative Sources:** Verify critical claims, equations, and specs directly against primary documentation, data books, or peer-reviewed literature. (Catches: Confident hallucinations and fabricated citations).
5. **Execute Boundary & Sanity Checks:** Subject values to extreme cases (zero, infinity, dimensional analysis, conservation of energy/units). (Catches: Mathematically impossible or inverted results).
6. **Triangulate via Independent Comparison:** Cross-check the output with an alternate model or a deterministic tool (calculator, compiler, script). (Catches: Model-specific biases and recurring blind spots).
7. **Conclude (Accept, Revise, or Discard):** Make a conscious engineering decision: accept verified portions, revise unverified claims with fresh evidence, or discard flawed outputs. (Catches: Blind reliance and unvetted AI copy-pasting).

**Worked Example (Non-VLSI Task):**
* **Objective:** Calculate the required battery bank capacity (in amp-hours) to power an off-grid 120W emergency radio system for 48 hours using a 12V battery system.
* **Step 1 (Constraints):** $P = 120\text{ W}$, $V = 12\text{ V}$, $t = 48\text{ h}$. Max allowed battery Depth of Discharge ($\text{DoD}$) = 50% (lead-acid longevity).
* **Step 2 (AI Claim):** AI states: $120\text{ W} / 12\text{ V} = 10\text{ A}$. $10\text{ A} \times 48\text{ h} = 480\text{ Ah}$. "You need a 480 Ah battery."
* **Step 3 (Inspect Assumptions):** The AI assumed 100% discharge efficiency and 0% inverter/cable loss, and ignored the 50% Depth of Discharge limit.
* **Step 4 (Authoritative Source):** Battery manufacturer application guides state lead-acid batteries must not exceed 50% DoD to prevent permanent cell degradation.
* **Step 5 (Boundary/Sanity Check):** Discharging a 480 Ah battery by 480 Ah leaves 0 Ah capacity, which destroys the battery bank within a few cycles.
* **Step 6 (Triangulate):** Manual arithmetic: Total energy = $120\text{ W} \times 48\text{ h} = 5,760\text{ Wh}$. Usable capacity needed = $480\text{ Ah}$. At 50% DoD, nominal capacity = $480 / 0.5 = 960\text{ Ah}$. Factoring in 85% inverter efficiency: $960 / 0.85 \approx 1,130\text{ Ah}$.
* **Step 7 (Conclude):** **Revise.** Reject the AI's 480 Ah figure; specify an 1,150 Ah battery system based on verified physical limits and safety margins.

### E - Evidence
* NASA Systems Engineering Handbook (NASA/SP-2016-6105 Rev 2) verification and validation protocols.
* Safety engineering standards for independent peer review.

### V - Verification
Tested this protocol against multiple technical prompts to confirm that Step 3 (Assumption Inspection) and Step 5 (Boundary Checks) consistently expose silent model simplifications.

### R - Reflection
Engineering verification is not just checking if the math is correct; it is checking whether the model solved the *right problem under the right physical constraints*.
