# Sivaguru R.M.

**Systems & AI Research Engineer** &middot; Chennai, India  
`sivagurumurugan1@gmail.com` &middot; [github.com/Sivaguru-2008](https://github.com/Sivaguru-2008)

---

I research and engineer deterministic execution engines, side-effect safety layers for autonomous agents, memory-efficient LLM inference architectures, and verifiable offline compliance pipelines. My work prioritizes distributed consistency, rigorous algorithmic foundations, empirical reproducibility, and intellectual honesty.

---

### Core Technical Focus

- **Deterministic Agent Systems:** Append-only event-sourced execution, lease-based crash recovery, and side-effect fencing (`agent-fence`) that prevents duplicate external actions during non-deterministic LLM retries.
- **LLM Inference Systems & Caching:** Rate-distortion KV cache compression, joint token-channel allocation, packed sub-byte quantization (INT2/INT4/INT8), and speculative verification.
- **Deterministic Parsing & Compliance:** Air-gapped, offline AST/grammar parsers for heterogeneous infrastructure configs (Cisco, Juniper, Fortinet, Arista, SONiC) with line-level evidence traceability.
- **Algorithmic Foundations & Computational Geometry:** Logarithmic-time spatial data structures (Orthogonal Range Trees with Fractional Cascading, Slab-Decomposition Point Location) implemented in low-level languages without external framework bloat.
- **Calibrated AI & Statistical Safety:** Finite-sample conformal prediction, streaming population statistics (PSSA with Clopper–Pearson intervals & BH FDR correction), and separating finite-shot measurement doubt from model ambiguity.

---

### Flagship Projects

#### [1. Agent Runtime](https://github.com/Sivaguru-2008/agent-runtime)
*Deterministic execution engine and side-effect safety runtime for autonomous AI agents.*
- **V1 Core Architecture:** Decouples cognition from execution dispatch via an append-only PostgreSQL 16 event store (`events`, `executions`, `execution_leases`, `tool_call_dedup`, `replay_branches`). Operates as a robust single-process Fastify runtime streaming live execution DAGs and timelines via PostgreSQL `LISTEN`/`NOTIFY`.
- **Side-Effect Fencing (`agent-fence`):** Enforces at-most-once semantics on irreversible tools (Stripe refunds, database writes, external APIs) using canonical parameter hashing, schema projection, and LLM semantic validation to catch non-deterministic retry paraphrases.
- **Deterministic Replay Sandbox:** Forks historical execution timelines from arbitrary checkpoints into isolated sandbox branches to reproduce failures and step-debug prompt improvements.
- **Verification Standard:** 984+ automated unit, invariant, and reliability tests passing across API and SDK workspaces.
- *Stack: TypeScript 5.6, Fastify 4.28, PostgreSQL 16, Next.js 15, Vitest, Docker*

#### [2. UniKV](https://github.com/Sivaguru-2008/UniKV)
*Unified KV cache compression with joint token-channel allocation and speculative verification.*
- **Mathematical Grounding:** Unifies token eviction and mixed-precision quantization into a rate-distortion knapsack allocation under fixed GPU memory constraints. Derived the exact attention eviction identity $\mathbf{o}_S - \mathbf{o} = m_E(\mathbf{o}_S - \mathbf{o}_E)$ (empirically bounded to $\le 3.7 \times 10^{-8}$ max numerical error in float32).
- **Custom Cache & Kernels:** Implemented packed 2-bit, 4-bit, and 8-bit integer cache memory layouts and packed SDPA attention with per-head active eviction masks.
- **Empirical Findings:** Validated on LLaMA and Qwen models on NVIDIA RTX Blackwell architecture. Discovered that the uncompressed baseline exhibits a $1.2\%$ verification noise floor caused by bf16 logit ties, and documented that query-agnostic eviction suffers a $+0.950 \pm 0.035$ retrieval collapse on needle-in-a-haystack tasks when questions follow context.
- *Stack: Python 3.12, PyTorch, Custom Sub-Byte Quantizer, Bash Benchmark Suites*

#### [3. ConfigIQ (Network Compliance)](https://github.com/Sivaguru-2008/network-compliance)
*Deterministic multi-vendor network security compliance auditor (SIH 2026).*
- **Unified Baseline Normalization:** Deterministic AST and grammar parsers normalize Cisco IOS/IOS-XE, Juniper Junos, Fortinet FortiOS, Arista EOS, and SONiC configurations into a single vendor-neutral `SecurityBaselineModel`.
- **Zero-Cloud Air-Gapped Verification:** Evaluates device baselines against CIS Benchmarks, NIST 800-53, and DISA STIG controls. Enforces socket-level isolation to guarantee zero data egress; every verdict (`PASS`/`FAIL`/`NEEDS_REVIEW`) links directly to the exact configuration line number.
- **Isolated LLM Fallback:** Unsupported third-party vendor configurations never receive fabricated passes; optional opt-in LLM fallback (`--allow-llm`) cleanly tags unverified configurations as `NEEDS_REVIEW`.
- *Stack: Python 3.12, AST Parsers, Pytest, Docker, SQLite Rule Base*

#### [4. CASCADE](https://github.com/Sivaguru-2008/cascade)
*Real-time clinical prescribing cascade surveillance on IBM LinuxONE (s390x) | IBM Z Datathon 2026.*
- **Dual-Loop Streaming Pipeline:** Loop 1 performs millisecond-latency dispensing stream interception combining an XGBoost classifier with SHAP feature attribution; Loop 2 executes streaming Prescription Sequence Symmetry Analysis (PSSA) across population dispensing events to discover unknown drug cascade pairs.
- **Statistical Rigor:** Controls for background prescribing trends via null-ratio adjustments, calculates exact Clopper–Pearson binomial confidence intervals, and applies Benjamini–Hochberg False Discovery Rate (FDR) corrections.
- **Privacy & Security:** Edge-layer tokenization (HMAC-SHA256 at ingest), AES-256-GCM encrypted persistence at rest, role-based access control, and automated report generation for the Pharmacovigilance Programme of India (PvPI).
- *Stack: Python, FastAPI, XGBoost, SHAP, SQLite / PostgreSQL, Docker, IBM LinuxONE (s390x)*

#### [5. AURA](https://github.com/Sivaguru-2008/aura)
*Clinical intelligence copilot with quantum-classical evidence fusion and calibrated doubt.*
- **Finite-Shot Doubt Separation:** Distinguishes between *measurement-limited doubt* (resolvable by buying higher shot counts: $\text{Var}[\langle Z \rangle] = (1 - \langle Z \rangle^2)/n_{\text{shots}}$) and *model-limited doubt* (irreducible ambiguity requiring human clinical escalation) using PennyLane variational quantum circuits executed on real IBM Quantum hardware (`ibm_marrakesh`).
- **Intellectual Honesty:** Evaluates against classical Bayesian product-of-experts baselines with conformal prediction; transparently documents that while VQCs do not exceed well-calibrated classical models on raw diagnostic accuracy, they provide valuable finite-shot measurement separation on offline clinical edge devices.
- *Stack: Python, PennyLane, Qiskit, Conformal Prediction, FastAPI*

#### [6. Emergency Dispatch System](https://github.com/Sivaguru-2008/emergency-dispatch-system)
*Logarithmic-time spatial resource allocation and ambulance routing in Java.*
- **Algorithmic Purity:** Implemented 2D Orthogonal Range Trees augmented with Fractional Cascading from first principles without external third-party dependencies, reducing 2D spatial window search from $O(\log^2 n + k)$ to optimal $O(\log n + k)$.
- **Point Location:** Slab-decomposition method answering zone routing queries in $O(\log n)$ time.
- **Empirical Performance:** Verified against brute-force linear search over 11,000 randomized spatial queries; empirical benchmarks show a **93.1x speedup** over linear scan at $N = 10,000$ points and 62 ms build time for $N = 50,000$ points.
- *Stack: Java (Core SE 17), Computational Geometry, Spatial Data Structures*

---

### Technical Competencies

- **Languages:** TypeScript, JavaScript (Node.js), Python, Java (SE 17), C, SQL
- **Systems & Architecture:** Event Sourcing, Transactional Outboxes, Crash Recovery & Replay, Idempotency Protocols, Fastify, PostgreSQL 16, Docker
- **AI & Systems Research:** Rate-Distortion KV Cache Allocation, Sub-Byte Quantization, Agent Fencing, Conformal Prediction, XGBoost, SHAP
- **Engineering Hygiene:** Invariant & Property-Based Testing, Deterministic Offline Execution, Conventional Commits, CI/CD
