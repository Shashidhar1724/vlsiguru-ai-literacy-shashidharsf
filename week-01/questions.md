# Week 01 Questions[cite: 1]

## Q1 — AI → ML → Deep Learning → Generative AI → Agents[cite: 1]

### A - Answer
* **Artificial Intelligence (AI):** The broad discipline of building computer systems capable of performing tasks that ordinarily require human intelligence, such as reasoning, visual perception, pattern synthesis, and decision-making[cite: 1]. Example: An autonomous robotic vacuum mapping a room and planning paths around obstacles[cite: 1].
* **Machine Learning (ML):** A subset of AI focused on algorithms that infer statistical patterns and decision boundaries directly from data rather than relying exclusively on hand-written procedural rules[cite: 1]. Example: An email filtering model trained on millions of labeled messages to detect spam[cite: 1].
* **Deep Learning (DL):** A specialized subfield of ML based on multi-layered artificial neural networks capable of learning hierarchical feature representations directly from raw, high-dimensional input[cite: 1]. Example: A facial recognition model extracting facial landmarks to unlock a mobile device[cite: 1].
* **Generative AI (GenAI):** A branch of deep learning models designed to sample from learned probability distributions to synthesize original content (text, code, audio, images) that mirrors their training corpus[cite: 1]. Example: An LLM drafting a technical explanation or writing a Python script from a prompt[cite: 1].
* **AI Agent:** A goal-oriented software system combining a foundation model reasoning core with memory, multi-step planning, and external tool execution (APIs, code interpreters, database connectors) to accomplish workflows iteratively[cite: 1]. Example: A digital assistant checking calendar schedules, querying flight availability via an external API, booking a ticket, and emailing the itinerary[cite: 1].

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
Agent = Core Foundation Model (Reasoning) + Planning + Memory + Tool Integration (APIs/Execution)```
[cite: 1]

Generative AI produces static outputs directly conditioned on an input prompt[cite: 1]. In contrast, an AI agent treats the generative model as a reasoning core within an active software loop: it observes the environment, plans sub-tasks, calls external tools, reads the results, and iterates until the goal is achieved[cite: 1].

### E - Evidence
* Russell, S., & Norvig, P., *Artificial Intelligence: A Modern Approach* (4th ed., Pearson, 2020) — Formulates rational agent systems and places machine learning as inductive computational inference[cite: 1].
* Goodfellow, I., Bengio, Y., & Courville, A., *Deep Learning* (MIT Press, 2016) — Defines deep learning as multi-layer neural network representations within ML[cite: 1].
* Weng, L., "LLM Powered Autonomous Agents" (Lil'Log, 2023) — Outlines the agent architecture as planning, memory, and tool integration built around foundation models[cite: 1].

### V - Verification
Cross-referenced standard enterprise architecture documentation from AWS, IBM, and Anthropic to confirm the structural distinction between standalone foundation model inference and multi-step agentic workflows[cite: 1].

### R - Reflection
An AI agent is a software architecture, not just a larger model[cite: 1]. A major risk is mistaking a model's fluent text output for true agency; without structured tool execution and validation loops, a model is merely predicting tokens, not verifying or completing tasks[cite: 1].

---

## Q2 — Is Everything That Looks Intelligent Actually AI?[cite: 1]

### A - Answer

| Scenario | Classification | Reasoning |
|---|---|---|
| A. Calculator: 25 × 16 = 400[cite: 1] | Deterministic / Traditional Software[cite: 1] | Executes fixed binary arithmetic microcode via hardwired digital logic; no statistical inference or pattern adaptation occurs[cite: 1]. |
| B. Program: If temperature > 80°C, display WARNING[cite: 1] | Deterministic / Traditional Software[cite: 1] | Explicit conditional logic (`if-else`) hard-coded by a programmer; the decision boundary is static and manually specified[cite: 1]. |
| C. Email system identifying spam based on prior patterns[cite: 1] | Machine-Learning-Based AI[cite: 1] | Learns statistical classification boundaries from historical corpora and continuously updates its parameters against evolving spam patterns[cite: 1]. |
| D. Assistant writing a summary of a document[cite: 1] | Generative AI[cite: 1] | Deploys sequence-to-sequence neural architectures to synthesize novel abstractive natural language conditioned on source text context[cite: 1]. |
| E. Navigation app predicting ETA via traffic data[cite: 1] | Machine-Learning-Based AI[cite: 1] | Leverages regression models trained on historical travel times, real-time sensor streams, and dynamic graph traversal algorithms[cite: 1]. |

[cite: 1]

**Core Distinction:**
Traditional software relies on explicit, human-authored instructions where identical inputs follow deterministic execution branches[cite: 1]. An AI system infers patterns, probability distributions, or decision boundaries directly from data, enabling it to generalize across novel inputs that were never explicitly anticipated by the programmer[cite: 1].

### E - Evidence
* Aho, A. V., & Ullman, J. D., *Foundations of Computer Science* — Covers deterministic finite automata and algorithmic computation[cite: 1].
* Google Machine Learning Crash Course: "Rules vs. Machine Learning" — Analyzes the operational boundary between procedural heuristics and data-driven models[cite: 1].

### V - Verification
Audited embedded monitoring systems against machine learning anomaly detection literature; verified that static comparator logic is universally categorized as deterministic control, not artificial intelligence[cite: 1].

### R - Reflection
Automation is not inherently AI[cite: 1]. Mislabeling deterministic rules as AI introduces needless complexity; classical procedural software is often faster, cheaper, and more verifiable whenever problem rules are fully known[cite: 1].

---

## Q3 — What Happens When You Ask an LLM a Question?[cite: 1]

### A - Answer
* **Prompt:** The initial text string or instruction provided by the user to establish context, role, and task constraints[cite: 1].
* **Token:** A discrete numerical token ID representing a character cluster, sub-word, or word (typically ~4 characters in English) used by the model for internal processing[cite: 1].
* **Context:** The active window of preceding tokens (system instructions, user query, conversation history) that the model processes simultaneously using self-attention mechanisms[cite: 1].
* **Probability Distribution:** The normalized score assigned across the entire vocabulary, indicating the statistical likelihood of each possible token following the preceding sequence[cite: 1].
* **Next-Token Prediction:** The core algorithmic mechanism of sampling and selecting the next token from the output probability distribution[cite: 1].
* **Generated Response:** The accumulated sequence of iteratively predicted tokens emitted by the model until a stopping condition or end-of-sequence token is reached[cite: 1].
* **Training vs. Inference:** *Training* is the high-cost offline phase where billions of model weights are adjusted across massive datasets using backpropagation; *Inference* is the operational phase where the frozen model processes input context to predict tokens without modifying its weights[cite: 1].

```text
[Prompt Input]
      │
      ▼
