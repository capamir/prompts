# 🧠 Unified AI Agent Operating System (v2026)

This repository contains a modular, high-fidelity framework of "Masterpiece" prompts designed to transform AI from a simple code generator into a Senior Tech Lead, Socratic Mentor, and Strategic Research Fellow.

## 🎯 Core Philosophy

Correctness > Convenience: Backend invariants and system integrity are non-negotiable.

Invariants First: Define what must always be true before writing logic.

Thinking > Typing: Decompose problems into atomic tasks before implementation.

Ownership: Documentation is code-verified to ensure long-term understanding.

## 🛠️ The 4-Stage Engineering Lifecycle

Every project in this repository follows a disciplined progression to ensure high-status engineering outcomes.

Stage 1: Architecture & Triage (dev_architect.md)

Perform Risk Triage (Tier A/B/C) to determine depth. Define system Invariants and document choices using ADRs (Architecture Decision Records).

Stage 2: Implementation (Language-Specific Workflows)

Use specialized engines to convert designs into code following the "Investigate First" protocol.

Go: Explicit errors, no magic, concurrent safety.

Django: Service layers, MTV isolation, REST integrity.

FastAPI: Async-first, strict Pydantic validation.

Next.js/React: Figma-to-code, Framer Motion/GSAP animations.

Agent Header: agent_meta_context.md — The mandatory posture for local coding agents.

Stage 3: Reliability & QA (dev_testing.md)

The "Skeptical Auditor" phase. Generate test suites that seek to break the code, proving invariants and handling failure modes (Race conditions, crashes).

Stage 4: Audit & Ownership (dev_audit.md)

The "Future Me" phase. Perform an Anti-Hallucination Audit to generate 100% code-verified documentation and log technical debt.

## 🛰️ Specialized Domains

Research Fellow: WSN (research_wsn_fellow.md)

Designed for Master’s level academic research. Translates academic papers into Python (SimPy/NetworkX) simulations with a focus on Energy Models, Fuzzy Logic, and Algorithmic Optimization.

Social Strategist (social_strategist.md)

A psychological engine for high-stakes professional and personal communication. Analyzes Power Dynamics, Frame Control, and Subtext to engineer high-status responses.

Translation Bridge (translation_structuring_instruction.md)

The bridge between Persian conceptual thought and professional English engineering artifacts.

## 📁 Repository Structure

.
├── core/
│   ├── AGENTS.md               # The permanent rule context
│   ├── collaboration.md        # The Human-AI contract
│   └── universal_workflow.md   # The project-agnostic engine
├── stage-1-architecture/
│   ├── dev_mentor.md           # The Socratic Lead entry point
│   └── dev_architect.md        # Triage and Invariants
├── stage-2-implementation/
│   ├── go_workflow.md
│   ├── django_workflow.md
│   ├── fastapi_workflow.md
│   ├── react_next_workflow.md
│   └── agent_meta_header.md    # Header for local agents
├── stage-3-validation/
│   ├── dev_testing.md          # QA & Skepticism
│   └── senior_review.md        # Adversarial Correctness
├── stage-4-maintenance/
│   └── dev_audit.md            # Ownership & Anti-Hallucination
└── specialized/
    ├── research_wsn.md         # Master's Research engine
    ├── social_strategist.md    # Psychology & Dynamics
    └── translation.md          # Persian-to-English Bridge


## 🚀 How to Use

Initialize: Load dev_mentor.md and AGENTS.md at the start of a session.

Triage: Use dev_architect.md to define the Tier and Invariants.

Execute: Select the appropriate Stage 2 Workflow for your stack.

Audit: Always close a task with dev_audit.md to ensure code ownership.

"Understanding precedes speed. Correctness is proven, not assumed."