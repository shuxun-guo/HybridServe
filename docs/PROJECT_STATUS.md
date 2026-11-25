# HybridServe — Project Status

**Last Updated:** 2026-11-26

## 1. Project Overview

HybridServe is an LLM inference and serving system project.

The project aims to independently implement selected core components of modern LLM inference systems, understand their underlying mechanisms, and subsequently integrate them with an established inference framework.

The goal is to build an engineering-oriented project demonstrating practical understanding of LLM inference optimization, GPU execution, memory management, and request scheduling.

## 2. Confirmed Technical Decisions

| Item                          | Decision                                                          |
| ----------------------------- | ----------------------------------------------------------------- |
| GPU                           | NVIDIA RTX 4090 24GB                                              |
| Primary Model                 | Qwen3.5-27B-GPTQ-Int4                                             |
| Primary Integration Framework | vLLM V1                                                           |
| Reference Framework           | SGLang                                                            |
| Implementation Approach       | C                                                                 |
| Development Strategy          | Independently implement core components, then integrate with vLLM |
| Initial Workload              | Text-only inference                                               |
| Initial Context Target        | 4K–8K                                                             |

**Important:** Model selection is confirmed, but model compatibility and hardware feasibility have not yet been validated.

## 3. Verified Completed Work

### 3.1 GPU Development Environment

The following environment was checked on BitaHub:

- GPU: NVIDIA GeForce RTX 4090 24GB
- NVIDIA Driver: 580.76.05
- PyTorch: 2.11.0+cu128
- PyTorch CUDA availability: True
- CUDA Toolkit: 12.8
- Triton: 3.6.0
- GCC/G++: 13.3.0
- CMake: 3.28.3
- Ninja: 1.11.1
- GNU Make: 4.3

Basic PyTorch GPU computation and Triton kernel compilation/execution were successfully tested.

### 3.2 Persistent Storage

NAS storage was mounted at:

`/hybridserve-storage`

The following directory was created:

`/hybridserve-storage/HybridServe`

A read/write test was successfully completed.

### 3.3 Project Structure

The local repository was initialized at:

`/hybridserve-storage/HybridServe/hybridserve-inference`

The initial directory structure, README.md, and .gitignore were created.

### 3.4 Git and GitHub

- Local Git repository initialized.
- Main branch created.
- Git author identity configured.
- Initial commit created:

`d06431e chore: initialize HybridServe project`

- Dedicated SSH authentication key generated for GitHub.
- GitHub SSH authentication verified.
- Remote repository configured:

`git@github.com:shuxun-guo/HybridServe.git`

- Initial push to GitHub succeeded.
- Local main branch tracks origin/main.

## 4. Current Development Phase

**Phase 0 — Model Compatibility, Environment Preparation and Baseline**

The project infrastructure is prepared. Core inference engine implementation has not started.

## 5. Outstanding Tasks

### 5.1 Model Compatibility Validation

- [ ] Identify the exact Qwen3.5-27B-GPTQ-Int4 model repository.
- [ ] Inspect model architecture and configuration.
- [ ] Verify GPTQ quantization format.
- [ ] Verify compatibility with the intended vLLM V1 release.
- [ ] Check whether additional model-specific dependencies are required.

### 5.2 GPU Memory Feasibility

- [ ] Estimate quantized model weight memory.
- [ ] Estimate KV Cache memory.
- [ ] Account for CUDA runtime and framework overhead.
- [ ] Account for CUDA Graph memory overhead.
- [ ] Evaluate feasibility of the 4K–8K context target.
- [ ] Determine practical concurrency limits.

### 5.3 Inference Environment

- [ ] Select a compatible vLLM version.
- [ ] Create an isolated inference environment.
- [ ] Install and validate vLLM.
- [ ] Download model weights.
- [ ] Launch the inference server.
- [ ] Complete a basic inference test.

### 5.4 Baseline Benchmark

- [ ] Establish a reproducible benchmark configuration.
- [ ] Measure Time To First Token (TTFT).
- [ ] Measure Time Per Output Token (TPOT).
- [ ] Measure request throughput.
- [ ] Measure token throughput.
- [ ] Record GPU memory consumption.
- [ ] Save benchmark configurations and results.

## 6. Next Immediate Task

Validate the exact model repository, architecture, GPTQ format, and compatibility with vLLM V1.

Do not download large model weights or install a new inference stack before completing this compatibility check.

After compatibility validation, proceed with GPU memory estimation and vLLM version selection.

## 7. Development Principles

1. Keep project documentation synchronized with actual implementation progress.
2. Distinguish completed, tested, planned, and unverified work.
3. Record important technical decisions and their rationale.
4. Establish reproducible benchmarks before attempting optimization.
5. Avoid modifying core architecture without understanding the trade-offs.
6. The project owner actively participates in core design, implementation, debugging, and performance analysis.
7. The assistant primarily provides technical guidance, code review, debugging assistance, and research support.

## 8. Update Policy

Update this document at the end of each meaningful development session.

Every update should reflect the actual state of the repository and development environment.

Never mark a task as completed without verification.