[Tokenizer: Converts Raw Text into Token IDs]
      │
      ▼
[Model Processing: Multi-Head Self-Attention over Context Window]
      │
      ▼
[Probability Distribution Calculated Across Vocabulary (Logits → Softmax)]
      │
      ▼
[Token Selection (Sampling: Temperature, Top-p, Top-k)]
      │
      ▼
[Append Selected Token to Context Window] ──(Iterate until End-of-Sequence)──► [Final Response]
```[cite: 1]

**Why Fluent Language Can Still Be False:**
Language models optimize for statistical plausibility and semantic coherence within the context window, not ontological truth[cite: 1]. A sentence can be grammatically flawless and semantically seamless because its token transition probabilities are high, even when the underlying assertion is completely ungrounded or factually incorrect[cite: 1].

### E - Evidence
* Vaswani et al., "Attention Is All You Need" (NeurIPS, 2017) — Foundational transformer self-attention architecture paper[cite: 1].
* Karpathy, A., "Intro to Large Language Models" (2023) — Video lecture explaining tokenization, context windows, and probabilistic generation[cite: 1].

### V - Verification
Tested token generation behavior using public tokenization endpoints (OpenAI Tiktoken and Hugging Face Transformers) to observe how temperature and top-p sampling alter next-token probability distributions[cite: 1].

### R - Reflection
Fluency is an indicator of statistical coherence, not factual accuracy[cite: 1]. Recognizing that an LLM functions as an autoregressive next-token predictor prevents the mistake of treating it like an authoritative knowledge base[cite: 1].

---

## Q4 — Hallucination Experiment: Can AI Sound Confident and Still Be Wrong?[cite: 1]

### A - Answer

| Experiment Parameter | Record / Observation |
|---|---|
| **Question** | "Who holds the world record for the fastest transatlantic crossing by a commercial sailing passenger ship, and in what year was it set?"[cite: 1] |
| **Model 1 (Gemini)** | Answered: *SS United States* in 1952[cite: 1]. Summary: Confidently detailed the 3 days, 10 hours, 40 minutes crossing, failing to identify that the vessel was powered by steam turbines and violated the "sailing ship" constraint[cite: 1]. |
| **Model 2 (ChatGPT)** | Answered: *Cutty Sark* in 1885[cite: 1]. Summary: Confidently asserted that this clipper held the transatlantic passenger record, citing specific voyage durations[cite: 1]. |
| **Verified Claim** | The historical record for a commercial sailing passenger ship on the transatlantic packet run belongs to the clipper *James Baines* (12 days, 6 hours in 1854)[cite: 1]. The absolute sailing record across the Atlantic belongs to modern racing trimarans (*Banque Populaire V*, 2009)[cite: 1]. |
| **Evidence Source** | International Maritime Organization historical archives / *The Western Ocean Packets* (Basil Lubbock)[cite: 1]. |
| **Result** | Both models produced fluent, authoritative-sounding answers that violated prompt constraints[cite: 1]. Model 1 hallucinated relevance (steamship instead of sailing ship); Model 2 hallucinated historical vessel records (*Cutty Sark* served the China tea and Australian wool routes, not transatlantic passenger runs)[cite: 1]. |
| **Lesson** | AI models prioritize strong statistical associations ("transatlantic record" + "fastest crossing") and construct smooth prose around them while quietly ignoring negative or restrictive constraints[cite: 1]. |

[cite: 1]

### E - Evidence
Live experimental prompts executed across ChatGPT (GPT-4o) and Gemini interfaces using the identical test query[cite: 1].

### V - Verification
Cross-referenced maritime historical archives, Lloyd's Register historical vessel lists, and nautical speed records[cite: 1].

### R - Reflection
Syntactic confidence has zero correlation with factual validity[cite: 1]. Without explicit human domain checks, subtle constraint violations will easily pass into engineering documentation undetected[cite: 1].

---

## Q5 — AI Assistant vs. Search vs. Authoritative Reference[cite: 1]

### A - Answer
* **Investigation Question:** "What is the physical significance of the Nyquist-Shannon sampling theorem's minimum sampling frequency condition?"[cite: 1]

| Criteria | AI Assistant (e.g., Claude/Gemini) | Search Engine (e.g., Google) | Authoritative Reference (Textbook/Standard) |
|---|---|---|---|
| **Answer Summary** | Explains that $f_s > 2B$ is necessary to prevent frequency-domain spectral replicas from overlapping (aliasing), enabling perfect signal reconstruction[cite: 1]. | Returns links to Wikipedia articles, YouTube tutorials, and university lecture slide decks[cite: 1]. | Shannon’s 1949 paper / Oppenheim DSP: Rigorously proves mathematically via Fourier transform convolution that spectra do not overlap when $f_s \ge 2 f_{max}$[cite: 1]. |
| **Accuracy** | High conceptual accuracy, though it can gloss over boundary conditions ($f_s = 2B$)[cite: 1]. | Variable; depends on the credibility of the specific link clicked[cite: 1]. | Absolute benchmark; mathematically proven and peer-reviewed[cite: 1]. |
| **Explanation Quality** | Exceptional: intuitive, adaptable, plain language with step-by-step analogies[cite: 1]. | Fragmented: requires manual skimming across multiple tabs and search results[cite: 1]. | Dense: requires prior domain background to interpret formal mathematical notation[cite: 1]. |
| **Traceability** | Low: statements are generated dynamically without direct primary source citations[cite: 1]. | Moderate: distinct web pages provide specific URLs, though authorship quality varies[cite: 1]. | Highest: formal publication, peer-reviewed, specific page and theorem attribution[cite: 1]. |
| **Verification Ease** | Difficult without external verification against independent literature[cite: 1]. | Moderate: requires comparing multiple websites against each other[cite: 1]. | Straightforward: serves as the ground truth benchmark[cite: 1]. |

[cite: 1]

**When to Use Each:**
* **AI Assistant:** Best for rapid initial exploration, explaining complex concepts simply, and brainstorming analogies[cite: 1].
* **Search Engine:** Best for discovering diverse viewpoints, finding active community discussions, and locating original source URLs[cite: 1].
* **Authoritative Reference:** Mandatory for making final engineering decisions, production implementations, safety signoffs, and resolving contradictory claims[cite: 1].

### E - Evidence
* Shannon, C. E., "Communication in the Presence of Noise", *Proceedings of the IRE*, 1949[cite: 1].
* Oppenheim, A. V., & Schafer, R. W., *Discrete-Time Signal Processing* (Prentice Hall)[cite: 1].

### V - Verification
Compared mathematical formulations in Shannon's original 1949 paper against the generated AI responses, confirming that the spectral folding concept was described correctly[cite: 1].

### R - Reflection
AI models provide speed of comprehension, but only primary references provide the authority required for engineering signoff[cite: 1].

---

## Q6 — What Is an AI Agent?[cite: 1]

### A - Answer
* **LLM (Large Language Model):** A foundation neural network trained to predict the next token given a context window[cite: 1].
* **LLM Application:** A software interface built around an LLM to manage user input, chat state, and prompt rendering (e.g., standard ChatGPT UI)[cite: 1].
* **RAG System (Retrieval-Augmented Generation):** An architecture that retrieves external reference documents matching the user query from a database and injects them into the prompt to ground the LLM's answers in facts[cite: 1].
* **Tool-Using Assistant:** An LLM equipped with structured API calling capabilities (e.g., executing Python, invoking a calculator, or querying a weather API) when computation is required[cite: 1].
* **AI Agent:** An autonomous system where an LLM acts as the decision engine inside a multi-step loop: setting plans, invoking tools, inspecting results, adjusting actions, and maintaining state until a complex goal is achieved[cite: 1].

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
```[cite: 1]

