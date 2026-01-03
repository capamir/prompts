# 🔍 Stage 4: Code Audit, Refactoring & Documentation (v2026.1)

## 🎯 Primary Objective

To ensure long-term system health by auditing the implementation against core principles, managing technical debt, and generating 100% accurate, code-verified documentation. This document governs the Maintenance & Evolution phase of the engineering lifecycle [cite: master_template Step 8].

## 🚦 Rule of Engagement: "The Anti-Hallucination Protocol"

You are strictly forbidden from documenting assumptions, wish lists, or generic patterns that aren't actually implemented in the codebase. Every claim must be verifiable [cite: docs.md]:

Verification Required: Every statement must cite a specific file path and actual function/class name.

No Guessing: If logic is missing or proof is not found in the code, mark it as [NEEDS VERIFICATION] or omit it.

Actuals Only: Reference actual configuration keys, environment variables, and error messages found in the files.

## 🏗️ The Audit Strategy

1. The Simplicity & KISS Review

Logic Consolidation: Identify code duplication (DRY) and extract reusable logic into service layers or utility packages [cite: AGENTS Rule 7].

Dead Code Elimination: Identify and delete unused variables, imports, or legacy paths [cite: AGENTS Rule 53].

Proportionality Check: Verify if the implementation is still proportional to the problem scale or if over-engineering has occurred [cite: AGENTS Rule 11].

2. Technical Debt Register

Document and categorize all incurred technical debt explicitly [cite: AGENTS Rule 51]:

Identification: Flag "hacks," temporary workarounds, or skipped test cases.

Categorization: Technical, Operational, Security, or Architectural.

Prioritization: Assign severity based on the risk of future maintenance friction.

3. Architecture & Boundary Audit

Separation of Concerns: Ensure no leaks exist between layers (e.g., database logic in views or frontend state in the backend) [cite: AGENTS Rule 10].

ADR Synchronization: Verify that the final implementation matches the approved Architecture Decision Records.

## 📝 The Documentation Output (Ownership)

Generate the final PROJECT_DOCUMENTATION.md following this structure:

Current System Overview: Factual summary of what the system actually does right now.

Architecture (The Reality): Component relationships and data flow based on actual imports/exports.

Feature Walkthrough: Step-by-step flow citing actual function names and types [cite: master_workflow 5].

Technical Invariants: List the actual invariants the code enforces (e.g., "Row level locking on X").

Failure & Recovery: Document how the system handles crashes based on the current implementation.

## 🧱 Language-Specific Audit Nuances

Go: Ensure all errors are handled and not ignored (_). Verify interface usage follows "Accept interfaces, return structs."

Django/FastAPI: Audit for missing type hints or Any types. Verify ORM efficiency and async-safety.

Next.js/React: Break down "God Components" into atomic units. Remove unused styles and Tailwind fragments.

### ✅ The Final Maintenance Gate (Rule 66)

A task is only "Completed & Owned" when:

$$$$

 Documentation is a 100% faithful, code-verified mirror of the system.

$$$$

 Technical debt is logged in the register with a remediation plan.

$$$$

 No debug fragments (print, console.log, TODO) remain.

$$$$

 The code passes the "Ownership Test": it can be modified confidently by future-you.

"The goal is long-term understanding and ownership, not just explanation."