# Sivaguru R.M.

**Systems & AI Engineer** &middot; Chennai, India  
`sivagurumurugan1@gmail.com` &middot; [github.com/Sivaguru-2008](https://github.com/Sivaguru-2008)

---

I build deterministic systems, execution engines, and safety infrastructure for autonomous agents and machine learning pipelines. My focus centers on distributed consistency, side-effect fencing, memory-efficient LLM inference, and verifiable offline compliance.

---

### Core Engineering Focus

- **Deterministic Agent Infrastructure:** Event-sourced execution, distributed lease fencing, and crash-consistent replay sandboxing for autonomous workflows.
- **LLM Systems & Inference Optimization:** KV-cache compression via joint token-channel bit allocation, packed sub-byte quantization, and speculative verification.
- **Compliance & Deterministic Parsing:** AST/grammar parsers for heterogeneous infrastructure configs (Cisco, Juniper, Fortinet, Arista, SONiC) with zero-hallucination compliance verification.
- **Safety & Calibrated Inference:** Finite-sample conformal prediction, streaming population statistics, and distinguishing measurement-limited uncertainty from model ambiguity.

---

### Selected Flagship Projects

#### [Agent Runtime](https://github.com/Sivaguru-2008/agent-runtime)
*Production-grade execution engine and safety layer for autonomous AI agents.*
- **Architecture:** Decouples cognition from execution dispatch using an append-only PostgreSQL event store, distributed lease coordination, and Redis Streams priority routing.
- **Side-Effect Fencing (`agent-fence`):** Enforces at-most-once semantics on irreversible external operations via canonical hash matching, schema projection, and causal risk escalation.
- **Deterministic Replay:** Allows arbitrary historical execution branches to be forked and stepped through in an isolated sandbox without repeating real-world side effects.
- **Engineering Standard:** 984+ automated unit, invariant, and integration tests across API and SDK workspaces.
- *Stack: TypeScript, Fastify, PostgreSQL, Redis Streams, Next.js 14, Docker, Vitest*

#### [UniKV](https://github.com/Sivaguru-2008/UniKV)
*Unified KV cache compression with joint token-channel allocation and speculative verification.*
- **Formulation:** Unifies token eviction and mixed-precision quantization under a single rate-distortion knapsack allocation with exact eviction identity derivations.
- **Implementation:** Custom packed int2 / int4 / int8 cache storage, packed SDPA attention kernels with per-head eviction masks, and streaming AIMD precision controllers.
- **Empirical Validation:** Benchmarked against 6 state-of-the-art baselines (StreamingLLM, SnapKV, Knorm, H2O, KIVI-4/2, RDKV) across multi-turn context and Needle-in-a-Haystack tasks.
- *Stack: Python, PyTorch, CUDA / Triton, Shell*

#### [CASCADE](https://github.com/Sivaguru-2008/cascade)
*Real-time clinical prescribing cascade surveillance on IBM LinuxONE (s390x).*
- **Dual-Loop Pipeline:** Loop 1 performs millisecond-latency dispensing stream interception (XGBoost + SHAP feature attribution); Loop 2 runs streaming Prescription Sequence Symmetry Analysis (PSSA) across population data with Clopper–Pearson confidence intervals and Benjamini–Hochberg FDR correction.
- **Enterprise Hardening:** Privacy-by-design tokenization (HMAC-SHA256 at ingest), AES-256-GCM encrypted persistence, and automated regulatory reporting for India's Pharmacovigilance Programme (PvPI).
- *Stack: Python, FastAPI, XGBoost, SHAP, SQLite / PostgreSQL, Docker, IBM LinuxONE (s390x)*

#### [ConfigIQ / Network Compliance](https://github.com/Sivaguru-2008/network-compliance)
*Deterministic multi-vendor network security compliance auditor (SIH 2026).*
- **Unified Normalization:** Custom deterministic grammar parsers normalize Cisco IOS/IOS-XE, Juniper Junos, Fortinet FortiOS, Arista EOS, and SONiC configurations into a single vendor-neutral `SecurityBaselineModel`.
- **Zero Hallucination:** Evaluates configs against CIS Benchmarks, NIST 800-53, and DISA STIG controls with every `PASS` / `FAIL` / `NEEDS_REVIEW` verdict backed by exact line-number traceability. Runs 100% offline.
- *Stack: Python, AST Parsing, Pytest, Docker, CIS Benchmark Suites*

#### [AURA](https://github.com/Sivaguru-2008/aura)
*Clinical intelligence copilot with quantum-classical evidence fusion and calibrated doubt.*
- **Finite-Shot Separation:** Distinguishes between *measurement-limited doubt* (resolvable with higher shot budgets) and *model-limited doubt* (irreducible ambiguity requiring human clinical escalation) using PennyLane variational circuits executed on IBM Quantum hardware (`ibm_marrakesh`).
- **Grounded Evaluation:** Incorporates Bayesian product-of-experts baselines, conformal prediction with abstention, and full offline privacy.
- *Stack: Python, PennyLane, Qiskit, Conformal Prediction, FastAPI*

#### [Emergency Dispatch System](https://github.com/Sivaguru-2008/emergency-dispatch-system)
*Logarithmic-time spatial resource allocation and emergency ambulance dispatch.*
- **Algorithmic Core:** Implemented 2D Orthogonal Range Trees augmented with Fractional Cascading, reducing 2D spatial queries from $O(\log^2 n + k)$ to optimal $O(\log n + k)$.
- **Point Location:** Slab-decomposition method answering zone-incident routing queries in $O(\log n)$ time. Pure Java implementation with zero external framework overhead.
- *Stack: Java (Core SE), Computational Geometry, Spatial Data Structures*

---

### Technical Competencies

- **Languages:** TypeScript, JavaScript (Node.js), Python, Java, C, SQL
- **Distributed Systems & Backend:** Event Sourcing, Transactional Outboxes, Distributed Locking / Leases, Idempotent APIs, PostgreSQL, Redis Streams, Docker
- **AI Systems & Safety:** Agent Runtime Fencing, KV-Cache Quantization & Eviction, Token Diagnostics, Conformal Safety, XGBoost, SHAP
- **Engineering Rigor:** Invariant Testing, Deterministic Replay, Chaos & Recovery Validation, Clean Architecture, CI/CD