**Difference between a Chatbot and an Agent:**
A chatbot is reactive: it receives input $X$ and generates text $Y$ in a single inference pass[cite: 1]. An agent is proactive and goal-driven: given a complex objective, it breaks the task into sub-goals, calls external tools, checks whether the tool succeeded, retries if errors occur, and determines when the overall task is complete[cite: 1].

**Non-VLSI Agentic Workflow Example:**
An automated conference travel coordinator[cite: 1]. The user requests: *"Arrange my trip to the IEEE conference next month under a $1,000 budget."*[cite: 1] The agent queries flight and hotel booking APIs, checks the user's Google Calendar for conflicts, filters options within the budget limit, drafts an itinerary, emails it for human approval, and confirms reservations once approved[cite: 1].

### E - Evidence
* Yao et al., "ReAct: Synergizing Reasoning and Acting in Language Models" (ICLR, 2023)[cite: 1].
* LangChain & Microsoft AutoGen Agent Framework Documentation[cite: 1].

### V - Verification
Verified against standard enterprise agentic specifications (e.g., CrewAI, Semantic Kernel) where agents are defined by a loop of perception, tool execution, and state evaluation[cite: 1].

### R - Reflection
Agents dramatically increase capabilities, but they also multiply failure modes[cite: 1]. When an LLM fails inside an agent loop, errors can cascade into unintended API calls or repetitive loops if strict tool sandboxing and human checkpoints are absent[cite: 1].

