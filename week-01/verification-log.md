# Week 01 Verification Log

| Date | Question / Claim | AI Tool | Claim Checked | Verification Source / Experiment | Result |
|---|---|---|---|---|---|
| 2026-09-29 | Q1: Agents vs GenAI | ChatGPT | Claimed agents are defined as fine-tuned generative models with larger parameter sizes. | Lil'Log (Weng, 2023) "LLM Powered Autonomous Agents"; LangChain architecture specs. | **Incorrect by AI:** Agents are system-level workflow architectures (tools + memory + control loop), not just larger models. |
| 2026-09-30 | Q4: Maritime Sailing Record | Gemini | Claimed *SS United States* holds the commercial sailing record. | Lloyd's Register & Maritime Museum archives. | **Failed Constraint by AI:** The *SS United States* was a steam turbine vessel, completely violating the "sailing ship" requirement. |
| 2026-10-01 | Q5: Nyquist Criterion | Claude | Claimed $f_s > 2B$ is sufficient for ideal reconstruction without aliasing. | Shannon (1949) original paper; Oppenheim DSP textbook. | **Verified Correct:** Faithfully reflects the non-overlapping spectra requirement in Fourier domain analysis. |
| 2026-10-01 | Q8: Microwave Intelligence | Gemini | Stated sensor microwave buttons use tiny embedded machine learning classifiers. | Manufacturer teardown guides and service repair schematics. | **Unsupported / Inaccurate by AI:** Standard microwaves use basic analog humidity/gas sensors wired to comparator circuits; no ML is present. |
| 2026-10-02 | Q10: Battery Sizing | ChatGPT | Stated a 480 Ah 12V battery suffices for a 120W, 48-hour continuous load. | Battery Council International (BCI) lead-acid application guides. | **Incomplete / Flawed by AI:** Completely neglected Depth-of-Discharge (DoD) limits and inverter conversion losses. |

## Notes
* **What did the AI get right?** Conceptual definitions, smooth summaries, and introductory explanations were consistently clear and grammatically fluent.
* **What did it get wrong or leave unsupported?** Edge constraints, domain-specific operating rules (e.g., Depth-of-Discharge), and distinguishing real ML from standard sensor hardware.
* **What did I learn about verification?** Never assume fluency means correctness. Checking simple constraints and inspecting silent assumptions is where verification pays off.
