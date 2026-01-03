# 🐹 Stage 2: Go Implementation Workflow (v2026.2)

## 🎯 Primary Objective

To implement approved architectural designs into high-performance, maintainable, and idiomatic Go applications. This document governs the Implementation and Validation phases for backend development [cite: master_workflow 4].

## 🚦 Rule of Engagement: The "Go Investigation"

Before generating any code, you MUST perform a Deep Investigation of:

Project Structure: Identify if the project follows /internal vs /pkg conventions or a flat structure.

Authoritative State: Review existing Structs and Interface contracts to ensure invariants are preserved [cite: master_workflow 2].

go.mod & Dependencies: Check toolchain versions and core libraries to avoid duplicate dependencies or version conflicts.

## 🏗️ Go-Specific Implementation Standards

1. Invariants & Correctness (The Go Proverbs)

Explicit Error Handling: Never ignore errors. Handle them immediately at the call site. Wrap errors with context: fmt.Errorf("context: %w", err) [cite: AGENTS Rule 22].

Writes Decide, Reads Inform: Avoid "check-then-act" patterns (TOCTOU races). Use atomic operations or appropriate locking mechanisms where state is shared [cite: master_workflow 2].

No Magic: Avoid init() functions and global state. Use explicit dependency injection via constructors [cite: AGENTS Rule 13].

2. Concurrency & Performance

Goroutines: Use concurrency only for truly independent, non-blocking tasks.

Channels vs. Mutex: Use channels for orchestration and mutexes for state protection. "Don't communicate by sharing memory; share memory by communicating."

Resource Management: Always use defer for closing files, DB connections, or releasing locks to ensure cleanup [cite: Universal 6.5].

3. Structural Design & Composition

Internal Privacy: Keep private logic in internal/ to prevent external package leakage [cite: AGENTS Rule 10].

Composition Over Embedding: Favor explicit composition; use struct embedding only when strictly necessary to avoid fragile hierarchies [cite: AGENTS Rule 20].

Standard Library First: Exhaust std library capabilities before adding external dependencies [cite: AGENTS Rule 23].

## 🧱 Atomic Task Specification (Go)

For every approved task from Stage 1, generate a spec including:

Given: Initial state, package context, and required imports.

When: The specific Function/Method action and signature.

Then: Expected outcome, return values, and error scenarios.

Acceptance Criteria: Behavioral Given/When/Then contracts [cite: AGENTS Rule 15].

## 🧪 Implementation Discipline

Atomic Commits: feat(<pkg>): <summary> – one logical change per commit [cite: git 3.3].

No Hallucinated Docs: Cite actual file paths and function names in all comments/logs [cite: docs.md].

Struggle Briefly: Use AI for boilerplate; keep ownership of business logic and synchronization rules [cite: master_template Step 6].

### ✅ Completion Checklist (Rule 66)

[ ] go fmt and go vet pass without warnings.

[ ] All errors are handled explicitly with context.

[ ] Race detection (-race) reports zero issues for concurrent code.

[ ] No panic() calls in production-grade code; use error returns.

Quick Start: "Go Workflow v2026.2 initialized. Architecture is approved. Please provide the Task ID or ADR. I will investigate the package boundaries and current interfaces before proposing Task 2.1."