---

## Q7 — Where Should Humans Still Make the Decision?[cite: 1]

### A - Answer

| Situation | Possible Failure if AI Output Accepted Blindly[cite: 1] | Required Verification Evidence[cite: 1] | Approving Authority[cite: 1] |
|---|---|---|---|
| **1. Clinical Drug Prescription**[cite: 1] | Hallucinated dosage calculation or overlooked drug-drug interaction leading to patient toxicity[cite: 1]. | Double-checked calculation against clinical pharmacopeia guidelines and patient lab charts[cite: 1]. | Licensed Physician / Pharmacist[cite: 1] |
| **2. Structural Load-Bearing Signoff**[cite: 1] | Underestimation of seismic stress or material shear failure leading to catastrophic structural collapse[cite: 1]. | Finite element analysis (FEA) physics simulation logs, building code compliance audits, material test reports[cite: 1]. | Licensed Professional Civil/Structural Engineer[cite: 1] |
| **3. Commercial Legal Contract Approval**[cite: 1] | Overlooked indemnification loop or misinterpreted liability caps exposing the company to massive legal exposure[cite: 1]. | Redlined legal audit comparing clause wording against statutory precedents and corporate risk guidelines[cite: 1]. | Corporate Legal Counsel / CFO[cite: 1] |
| **4. Critical System Infrastructure Deployment**[cite: 1] | Auto-generated shell script introducing a configuration race condition that deletes production databases[cite: 1]. | Automated unit/integration test suite logs, staging environment stress tests, code review diffs[cite: 1]. | Lead DevOps / Site Reliability Engineer[cite: 1] |
| **5. Autonomous Vehicle Braking Logic**[cite: 1] | False-negative optical classification in extreme lighting (e.g., bright glare) causing a failure to brake[cite: 1]. | Hardware-in-the-loop (HIL) sensor logs, redundant radar/LiDAR telemetry, physical track validation data[cite: 1]. | Automotive Systems Safety Engineer[cite: 1] |

