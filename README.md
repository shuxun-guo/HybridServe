# HybridServe

A high-performance LLM inference and serving system.

## Project Overview

HybridServe aims to explore and implement core components
of modern LLM inference systems, followed by integration
with production-grade inference frameworks.

## Technical Strategy

- Independently implement core inference components.
- Use vLLM V1 as the primary integration framework.
- Refer to SGLang for architectural and implementation insights.
- Develop and evaluate GPU kernels using Triton and CUDA.

## Initial Development Scope

- Hardware: NVIDIA RTX 4090 24GB
- Initial workload: Text-only inference
- Target context length: 4K-8K
- Planned primary model: Qwen3.5-27B-GPTQ-Int4
- Model compatibility and memory feasibility will be validated.

## Core Components

1. Request and Batch Manager
2. Token Budget Scheduler
3. Paged KV Cache
4. Hybrid State Manager
5. Reference and GPU Kernels
6. Performance Metrics
7. vLLM Integration

## Development Roadmap

- Phase 0: Environment Setup and Baseline
- Phase 1: Paged KV Cache
- Phase 2: Continuous Batching and Scheduler
- Phase 3: GPU Kernel Optimization
- Phase 4: vLLM Integration
- Phase 5: End-to-End Benchmarking

## Repository Structure

- configs/: Configuration files
- docs/: Architecture and experiment documentation
- src/: Core implementation
- tests/: Unit and integration tests
- benchmarks/: Performance benchmarks
- scripts/: Utility scripts
- models/: Model storage
- logs/: Experiment logs

## Status

Environment setup completed.
Core implementation has not started.
