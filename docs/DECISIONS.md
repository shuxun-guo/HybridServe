# HybridServe — Technical Decision Records

This document records the major technical decisions made during the development of HybridServe.

Its purpose is to preserve design rationale, avoid repeatedly revisiting settled decisions, and provide a reliable reference for future development.

Decision status:
- **Confirmed:** Explicitly selected and agreed upon.
- **Pending Validation:** Selected, but technical feasibility has not yet been verified.
- **Open:** No final decision has been made.

---

## DEC-001: Project Objective

**Status:** Confirmed

**Decision:**

Build an engineering-oriented LLM inference and serving system.

The project should demonstrate substantial practical engineering capabilities in:

- LLM inference optimization
- GPU execution and kernel optimization
- KV Cache management
- Request scheduling
- Continuous Batching
- Inference framework integration
- Performance profiling and benchmarking

**Rationale:**

The primary objective is to build a technically substantial project that can demonstrate practical competence to AI Infrastructure and LLM systems engineering interviewers.

The project does not need to introduce a novel research algorithm. Engineering depth, implementation quality, reproducibility, and the ability to explain design trade-offs are more important than claiming innovation for its own sake.

---

## DEC-002: Hardware Platform

**Status:** Confirmed

**Decision:**

- GPU: NVIDIA GeForce RTX 4090
- VRAM: 24GB
- Development platform: BitaHub GPU rental
- NAS storage: BitaHub shared storage

**Resource Constraints:**

- Approximate total project budget: RMB 2,000.
- Preferred RTX 4090 rental price: RMB 1–2/hour.

**Rationale:**

RTX 4090 provides a practical single-GPU development environment for CUDA, Triton, and LLM inference experiments.

The project should minimize unnecessary GPU rental time.

---

## DEC-003: Primary Test Model

**Status:** Pending Validation

**Decision:**

Primary planned model:

`Qwen3.5-27B-GPTQ-Int4`

**Rationale:**

Use a relatively substantial model rather than a small demonstration model, so that the project can investigate realistic memory management, scheduling, and inference performance challenges.

**Unresolved Issues:**

- Exact model repository and revision.
- Actual architecture configuration.
- GPTQ quantization format and implementation.
- Compatibility with the selected vLLM version.
- RTX 4090 24GB memory feasibility.
- Practical context length and concurrency.

The model selection is confirmed, but deployment feasibility is not yet established.

---

## DEC-004: Primary Inference Framework

**Status:** Confirmed

**Decision:**

Use `vLLM V1` as the primary inference framework for integration.

Use `SGLang` as a secondary reference for architectural study and implementation comparisons.

**Rationale:**

The project should have a clear integration target rather than attempting to independently reproduce every component of a production inference framework.

vLLM V1 will serve as the primary integration framework, while SGLang provides an additional reference for understanding modern serving architectures.

**Unresolved Issues:**

- Exact compatible vLLM release.
- Model-specific backend support.
- Integration interfaces and implementation details.

---

## DEC-005: Implementation Approach

**Status:** Confirmed

**Decision:**

Use implementation approach C, as explicitly selected by the project owner.

Independently implement selected core inference components, then integrate them with the established inference framework.

**Development Principle:**

The project should involve genuine implementation and engineering work rather than merely wrapping an existing inference engine with an API layer.

The exact module boundaries and integration strategy should be documented as implementation progresses.

---

## DEC-006: Initial Workload

**Status:** Confirmed

**Decision:**

Start with text-only LLM inference.

Initial context-length target:

- 4K tokens.
- 8K tokens.

These are initial evaluation targets, not yet verified hardware capabilities.

**Rationale:**

Keep the initial workload focused so that performance measurements and subsequent optimizations can be compared under reproducible conditions.

---

## DEC-007: Development Collaboration

**Status:** Confirmed

**Decision:**

The project owner should actively participate in core engineering work.

The assistant primarily acts as a technical mentor and development partner.

**Responsibilities:**

Project owner:
- Participate in architectural decisions.
- Implement core components.
- Debug and optimize code.
- Design and conduct experiments.
- Analyze performance results.

Assistant:
- Explain technical concepts.
- Help break down complex tasks.
- Provide research and documentation guidance.
- Review code and identify problems.
- Assist with debugging and performance analysis.

The assistant should not take over important implementation work unless explicitly requested.

---

## DEC-008: Benchmarking Strategy

**Status:** Confirmed

**Decision:**

Establish a reproducible baseline before evaluating custom optimizations.

Primary metrics:

- TTFT (Time To First Token)
- TPOT (Time Per Output Token)
- Request throughput
- Output token throughput
- GPU memory consumption

**Rationale:**

Performance improvements must be supported by measurable experimental results.

Comparisons should use consistent hardware, model, workload, and benchmark configurations.

---

## Decision Change Policy

1. Do not silently change confirmed decisions.
2. Revisit a decision only when new technical evidence justifies doing so.
3. Record the reason for every significant change.
4. Distinguish confirmed decisions from assumptions and unverified plans.
5. Update this document whenever a major technical decision changes.