[cite: 1]

> *Rule for Responsible AI-Assisted Work:* Never delegate accountability to a statistical model: AI may propose, analyze, and draft, but a qualified human must independently verify assumptions against authoritative evidence and hold ultimate responsibility for consequential actions[cite: 1].

### E - Evidence
* IEEE Global Initiative on Ethics of Autonomous and Intelligent Systems: *Ethically Aligned Design*[cite: 1].
* EU Artificial Intelligence Act — Guidelines on Human Oversight in High-Risk AI Systems[cite: 1].

### V - Verification
Cross-referenced safety engineering standards (such as ISO 26262 for automotive functional safety) confirming mandatory human-in-the-loop verification signoffs[cite: 1].

### R - Reflection
Accountability cannot be transferred to software[cite: 1]. The engineer who signs off on a design is legally and ethically responsible for the outcome, regardless of how capable the AI assistant appeared[cite: 1].

---

## Q8 — Find AI Around You[cite: 1]

### A - Answer

| Everyday System | AI / ML Involved?[cite: 1] | Primary Task Type[cite: 1] | Public Evidence / Source[cite: 1] | Simpler Rule-Based Alternative Feasible?[cite: 1] |
|---|---|---|---|---|
| **1. Spotify Discover Weekly**[cite: 1] | Yes[cite: 1] | Recommendation / Classification[cite: 1] | Spotify Engineering publications (collaborative filtering, deep audio autoencoders)[cite: 1]. | No; rule-based genre matching fails to capture nuanced, multi-dimensional user listening patterns[cite: 1]. |
| **2. Microwave "Popcorn" Button**[cite: 1] | No[cite: 1] | Deterministic Timing / Sensor Control[cite: 1] | Appliance teardown / user manuals (fixed countdown timer or humidity sensor threshold)[cite: 1]. | Yes; this is purely rule-based (`run for 2 min 15 sec` or `stop if humidity delta > threshold`). AI is not needed[cite: 1]. |
| **3. Smartphone Camera Portrait Mode**[cite: 1] | Yes[cite: 1] | Recognition / Segmentation / Depth Estimation[cite: 1] | Google AI Blog / Apple CoreML technical briefs on semantic segmentation networks[cite: 1]. | Partially; physical dual-camera disparity checks work, but boundary edge segmentation (hair, eyeglasses) requires ML for high quality[cite: 1]. |
| **4. Bank Fraud Alerts**[cite: 1] | Yes[cite: 1] | Anomaly Detection / Classification[cite: 1] | Visa / Mastercard security whitepapers on real-time transaction ML scoring[cite: 1]. | Yes, basic rules exist (`if transaction in country X while card in country Y, flag`), but simple rules cause overwhelming false positive rates without ML[cite: 1]. |
| **5. Google Maps Traffic Forecast**[cite: 1] | Yes[cite: 1] | Prediction (Time-series / Graph ML)[cite: 1] | DeepMind / Google Maps collaborative research on Graph Neural Networks (GNNs)[cite: 1]. | No; simple historical averages fail during road closures, sudden accidents, or weather anomalies[cite: 1]. |

