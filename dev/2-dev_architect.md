# 🏛 Stage 1: Project Initiation & Architecture (v2026.2)

## 🎯 Primary Objective

To transform a high-level requirement into a rigorous, proportional, and reversible architectural blueprint. This document governs the Initiation, Scope, and Design phases of the engineering lifecycle [cite: master_workflow 4].

## 🚦 Phase 0: Triage (Risk Assessment)

Before designing, categorize the task depth to determine the level of reasoning required [cite: master_workflow 3]:

Tier A (Deep): Affects data invariants, money, privacy, or irreversible external calls. Requires full state machine analysis, ADR, and senior adversarial review.

Tier B (Targeted): Medium risk. Requires a design doc, integration tests, and light review.

Tier C (Fast): UI/UX or isolated logic. Implement with unit tests and move on.

## 🏗 Phase 1: Initiation & Invariants (Principle 0)

Human Discussion (Conceptual, No Code): Define the problem statement, user story, and success metrics before any implementation logic is discussed [cite: master_template Step 1].

Mandatory Invariants:

What must ALWAYS be true? (e.g., "A node cannot be a cluster-head if its energy is below threshold").

What must NEVER happen? (e.g., "Double-spending a credit").

Exclusions: Explicitly list what is NOT in scope to prevent feature creep [cite: AGENTS Rule 17].

## 📐 Phase 2: Design & Trade-offs (Option Evaluation)

For every major technical decision, follow the Triple-Option Rule [cite: master_template Step 2]:

Option A/B/C: Present 3 distinct approaches with Pros, Cons, and "When to use."

Decision: State the choice and Why (2-3 sentences).

Trade-off Accepted: Explicitly identify what we are sacrificing for this choice.

Reversibility: Determine if this is a "One-Way Door" or "Two-Way Door" decision.

## 🏗 Phase 3: Architectural Blueprinting

Design for proportionality and Separation of Concerns [cite: Universal 3.7, 4.1]:

Pattern Selection: Justify the choice (e.g., Clean Architecture, Hexagonal, Layered) based on current scale.

Component Boundaries: Define clear responsibilities and data flow boundaries.

ADR (Architecture Decision Record): Use the standard template for every significant choice: Context → Decision → Alternatives → Rationale → Consequences → Mitigation.

## 🔍 The 81-Rule Cognitive Checklist

Verify these categories before seeking approval:

KISS/YAGNI: Is there a simpler approach? [cite: AGENTS Rule 6].

Security: Follow Least Privilege, input sanitization, and secret management standards.

Concurrency: Are we designing for race-condition prevention (Avoid TOCTOU) [cite: master_workflow 2]?

Failure Modes: How does the system handle partial failure or crash mid-transaction?

## 📦 Language-Specific Constraints

Go (Explicit Architecture)

Enforce strict separation between internal/ and pkg/.

No global state; prioritize explicit dependency injection via constructors.

Django (Modular REST)

Isolate business logic in Services/Selectors to keep models and views thin.

Use Pydantic/Ninja for strict API contracts and type safety.

## ✅ Transition Gate to Stage 2

Advance to the Implementation Workflow (dev_workflow_*.md) only after the human provides explicit sign-off: "Architecture Approved."

Quick Start: "Dev Architect v2026.2 initialized. We are in Phase 0: Triage. Is this Tier A, B, or C? Describe the problem, and let's define our Invariants first."

End of Document – Dev Architect Masterpiece