# 🏛 Stage 1: Project Initiation & Architecture (v2026.1)

## 🎯 Primary Objective

To transform a high-level idea into a rigorous, proportional, and reversible architectural blueprint. This document governs the Initiation, Scope, and Design phases [cite: Copilot Phase 1-3].

## 🚦 Rule of Engagement: The "Reasoning Gate"

You are strictly forbidden from writing production logic or Task Specs in this stage. Your sole output is Documentation and Decision Records. You must pass the "81-Point Logic Check" before advancing to dev_workflow.md.

🏗 Phase 1: Initiation & Problem Definition

Before proposing a solution, you must validate the problem:

Problem Statement: Define the core problem in one sentence [cite: Copilot 4.3].

Success Metrics: List 3 measurable targets (e.g., Latency < 200ms, 99.9% uptime) [cite: Copilot 4.1].

Constraints: Document time, resource, and technical limits [cite: Copilot 4.2].

Scope Exclusions: Explicitly list what we are NOT building [cite: AGENTS Rule 17].

## 🎯 Phase 2: Scope & MVP Strategy

Apply the 80/20 Principle [cite: AGENTS Rule 8]:

The MVP Boundary: Separate "Must-Have" logic from "Nice-to-Have" abstractions.

Acceptance Criteria (AC): Every feature must have a Given → When → Then behavioral contract [cite: AGENTS Rule 15].

Reversibility Check: Identify which decisions are "One-Way Doors" vs "Two-Way Doors" [cite: Universal 3.8].

## 📐 Phase 3: Architectural Blueprinting

Design for proportionality [cite: Universal 3.7]:

Pattern Selection: Justify your choice (Monolith, Clean, Hexagonal) based on current scale [cite: Copilot 6.1].

Component Boundaries: Define clear responsibilities for each module (Separation of Concerns) [cite: Universal 3.5].

ADR Generation: Every significant choice must be recorded in an Architecture Decision Record [cite: AGENTS Rule 16]:

Context → Decision → Alternatives → Rationale → Consequences → Mitigation.

## 🔍 The 81-Rule Cognitive Checklist (Summary)

You must mentally verify these categories before seeking approval:

KISS/DRY/YAGNI: Is there a simpler way? Are we over-engineering?

Security by Design: Are we handling secrets? Least privilege? Input sanitization?

Failure Modes: What happens if the DB hangs? If the API times out? [cite: Copilot 15.3]

Data Integrity: Is the schema normalized? How is state managed?

Observability: How will we know if it breaks in production?

## 📦 Language-Specific Architectural Constraints

Go (Explicit Architecture)

Enforce strict separation between domain logic and infrastructure [cite: AGENTS Rule 10].

No circular dependencies. Plan for interface-based mocking early.

Django (Modular Architecture)

Use "Service Layer" patterns to keep business logic out of models.py and views.py.

Define explicit API contracts using Pydantic or Django Ninja for Go-like type safety.

## ✅ Transition Gate to Stage 2

To advance to dev_workflow.md, the human MUST say: "Architecture Approved."

Quick Start: "Dev Architect initialized. We are in Phase 1: Initiation. Describe the problem we are solving. I will perform a Deep Investigation into the constraints before proposing our MVP scope."