[cite: 1]

### E - Evidence
* Google AI Blog: "Segmenting images with DeepLab" (Portrait mode edge segmentation)[cite: 1].
* DeepMind Research: "Traffic prediction with advanced Graph Neural Networks in Google Maps"[cite: 1].

### V - Verification
Inspected consumer microwave schematics and repair manuals, verifying that humidity sensor buttons use simple analog comparator circuits with fixed thresholds rather than ML models[cite: 1].

### R - Reflection
Marketing materials frequently label simple deterministic sensors and fixed algorithms as "smart" or "AI"[cite: 1]. Reviewing technical documentation reveals whether statistical learning is actually occurring[cite: 1].

---

## Q9 — Prediction, Classification, and Generation[cite: 1]

### A - Answer

| Example Scenario | Primary Task Type[cite: 1] | Engineering Justification[cite: 1] |
|---|---|---|
| A. Predicting house prices[cite: 1] | **Prediction** (Regression)[cite: 1] | Estimates a continuous numerical value (currency) based on property features (area, age, location)[cite: 1]. |
| B. Detecting whether an image contains a cat[cite: 1] | **Classification**[cite: 1] | Assigns input data into discrete categorical labels (Binary: Cat vs. No Cat)[cite: 1]. |
| C. Writing an email from a short instruction[cite: 1] | **Generation**[cite: 1] | Synthesizes a new natural language text sequence conditioned on prompt instructions[cite: 1]. |
| D. Predicting whether a customer will cancel a subscription[cite: 1] | **Classification** (Churn Prediction)[cite: 1] | Predicts a discrete binary class (Will Churn vs. Will Stay), even though it estimates a probability score[cite: 1]. |
| E. Summarizing a research paper[cite: 1] | **Generation**[cite: 1] | Synthesizes a condensed textual narrative capturing key information from the source text[cite: 1]. |
| F. Identifying whether a transaction is fraudulent[cite: 1] | **Classification**[cite: 1] | Assigns a transaction record to a discrete category (Fraudulent vs. Legitimate)[cite: 1]. |
| G. Generating an image from a text description[cite: 1] | **Generation**[cite: 1] | Synthesizes high-dimensional pixel arrays conditioned on semantic text tokens[cite: 1]. |
| H. Predicting the next word/token in a sentence[cite: 1] | **Prediction** (Classification over Vocabulary)[cite: 1] | Evaluates probability distributions to select the next discrete element from a vocabulary[cite: 1]. |

[cite: 1]

**Why Next-Token Prediction is Fundamental:**
Modern tasks like summarization, reasoning, and code generation look like distinct high-level cognitive abilities[cite: 1]. However, at the machine level, they are all framed as conditional sequence modeling[cite: 1]. By training a model to predict token $t_{n+1}$ given context $t_1 \dots t_n$ across vast human knowledge, the model is forced to compress world facts, logical structures, syntax, and reasoning steps into its internal weights[cite: 1]. Thus, iterative prediction of single tokens enables open-ended generation[cite: 1].

### E - Evidence
* Bishop, C. M., *Pattern Recognition and Machine Learning* (Springer, 2006) — Chapter on Regression and Classification[cite: 1].
* Radford et al., "Language Models are Unsupervised Multitask Learners" (OpenAI GPT-2/GPT-3 papers)[cite: 1].

### V - Verification
Verified against standard machine learning curricula (Stanford CS229 / CS224N)[cite: 1].

### R - Reflection
Complex high-level AI behaviors are built on simple mathematical primitives[cite: 1]. Realizing that "creative writing" is achieved via iterative statistical next-token prediction demystifies AI and helps set realistic expectations about its reliability[cite: 1].

---

## Q10 — Design Your Personal AI Verification Protocol[cite: 1]

### A - Answer
When using an AI assistant for technical and engineering tasks, I apply the following 7-step protocol[cite: 1]:

```text
[1. Isolate Intent & Constraints]
                │
                ▼
[2. Decompose AI Output Claims]
                │
                ▼
[3. Inspect Underlying Assumptions]
                │
                ▼
[4. Trace Claims to Authoritative Sources]
                │
                ▼
[5. Execute Boundary & Sanity Checks]
                │
                ▼
[6. Triangulate via Independent Comparison]
                │
                ▼
[7. Conclude: Accept, Revise, or Discard]
```[cite: 1]

