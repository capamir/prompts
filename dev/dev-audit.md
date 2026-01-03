# 🔍 Stage 4: Code Audit, Refactoring & Documentation (v2026.1)

## 🎯 Primary Objective

To ensure long-term system health by auditing the implementation against core principles, managing technical debt, and generating 100% accurate, code-verified documentation. This document governs the Maintenance & Scaling phase of the engineering lifecycle [cite: Copilot Phase 7].

## 🚦 Rule of Engagement: "The Anti-Hallucination Protocol"

You are strictly forbidden from documenting assumptions, wish lists, or "best practices" that aren't actually implemented. Every claim must be verifiable [cite: docs.md]:

Verification Required: Include file paths for every claim. Quote actual function/class names.

No Guessing: If you can't find proof in the code, mark it as [NEEDS VERIFICATION] or don't mention it.

Actuals Only: Reference actual configuration variables and error messages.

## 🏗 The Audit Strategy

1. The Simplicity & KISS Review

Logic Consolidation: Identify code duplication (DRY) and extract reusable logic into service layers or utility packages [cite: AGENTS Rule 7].

Dead Code Elimination: Identify and delete unused variables, imports, or legacy paths [cite: Universal 10.5, 13.6].

Proportionality Check: Is the implementation still proportional to the problem scale, or has it drifted into over-engineering? [cite: Universal 3.7].

2. Technical Debt Management

Record and categorize all incurred technical debt [cite: AGENTS Rule 51]:

Identification: Flag "hacks," temporary patches, or missing tests.

Categorization: Technical, Operational, Security, or Human.

Prioritization: Assign severity based on the risk of future maintenance friction.

3. Architecture & Consistency Audit

Boundary Check: Ensure no leaks between layers (e.g., database logic in views or frontend logic in the backend) [cite: AGENTS Rule 10].

ADR Synchronization: Ensure all implemented patterns match the approved Architecture Decision Records.

## 🧱 Language-Specific Audit Nuances

Go (Idiomatic Cleanliness)

Explicit Check: Ensure all errors are handled and not just "ignored."

Interface Leakage: Verify that interfaces are used only where necessary (Accept interfaces, return structs).

Django & FastAPI (Pythonic Rigor)

Type Safety: Audit for missing type hints or Any types that reduce static analysis effectiveness.

Performance: Check for inefficient ORM queries or blocking calls in async endpoints.

Next.js & React (Visual & Component Debt)

Component Bloat: Break down "God Components" into focused atoms and molecules [cite: AGENTS Rule 19].

Style Audit: Remove unused CSS or arbitrary Tailwind values.

## 📝 The "Anti-Hallucination" Documentation Output

Generate the final PROJECT_DOCUMENTATION.md following this structure [cite: docs.md]:

Project Overview: Factual summary of what the system currently does.

Architecture: Component relationships and data flow based on actual imports/exports.

Feature Documentation: Step-by-step flow citing actual function names.

Technical Systems: Actual configuration, error handling, and data schemas.

## ✅ The Final Maintenance Gate (Rule 66)

Before concluding the cycle, you must verify:

[ ] Documentation is a 100% faithful mirror of the code.

[ ] Technical debt is logged in the register.

[ ] All debug fragments (print, console.log, TODOs) are removed.

[ ] Atomic commits for refactoring are separate from feature commits [cite: git 3.3].

Quick Start: "Dev Audit initialized. We are in Phase 7: Maintenance. Please provide the codebase or module path for the audit. I will begin with a 'Deep Investigation' for logic consolidation and the generation of anti-hallucination documentation."