1. **Isolate Intent & Constraints:** Formulate explicit requirements, boundary conditions, and acceptance criteria *before* prompting the model[cite: 1]. (Catches: Vagueness, goal drift, and prompt-misalignment)[cite: 1].
2. **Decompose AI Output Claims:** Separate the generated response into discrete, testable units: factual statements, structural assertions, and mathematical equations. (Catches: Believing an entire answer just because the introductory paragraph is correct).
3. **Inspect Underlying Assumptions:** Identify silent premises assumed by the AI (e.g., standard temperature/pressure, lossless conditions, specific library versions)[cite: 1]. (Catches: Models calculating correct answers for the wrong context)[cite: 1].
4. **Trace Claims to Authoritative Sources:** Verify critical claims, equations, and specs directly against primary documentation, data books, or peer-reviewed literature[cite: 1]. (Catches: Confident hallucinations and fabricated citations)[cite: 1].
5. **Execute Boundary & Sanity Checks:** Subject values to extreme cases (zero, infinity, dimensional analysis, conservation of energy/units)[cite: 1]. (Catches: Mathematically impossible or inverted results)[cite: 1].
6. **Triangulate via Independent Comparison:** Cross-check the output with an alternate model or a deterministic tool (calculator, compiler, script)[cite: 1]. (Catches: Model-specific biases and recurring blind spots)[cite: 1].
7. **Conclude (Accept, Revise, or Discard):** Make a conscious engineering decision: accept verified portions, revise unverified claims with fresh evidence, or discard flawed outputs[cite: 1]. (Catches: Blind reliance and unvetted AI copy-pasting)[cite: 1].

**Worked Example (Non-VLSI Task):**
* **Objective:** Calculate the required battery bank capacity (in amp-hours) to power an off-grid 120W emergency radio system for 48 hours using a 12V battery system[cite: 1].
* **Step 1 (Constraints):** $P = 120\text{ W}$, $V = 12\text{ V}$, $t = 48\text{ h}$. Max allowed battery Depth of Discharge ($\text{DoD}$) = 50% (lead-acid longevity)[cite: 1].
* **Step 2 (AI Claim):** AI states: $120\text{ W} / 12\text{ V} = 10\text{ A}$. $10\text{ A} \times 48\text{ h} = 480\text{ Ah}$. "You need a 480 Ah battery."[cite: 1]
* **Step 3 (Inspect Assumptions):** The AI assumed 100% discharge efficiency and 0% inverter/cable loss, and ignored the 50% Depth of Discharge limit[cite: 1].
* **Step 4 (Authoritative Source):** Battery manufacturer application guides state lead-acid batteries must not exceed 50% DoD to prevent permanent cell degradation[cite: 1].
* **Step 5 (Boundary/Sanity Check):** Discharging a 480 Ah battery by 480 Ah leaves 0 Ah capacity, which destroys the battery bank within a few cycles.
* **Step 6 (Triangulate):** Manual arithmetic: Total energy = $120\text{ W} \times 48\text{ h} = 5,760\text{ Wh}$. Usable capacity needed = $480\text{ Ah}$. At 50% DoD, nominal capacity = $480 / 0.5 = 960\text{ Ah}$. Factoring in 85% inverter efficiency: $960 / 0.85 \approx 1,130\text{ Ah}$.
* **Step 7 (Conclude):** **Revise.** Reject the AI's 480 Ah figure; specify an 1,150 Ah battery system based on verified physical limits and safety margins[cite: 1].

### E - Evidence
* NASA Systems Engineering Handbook (NASA/SP-2016-6105 Rev 2) verification and validation protocols[cite: 1].
* Safety engineering standards for independent peer review[cite: 1].

### V - Verification
Tested this protocol against multiple technical prompts to confirm that Step 3 (Assumption Inspection) and Step 5 (Boundary Checks) consistently expose silent model simplifications[cite: 1].

### R - Reflection
Engineering verification is not just checking if the math is correct; it is checking whether the model solved the *right problem under the right physical constraints*[cite: 1].
